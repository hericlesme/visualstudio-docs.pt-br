---
title: 'Preparação da depuração: Aplicativos dos Windows Forms | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging Windows applications
- Windows applications, debugging
- debugging [Visual Studio], Windows applications
- debugging [C#], Windows applications
- debugging [Visual Basic], Windows applications
ms.assetid: 7092ee7f-8378-4def-aef8-1695bd97cf14
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bde2b6d2885a83057a0211f6da4f9e4ff65ef46f
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2018
---
# <a name="debugging-preparation-windows-forms-applications"></a>Preparação da depuração: aplicativos dos Windows Forms
O modelo de projeto do Windows Forms (.NET) cria um aplicativo do Windows Forms. Depurar esse tipo de aplicativo no [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] é simples. Para obter mais informações, consulte [criando um projeto de aplicativo do Windows](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa).  
  
 Quando você cria um projeto do Windows Forms com o modelo de projeto, o [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] cria automaticamente as configurações necessárias para as configurações de depuração e versão. Se necessário, você pode alterar essas configurações. Essas configurações podem ser alteradas no  **\<nome do projeto > páginas de propriedade** caixa de diálogo (**meu projeto** no Visual Basic).  
  
 Para obter mais informações, consulte [configurações de propriedade recomendadas](../debugger/managed-debugging-recommended-property-settings.md).  
  
 A tabela a seguir exibe uma configuração de propriedade recomendada adicional.  
  
### <a name="configuration-properties-in-debug-tab"></a>Propriedades de configuração na guia Depurar  
  
|**Nome da propriedade**|**Configuração**|  
|-----------------------|-----------------|  
|**Iniciar ação**|-Definir para **projeto de início,** maioria das vezes. Definido como **Iniciar programa externo** se você deseja iniciar outro executável quando você inicia a depuração (geralmente para depuração de DLLs).|  
  
 Você pode depurar aplicativos do Windows Forms de dentro do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ou anexando a um aplicativo já em execução. Para obter mais informações sobre como anexar, consulte [anexar a processos em execução](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).  
  
### <a name="to-debug-a-c-f-or-visual-basic-windows-forms-application"></a>Para depurar um aplicativo C#, F# ou Windows Forms do Visual Basic  
  
1.  Abra o projeto no [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
2.  Crie pontos de interrupção conforme o necessário.  
  
     Como os aplicativos do Windows Forms são controlados por eventos, seus pontos de interrupção entrarão no código do manipulador de eventos ou nos métodos chamados pelo código do manipulador de eventos. Eventos comuns nos quais colocar pontos de interrupção incluem:  
  
    1.  Os eventos associados a um controle, como Clique, Insira etc.  
  
    2.  Os eventos associados à inicialização e o desligamento do aplicativo, como Carregar, Ativado etc.  
  
    3.  Foco e eventos de validação.  
  
     Para obter mais informações, consulte [Criando manipuladores de eventos nos Windows Forms](/dotnet/framework/winforms/creating-event-handlers-in-windows-forms).  
  
3.  Sobre o **depurar** menu, clique em **iniciar**.  
  
4.  A depuração usando as técnicas discutidas na [Noções básicas do depurador](../debugger/debugger-basics.md).  
  
## <a name="see-also"></a>Consulte também  
 [Depurando código gerenciado](../debugger/debugging-managed-code.md)   
 [Tipos de projeto do C#, F# e Visual Basic](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)   
 [Como: definir configurações de depuração e versão](../debugger/how-to-set-debug-and-release-configurations.md)   
 [Configurações do projeto para configurações de depuração de C#](../debugger/project-settings-for-csharp-debug-configurations.md)   
 [Configurações do projeto para uma configuração de depuração do Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)   
 [Anexar a processos em execução](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [Windows Forms](/dotnet/framework/winforms/index)