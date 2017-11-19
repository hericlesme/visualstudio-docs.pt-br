---
title: Programando suplementos do VSTO | Microsoft Docs
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VST.ProjectItem.Addin
- VST.ProjectItem.AddinProject
- thisAddIn
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ICustomTaskPaneConsumer interface
- add-ins [Office development in Visual Studio], programming
- IRibbonExtensibility interface
- UI customizing [Office development in Visual Studio]
- Office applications [Office development in Visual Studio], application-level add-ins
- programming [Office development in Visual Studio], application-level add-ins
- ThisAddIn class
- user interfaces [Office development in Visual Studio], customizing
- writing code for Office solutions
- host items [Office development in Visual Studio], AddIn
- application development [Office development in Visual Studio], application-level add-ins
- add-ins [Office development in Visual Studio], ThisAddIn class
- application-level add-ins [Office development in Visual Studio], ThisAddIn class
- FormRegionStartup interface
- ThisAddIn_Startup
- application-level add-ins [Office development in Visual Studio], programming
- ThisAddIn_Shutdown
ms.assetid: c534786d-2833-4afa-9e4c-4633f46b9eed
caps.latest.revision: "70"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 1516922d91bf517f2bf9e9512d6c5a00cb1ae868
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="programming-vsto-add-ins"></a>Programando suplementos do VSTO
  Quando você estende um aplicativo do Microsoft Office, criando um suplemento do VSTO, você escreve código diretamente em relação a `ThisAddIn` classe em seu projeto. Você pode usar essa classe para executar tarefas como acessar o modelo de objeto do aplicativo host do Microsoft Office, personalizando a interface do usuário (IU) do aplicativo e expor os objetos no seu suplemento do VSTO para outras soluções do Office.  
  
 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]  
  
 Alguns aspectos de escrever código em projetos de suplemento do VSTO são diferentes de outros tipos de projetos no Visual Studio. Muitas dessas diferenças são causadas pela maneira como o Office modelos de objeto são expostos para código gerenciado. Para obter mais informações, consulte [escrevendo código em soluções do Office](../vsto/writing-code-in-office-solutions.md).  
  
 Para obter informações gerais sobre suplementos do VSTO e outros tipos de soluções que você pode criar usando as ferramentas de desenvolvimento do Office no Visual Studio, consulte [visão geral de desenvolvimento de soluções do Office &#40; VSTO &#41; ](../vsto/office-solutions-development-overview-vsto.md).  
  
## <a name="using-the-thisaddin-class"></a>Usando a classe ThisAddIn  
 Você pode começar a escrever seu código de suplemento do VSTO no `ThisAddIn` classe. O Visual Studio gera automaticamente essa classe no ThisAddIn (em [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)]) ou arquivo de código ThisAddIn.cs (em c#) em seu projeto de suplemento do VSTO. O [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] automaticamente cria uma instância dessa classe para você quando o aplicativo do Microsoft Office carrega o suplemento do VSTO.  
  
 Há dois manipuladores de eventos padrão no `ThisAddIn` classe. Para executar código quando o suplemento do VSTO é carregado, adicione código para o `ThisAddIn_Startup` manipulador de eventos. Para executar código antes do suplemento do VSTO é descarregado, adicione código para o `ThisAddIn_Shutdown` manipulador de eventos. Para obter mais informações sobre esses manipuladores de eventos, consulte [eventos em projetos do Office](../vsto/events-in-office-projects.md).  
  
> [!NOTE]  
>  No Outlook, por padrão o `ThisAddIn_Shutdown` manipulador de eventos não é sempre chamado quando o suplemento do VSTO é descarregado. Para obter mais informações, consulte [eventos em projetos do Office](../vsto/events-in-office-projects.md).  
  
### <a name="accessing-the-object-model-of-the-host-application"></a>Acessando o modelo de objeto do aplicativo Host  
 Para acessar o modelo de objeto do aplicativo host, use o `Application` campo o `ThisAddIn` classe. Esse campo retorna um objeto que representa a instância atual do aplicativo host. A tabela a seguir lista o tipo do valor de retorno para o `Application` campo em cada projeto de suplemento do VSTO.  
  
|aplicativo de host|Tipo de valor de retorno|  
|----------------------|-----------------------|  
|Microsoft Office Excel|<xref:Microsoft.Office.Interop.Excel.Application>|  
|Microsoft Office InfoPath|<xref:Microsoft.Office.Interop.InfoPath.Application>|  
|Microsoft Office Outlook|<xref:Microsoft.Office.Interop.Outlook.Application>|  
|Microsoft Office PowerPoint|<xref:Microsoft.Office.Interop.PowerPoint.Application>|  
|Microsoft Office Project|Microsoft.Office.Interop.MSProject.Application|  
|Microsoft Office Visio|Microsoft.Office.Interop.Visio.Application|  
|Microsoft Office Word|<xref:Microsoft.Office.Interop.Word.Application>|  
  
 O exemplo de código a seguir mostra como usar o `Application` campo para criar uma nova pasta de trabalho em um suplemento do VSTO para o Microsoft Office Excel. Este exemplo se destina a ser executado a partir de `ThisAddIn` classe.  
  
```vb  
Dim newWorkbook As Excel.Workbook = Me.Application.Workbooks.Add()  
```  
  
```csharp  
Excel.Workbook newWorkbook = this.Application.Workbooks.Add(System.Type.Missing);  
```  
  
 Para fazer a mesma coisa de fora de `ThisAddIn` classe, use o `Globals` de objeto para acessar o `ThisAddIn` classe. Para obter mais informações sobre o `Globals` de objeto, consulte [acesso Global a objetos em projetos do Office](../vsto/global-access-to-objects-in-office-projects.md).  
  
```vb  
Dim newWorkbook As Excel.Workbook = Globals.ThisAddIn.Application.Workbooks.Add()  
```  
  
```csharp  
Excel.Workbook newWorkbook = Globals.ThisAddIn.Application.Workbooks.Add(System.Type.Missing);  
```  
  
 Para obter mais informações sobre os modelos de objeto de aplicativos específicos do Microsoft Office, consulte os tópicos a seguir:  
  
-   [Visão geral do modelo de objeto do Excel](../vsto/excel-object-model-overview.md)  
  
-   [Visão geral do modelo de objeto do Word](../vsto/word-object-model-overview.md)  
  
-   [Visão geral do modelo de objeto do Outlook](../vsto/outlook-object-model-overview.md)  
  
-   [Soluções InfoPath](../vsto/infopath-solutions.md)  
  
-   [Soluções PowerPoint](../vsto/powerpoint-solutions.md)  
  
-   [Soluções do projeto](../vsto/project-solutions.md)  
  
-   [Visão geral do modelo de objeto do Visio](../vsto/visio-object-model-overview.md)  
  
###  <a name="AccessingDocuments"></a>Acessar um documento quando inicia o aplicativo do Office  
 Nem todos os [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] aplicativos abrem um documento automaticamente quando você inicia e nenhum do [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] aplicativos abrem um documento, quando você iniciá-los. Portanto, não adicione código de `ThisAdd-In_Startup` manipulador de eventos se o código requer um documento a ser aberto. Em vez disso, adicione esse código para um evento que o aplicativo do Office emite quando um usuário cria ou abre um documento. Dessa forma, você pode garantir que um documento está aberto antes de seu código executa operações nele.  
  
 O exemplo de código a seguir funciona com um documento do Word somente quando o usuário cria um documento ou abre um documento existente.  
  
 [!code-csharp[Trin_WordAddIn_Menus#3](../vsto/codesnippet/CSharp/trin_wordaddin_menus.cs/thisaddin.cs#3)]
 [!code-vb[Trin_WordAddIn_Menus#3](../vsto/codesnippet/VisualBasic/trin_wordaddin_menus.vb/thisaddin.vb#3)]  
  
### <a name="thisaddin-members-to-use-for-other-tasks"></a>Membros de classe ThisAddIn para uso para outras tarefas  
 A tabela a seguir descreve outras tarefas comuns e mostra quais membros do `ThisAddIn` classe que você pode usar para executar as tarefas.  
  
|Tarefa|Membro a ser usado|  
|----------|-------------------|  
|Execute o código para inicializar o suplemento do VSTO quando o suplemento do VSTO é carregado.|Adicione código para o `ThisAddIn_Startup` método. Este é o manipulador de eventos padrão para o <xref:Microsoft.Office.Tools.AddInBase.Startup> evento. Para obter mais informações, consulte [eventos em projetos do Office](../vsto/events-in-office-projects.md).|  
|Execute o código para limpar os recursos usados pelo suplemento do VSTO antes do suplemento do VSTO é descarregado.|Adicione código para o `ThisAddIn_Shutdown` método. Este é o manipulador de eventos padrão para o <xref:Microsoft.Office.Tools.AddInBase.Shutdown> evento. Para obter mais informações, consulte [eventos em projetos do Office](../vsto/events-in-office-projects.md). **Observação:** no Outlook, por padrão o `ThisAddIn_Startup` manipulador de eventos não é sempre chamado quando o suplemento do VSTO é descarregado. Para obter mais informações, consulte [eventos em projetos do Office](../vsto/events-in-office-projects.md).|  
|Exiba um painel tarefa personalizada.|Use o `CustomTaskPanes` campo. Para obter mais informações, consulte [painéis de tarefas personalizados](../vsto/custom-task-panes.md).|  
|Expor objetos no seu suplemento do VSTO para outras soluções do Microsoft Office.|Substituir o método <xref:Microsoft.Office.Tools.AddInBase.RequestComAddInAutomationService%2A>. Para obter mais informações, consulte [chamando código em suplementos do VSTO de outras soluções do Office](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md).|  
|Personalize um recurso do Microsoft Office System, implementando uma interface de extensibilidade.|Substituir o <xref:Microsoft.Office.Tools.AddInBase.RequestService%2A> método para retornar uma instância de uma classe que implementa a interface. Para obter mais informações, consulte [personalização da interface do usuário recursos por usando Interfaces de extensibilidade](../vsto/customizing-ui-features-by-using-extensibility-interfaces.md). **Observação:** para personalizar a faixa de opções da interface do usuário, você também pode substituir o <xref:Microsoft.Office.Tools.AddInBase.CreateRibbonExtensibilityObject%2A> método.|  
  
### <a name="understanding-the-design-of-the-thisaddin-class"></a>Noções básicas sobre o Design da classe ThisAddIn  
 Em projetos direcionados a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)], <xref:Microsoft.Office.Tools.AddIn> é uma interface. O `ThisAddIn` classe deriva de <xref:Microsoft.Office.Tools.AddInBase> classe. Essa classe base redireciona todas as chamadas para seus membros para uma implementação interna do <xref:Microsoft.Office.Tools.AddIn> interface o [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)].  
  
 Em projetos de suplemento do VSTO para Outlook, o `ThisAddIn` classe deriva da classe Microsoft.Office.Tools.Outlook.OutlookAddIn em projetos direcionados ao .NET Framework 3.5 e, na <xref:Microsoft.Office.Tools.Outlook.OutlookAddInBase> em projetos direcionados a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]. Essas classes base fornecem algumas funcionalidades adicionais para dar suporte a regiões de formulário. Para obter mais informações sobre regiões de formulário, consulte [criar regiões de formulário do Outlook](../vsto/creating-outlook-form-regions.md).  
  
## <a name="customizing-the-user-interface-of-microsoft-office-applications"></a>Personalizando a Interface do usuário dos aplicativos do Microsoft Office  
 Programaticamente, você pode personalizar os aplicativos de interface do usuário do Microsoft Office usando um suplemento do VSTO. Por exemplo, pode personalizar a faixa de opções, exibir um painel tarefa personalizada ou criar uma região de formulário personalizado no Outlook. Para obter mais informações, consulte [personalização da interface do usuário do Office](../vsto/office-ui-customization.md).  
  
 Visual Studio fornece classes que você pode usar para criar regiões de formulário do Outlook, personalizações da faixa de opções e painéis de tarefas personalizados e designers. Esses designers e classes de ajudam a simplificar o processo de personalizar esses recursos. Para obter mais informações, consulte [painéis de tarefas personalizados](../vsto/custom-task-panes.md), [Designer da faixa de opções](../vsto/ribbon-designer.md), e [criar regiões de formulário do Outlook](../vsto/creating-outlook-form-regions.md).  
  
 Se você quiser personalizar um desses recursos de forma que não há suporte para as classes e designers, você também pode personalizar esses recursos, Implementando um *interface de extensibilidade* no seu suplemento do VSTO. Para obter mais informações, consulte [personalização da interface do usuário recursos por usando Interfaces de extensibilidade](../vsto/customizing-ui-features-by-using-extensibility-interfaces.md).  
  
 Além disso, você pode modificar os documentos de interface do usuário do Word e pastas de trabalho do Excel por gerar itens de host que estendem o comportamento de documentos e pastas de trabalho. Isso permite que você adicione controles gerenciados a documentos e planilhas. Para obter mais informações, consulte [Estendendo documentos do Word e pastas de trabalho do Excel no suplemento do VSTO em tempo de execução](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
## <a name="calling-code-in-vsto-add-ins-from-other-solutions"></a>Chamando código em suplementos do VSTO de outras soluções  
 Você pode expor os objetos no seu suplemento do VSTO para outras soluções, incluindo outras soluções do Office. Isso é útil se o suplemento do VSTO fornece um serviço que você deseja habilitar outras soluções para usar. Por exemplo, se você tiver um suplemento do VSTO para o Microsoft Office Excel que executa cálculos nos dados financeiros de um serviço web, outras soluções podem executar esses cálculos chamando o suplemento do Excel VSTO em tempo de execução.  
  
 Para obter mais informações, consulte [chamando código em suplementos do VSTO de outras soluções do Office](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md).  
  
## <a name="see-also"></a>Consulte também  
 [Desenvolvendo soluções do Office](../vsto/developing-office-solutions.md)   
 [Estendendo documentos do Word e pastas de trabalho do Excel em suplementos do VSTO em tempo de execução](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Chamando código em suplementos do VSTO de outras soluções do Office](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md)   
 [Passo a passo: Chamando código em um suplemento do VSTO por meio do VBA](../vsto/walkthrough-calling-code-in-a-vsto-add-in-from-vba.md)   
 [Personalizando recursos de interface do usuário usando Interfaces de extensibilidade](../vsto/customizing-ui-features-by-using-extensibility-interfaces.md)   
 [Como: criar projetos do Office no Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Arquitetura de suplementos do VSTO](../vsto/architecture-of-vsto-add-ins.md)   
 [Escrevendo código em soluções do Office](../vsto/writing-code-in-office-solutions.md)  
  
  