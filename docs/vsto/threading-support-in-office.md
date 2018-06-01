---
title: Suporte a Threading no Office
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- multiple threads [Office development in Visual Studio]
- threading [Office development in Visual Studio]
- Office applications [Office development in Visual Studio], threading support
- object models [Office development in Visual Studio], threading support
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 966f012b2ff4860205186410951b759c2e214668
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/01/2018
ms.locfileid: "34693078"
---
# <a name="threading-support-in-office"></a>Suporte a Threading no Office
  Este artigo fornece informações sobre como threading é suportado no modelo de objeto do Microsoft Office. O modelo de objeto do Office não é thread-safe, mas é possível trabalhar com vários segmentos em uma solução do Office. Aplicativos do Office são servidores do modelo de objeto de componente (COM). COM permite que os clientes chamar servidores COM em threads arbitrários. Para servidores COM que não são thread-safe, COM fornece um mecanismo para serializar chamadas simultâneas para que apenas um thread lógico executa no servidor a qualquer momento. Esse mecanismo é conhecido como o modelo de single-threaded apartment (STA). Porque as chamadas são serializadas, os chamadores podem ser bloqueados por períodos de tempo enquanto o servidor está ocupado ou está lidando com outras chamadas em um thread em segundo plano.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## <a name="knowledge-required-when-using-multiple-threads"></a>Necessário ao usar vários segmentos de dados de Conhecimento  
 Para trabalhar com vários threads, você deve ter pelo menos básico dos seguintes aspectos de multithreading:  
  
-   APIs do Windows  
  
-   COM multithread conceitos  
  
-   Concorrência  
  
-   Sincronização  
  
-   realização de marshaling  
  
 Para obter informações gerais sobre consulte multithreading, [threading gerenciado](/dotnet/standard/threading/).  
  
 Office é executada em STA o principal Noções básicas sobre as implicações de isso torna possível entender como usar vários threads com o Office.  
  
## <a name="basic-multithreading-scenario"></a>Cenário de multithreading básico  
 Código em soluções do Office sempre é executado no thread da interface do usuário principal. Você talvez queira suavizar o desempenho de aplicativos executando uma tarefa separada em um thread em segundo plano. A meta é concluir duas tarefas aparentemente ao mesmo tempo, em vez de uma tarefa seguida por outra, que resulta na execução mais suave (o principal motivo para usar vários threads). Por exemplo, você pode ter seu código de evento no thread principal da interface do usuário do Excel e em um thread em segundo plano, você pode executar uma tarefa que coleta dados de um servidor e atualiza as células na interface de usuário do Excel com os dados do servidor.  
  
## <a name="background-threads-that-call-into-the-office-object-model"></a>Threads em segundo plano que chamam o modelo de objeto do Office  
 Quando um thread em segundo plano faz uma chamada para o aplicativo do Office, a chamada é empacotada automaticamente através do limite de STA. No entanto, não há nenhuma garantia de que o aplicativo do Office pode manipular a chamada no momento em que torna o thread em segundo plano. Há várias possibilidades:  
  
1.  O aplicativo do Office deve bomba de mensagens para a chamada terá a oportunidade de inserir. Se estiver executando pesado processamento sem resposta isso pode levar tempo.  
  
2.  Se outro thread lógico já está no compartimento, não pode inserir o novo thread. Isso geralmente ocorre quando um thread lógico entra o aplicativo do Office e, em seguida, faz uma chamada reentrante para apartment do chamador. O aplicativo está bloqueado, aguardando que chamam retornar.  
  
3.  Excel pode estar em um estado, de modo que ele não pode tratar imediatamente uma chamada de entrada. Por exemplo, o aplicativo do Office pode estar exibindo uma caixa de diálogo modal.  
  
 Possibilidades 2 e 3, COM fornece o [IMessageFilter](http://msdn.microsoft.com/en-us/e12d48c0-5033-47a8-bdcd-e94c49857248) interface. Se o servidor implementa, todas as chamadas inserir por meio de [HandleIncomingCall](http://msdn.microsoft.com/en-us/7e31b518-ef4f-4bdd-b5c7-e1b16383a5be) método. Possibilidade 2, chamadas automaticamente são rejeitadas. Possibilidade 3, o servidor poderá rejeitar a chamada, dependendo das circunstâncias. Se a chamada for rejeitada, o chamador deve decidir o que fazer. Normalmente, o implementa chamador [IMessageFilter](http://msdn.microsoft.com/en-us/e12d48c0-5033-47a8-bdcd-e94c49857248), nesse caso seria notificado da rejeição pelo [RetryRejectedCall](http://msdn.microsoft.com/en-us/3f800819-2a21-4e46-ad15-f9594fac1a3d) método.  
  
 No entanto, no caso de soluções criadas usando as ferramentas de desenvolvimento do Office no Visual Studio, interoperabilidade COM converte rejeitadas todas as chamadas para um <xref:System.Runtime.InteropServices.COMException> ("o filtro de mensagem indicado que o aplicativo está ocupado"). Sempre que você faz um modelo de objeto de chamada em um thread em segundo plano, você deve para estar preparado para lidar com essa exceção. Normalmente, que envolve tentar novamente para um determinado período de tempo e, em seguida, exibir uma caixa de diálogo. No entanto, você também pode criar o thread em segundo plano como STA e, em seguida, registre um filtro de mensagem para esse thread lidar com isso.  
  
## <a name="start-the-thread-correctly"></a>Iniciar o thread corretamente  
 Quando você cria um novo thread STA, defina o estado de apartment como STA antes de iniciar o thread. O exemplo de código a seguir demonstra como fazer isso.  
  
 [!code-csharp[Trin_VstcoreCreatingExcel#5](../vsto/codesnippet/CSharp/Trin_VstcoreCreatingExcelCS/ThisWorkbook.cs#5)]
 [!code-vb[Trin_VstcoreCreatingExcel#5](../vsto/codesnippet/VisualBasic/Trin_VstcoreCreatingExcelVB/ThisWorkbook.vb#5)]  
  
 Para obter mais informações, consulte [práticas recomendadas de threading gerenciado](/dotnet/standard/threading/managed-threading-best-practices).  
  
## <a name="modeless-forms"></a>Formulários sem janela restrita  
 Um formulário sem janela restrita permite algum tipo de interação com o aplicativo enquanto o formulário é exibido. O usuário interage com o formulário e o formulário interage com o aplicativo sem fechar. O modelo de objeto do Office oferece suporte a formulários sem janela restrita gerenciados; No entanto, eles não devem ser usados em um thread em segundo plano.  
  
## <a name="see-also"></a>Consulte também  
 [Threading gerenciado](/dotnet/standard/threading/)  
 [Threading (c#)](/dotnet/csharp/programming-guide/concepts/threading/index) [Threading (Visual Basic)](/dotnet/visual-basic/programming-guide/concepts/threading/index)   
 [Use threads e threading](/dotnet/standard/threading/using-threads-and-threading)   
 [Projetar e criar soluções do Office](../vsto/designing-and-creating-office-solutions.md)  
  
  