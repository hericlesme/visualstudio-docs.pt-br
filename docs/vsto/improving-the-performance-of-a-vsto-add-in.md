---
title: Melhorando o desempenho de um suplemento do VSTO | Microsoft Docs
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
ms.assetid: 03ef25c2-6308-4737-a655-74bbbb472dc2
caps.latest.revision: "14"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: aa8aba456e6912569480305922511f6ffebe674b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="improving-the-performance-of-a-vsto-add-in"></a>Melhorando o desempenho de um suplemento do VSTO
  Você pode dar aos usuários uma experiência melhor otimizando suplementos do VSTO que você cria para o Office aplicativos para que eles iniciarem rapidamente, desligar, abrir itens e executar outras tarefas. Se o suplemento do VSTO para Outlook, você também pode reduzir a chance de que seu suplemento do VSTO será desabilitado devido ao baixo desempenho. Você pode aumentar o desempenho de seu suplemento do VSTO implementando as estratégias a seguir:  
  
-   [Carregar o suplemento do VSTO sob demanda](#Load).  
  
-   [Publicar soluções do Office usando o Windows Installer](#Publish).  
  
-   [Ignorar a reflexão de faixa de opções](#Bypass).  
  
-   [Executar operações caras em um thread de execução separado](#Perform).  
  
 Para obter mais informações sobre como otimizar um suplemento do VSTO do Outlook, consulte [critérios de desempenho para manter os suplementos do VSTO habilitados](http://go.microsoft.com/fwlink/?LinkID=266503).  
  
##  <a name="Load"></a>Carregar o suplemento do VSTO sob demanda  
 Você pode configurar um suplemento do VSTO para carregar somente nas seguintes circunstâncias:  
  
-   Na primeira vez que o usuário inicia o aplicativo depois que o suplemento do VSTO é instalado.  
  
-   Na primeira vez que o usuário interage com o suplemento do VSTO após iniciar o aplicativo a qualquer momento subsequente.  
  
 Por exemplo, o suplemento do VSTO pode preencher uma planilha com os dados quando o usuário escolhe um botão personalizado que é rotulado **obter meus dados**. O aplicativo deve carregar o suplemento do VSTO pelo menos uma vez para que o **obter meus dados** botão pode aparecer na faixa de opções. No entanto, o suplemento do VSTO não carrega novamente quando o usuário inicia o aplicativo na próxima vez. O suplemento do VSTO carrega apenas quando o usuário escolhe o **obter meus dados** botão.  
  
#### <a name="to-configure-a-clickonce-solution-to-load-vsto-add-ins-on-demand"></a>Para configurar uma solução ClickOnce para carregar o suplemento do VSTO sob demanda  
  
1.  Em **Solution Explorer**, escolha o nó do projeto.  
  
2.  Na barra de menus, escolha **Exibir**, **Páginas de Propriedade**.  
  
3.  Sobre o **publicar** guia, escolha o **opções** botão.  
  
4.  No **opções de publicação** caixa de diálogo caixa, escolha o **configurações Office** do item de lista, escolha o **carga sob demanda** opção e, em seguida, escolha o **Okey**botão.  
  
#### <a name="to-configure-a-windows-installer-solution-to-load-vsto-add-ins-on-demand"></a>Para configurar uma solução do Windows Installer para carregar o suplemento do VSTO sob demanda  
  
1.  No registro, defina o `LoadBehavior` entrada o *raiz*\Software\Microsoft\Office\\*ApplicationName*\Addins\\*adicionar ID*chave para **0x10**.  
  
     Para obter mais informações, consulte [entradas do registro para suplementos do VSTO](../vsto/registry-entries-for-vsto-add-ins.md).  
  
#### <a name="to-configure-a-solution-to-load-vsto-add-ins-on-demand-while-you-debug-the-solution"></a>Para configurar uma solução para carregar o suplemento do VSTO sob demanda ao depurar a solução  
  
1.  Criar um script que define o `LoadBehavior` entrada o *raiz*\Software\Microsoft\Office\\*ApplicationName*\Addins\\*adicionar ID* chave para **0x10**.  
  
     O código a seguir mostra um exemplo do script.  
  
    ```  
    [HKEY_CURRENT_USER\Software\Microsoft\Office\Excel\Addins\MyAddIn]  
    "Description"="MyAddIn"  
    "FriendlyName"="MyAddIn"  
    "LoadBehavior"=dword:00000010  
    "Manifest"="c:\\Temp\\MyAddIn\\bin\\Debug\\MyAddIn.vsto|vstolocal"  
  
    ```  
  
2.  Crie um evento de pós-compilação que atualiza o registro usando o script.  
  
     O código a seguir mostra um exemplo de uma cadeia de caracteres de comando que você pode adicionar a um evento de pós-compilação.  
  
    ```  
    regedit /s "$(SolutionDir)$(SolutionName).reg"  
  
    ```  
  
     Para obter informações sobre como criar um evento de pós-compilação em um projeto c#, consulte [como: especificar eventos de compilação &#40; C &#35; &#41; ](/visualstudio/ide/how-to-specify-build-events-csharp).  
  
     Para obter informações sobre como criar um evento de pós-compilação em um projeto do Visual Basic, consulte [como: especificar eventos de compilação &#40; Visual Basic &#41; ](/visualstudio/ide/how-to-specify-build-events-visual-basic).  
  
##  <a name="Publish"></a>Publicar soluções do Office usando o Windows Installer  
 Se você publicar sua solução usando o Windows Installer, o Visual Studio 2010 Tools para Office Runtime ignora as etapas a seguir, quando o suplemento do VSTO é carregado.  
  
-   Validação do esquema de manifesto.  
  
-   Verificando atualizações automaticamente.  
  
-   Validação de assinaturas digitais de manifestos de implantação.  
  
    > [!NOTE]  
    >  Essa abordagem não é necessária se você implantar o suplemento do VSTO em um local seguro nos computadores dos usuários.  
  
 Para obter mais informações, consulte [Implantando uma solução do Office usando o Windows Installer](../vsto/deploying-an-office-solution-by-using-windows-installer.md).  
  
##  <a name="Bypass"></a>Reflexão de faixa de opções de Bypass  
 Se você criar uma solução usando [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)], certifique-se de que seus usuários instalou a versão mais recente do Visual Studio 2010 Tools para Office Runtime quando você implanta a solução. Versões mais antigas do que em tempo de execução são refletidas em assemblies de solução para localizar as personalizações da faixa de opções. Esse processo pode causar o suplemento do VSTO carregar mais lentamente.  
  
 Como alternativa, você pode impedir que qualquer versão do Visual Studio 2010 Tools for Office Runtime usando a reflexão para identificar as personalizações da faixa de opções. Para seguir essa estratégia, substituir o `CreateRibbonExtensibility` método e objetos de retorno explicitamente da faixa de opções. Se o suplemento do VSTO não contém quaisquer personalizações da faixa de opções, retorno `null` dentro do método.  
  
 O exemplo a seguir retorna um objeto de faixa de opções com base no valor de um campo.  
  
 [!code-vb[Trin_Ribbon_Choose_Ribbon#1](../vsto/codesnippet/VisualBasic/trin_ribbon_choose_ribbon_4/ThisWorkbook.vb#1)]
 [!code-csharp[Trin_Ribbon_Choose_Ribbon#1](../vsto/codesnippet/CSharp/trin_ribbon_choose_ribbon_4/ThisWorkbook.cs#1)]  
  
##  <a name="Perform"></a>Executar operações caras em um Thread de execução separado  
 Considere a execução de tarefas demoradas (como tarefas de longa execução, conexões de banco de dados ou outros tipos de chamadas de rede) em um thread separado. Para obter mais informações, consulte [suporte a Threading no Office](../vsto/threading-support-in-office.md).  
  
> [!NOTE]  
>  Todo o código que chama o modelo de objeto do Office deve se executado no thread principal.  
  
## <a name="see-also"></a>Consulte também  
 [Suplementos do VSTO de carregamento por demanda](http://blogs.msdn.com/b/andreww/archive/2008/07/14/demand-loading-vsto-add-ins.aspx)   
 [Carregamento de atraso do CLR em suplementos do Office](http://blogs.msdn.com/b/andreww/archive/2008/04/19/delay-loading-the-clr-in-office-add-ins.aspx)   
 [Desempenho do VSTO: Carregamento de atraso e você (Stephen Peters)](http://blogs.msdn.com/b/vsto/archive/2010/01/07/vsto-performance-delay-loading-and-you.aspx)   
 [Melhorias de desempenho em breve para um Service Pack perto de você (Stephen Peters)](http://blogs.msdn.com/b/vsto/archive/2010/11/30/performance-improvements-coming-soon-to-a-service-pack-near-you-stephen-peters.aspx)   
 [Desempenho do VSTO: Reflexão de faixa de opções (Stephen Peters)](http://blogs.msdn.com/b/vsto/archive/2010/06/03/vsto-performance-ribbon-reflection.aspx)  
  
  