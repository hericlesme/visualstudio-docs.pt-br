---
title: "Programando personalizações no nível do documento | Microsoft Docs"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- Sheet3
- thisWorkbook
- thisDocument
- Sheet1
- Sheet2
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ThisDocument class
- Sheet3 class
- ThisWorkbook class
- writing code for Office solutions
- programming [Office development in Visual Studio], document-level customizations
- Sheet1 class
- Office applications [Office development in Visual Studio], document-level customizations
- Sheet2 class
- document-level customizations [Office development in Visual Studio], programming
- application development [Office development in Visual Studio], document-level customizations
ms.assetid: 6c421055-7bea-4db4-a4c9-539b8c78d4ee
caps.latest.revision: "34"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 68135e13a0e78e0250b087713ab459825018ff84
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="programming-document-level-customizations"></a>Programando personalizações no nível do documento
  Quando você estende o Microsoft Office Word ou o Microsoft Office Excel usando uma personalização no nível do documento, você pode executar as seguintes tarefas:  
  
-   Automatize o aplicativo usando o modelo de objeto.  
  
-   Adicione controles para a superfície do documento.  
  
-   Chame o Visual Basic para código Applications (VBA) no documento do assembly de personalização.  
  
-   Chame o código no assembly de personalização do VBA.  
  
-   Gerencie determinados aspectos do documento enquanto ele está em um servidor que não tenha o Microsoft Office instalado.  
  
-   Personalize a interface do usuário (IU) do aplicativo.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Alguns aspectos de escrever código em projetos de nível de documento são diferentes de outros tipos de projetos no Visual Studio. Muitas dessas diferenças são causadas pela maneira como o Office modelos de objeto são expostos para código gerenciado. Para obter mais informações, consulte [escrevendo código em soluções do Office](../vsto/writing-code-in-office-solutions.md).  
  
 Para obter informações gerais sobre as personalizações no nível do documento e outros tipos de soluções que você pode criar usando as ferramentas de desenvolvimento do Office no Visual Studio, consulte [visão geral de desenvolvimento de soluções do Office &#40; VSTO &#41; ](../vsto/office-solutions-development-overview-vsto.md).  
  
## <a name="using-the-generated-classes-in-document-level-projects"></a>Usando as Classes geradas em projetos no nível de documento  
 Quando você cria um projeto no nível do documento, o Visual Studio gera automaticamente uma classe no projeto que você pode usar para começar a escrever seu código. Para o Word e Excel, o Visual Studio gera classes diferentes:  
  
-   Em projetos de nível de documento para Word, a classe é chamada `ThisDocument` por padrão.  
  
-   Projetos no nível de documento para Excel tem várias classes geradas: um para a pasta de trabalho em si e um para cada planilha. Por padrão, essas classes têm os seguintes nomes:  
  
    -   `ThisWorkbook`  
  
    -   `Sheet1`  
  
    -   `Sheet2`  
  
    -   `Sheet3`  
  
 A classe gerada inclui manipuladores de eventos que são chamados quando o documento for aberto ou fechado. Para executar código quando o documento for aberto, adicione código para o `Startup` manipulador de eventos. Para executar código antes que o documento é fechado, adicione código para o `Shutdown` manipulador de eventos. Para obter mais informações, consulte [eventos em projetos do Office](../vsto/events-in-office-projects.md).  
  
### <a name="understanding-the-design-of-the-generated-classes"></a>Noções básicas sobre o Design das Classes geradas  
 Em projetos direcionados a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)], tipos de item de host no [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] são interfaces, portanto as classes geradas não podem derivar a implementação da parte deles. Em vez disso, as classes geradas derivam a maioria de seus membros das seguintes classes base:  
  
-   `ThisDocument`: deriva de <xref:Microsoft.Office.Tools.Word.DocumentBase>.  
  
-   `ThisWorkbook`: deriva de <xref:Microsoft.Office.Tools.Excel.WorkbookBase>.  
  
-   `Sheet` *n* : deriva de <xref:Microsoft.Office.Tools.Excel.WorksheetBase>.  
  
 Essas classes base redirecionam todas as chamadas para seus membros para internas implementações de interfaces de item de host correspondente no [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]. Por exemplo, se você chamar o <xref:Microsoft.Office.Tools.Word.DocumentBase.Protect%2A> método do `ThisDocument` classe, o <xref:Microsoft.Office.Tools.Word.DocumentBase> classe redireciona essa chamada para a implementação interna do <xref:Microsoft.Office.Tools.Word.Document> interface no [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)].  
  
## <a name="accessing-the-object-model-of-the-host-application"></a>Acessando o modelo de objeto do aplicativo Host  
 Para acessar o modelo de objeto do aplicativo host, use os membros da classe gerada em seu projeto. Cada uma dessas classes corresponde a um objeto no modelo de objeto do Excel ou Word e conter a maioria das mesmas propriedades, métodos e eventos. Por exemplo, o `ThisDocument` classe em um projeto no nível de documento para Word fornece a maioria dos mesmos membros como o <xref:Microsoft.Office.Interop.Word.Document> objeto no modelo de objeto do Word.  
  
 O exemplo de código a seguir mostra como usar o modelo de objeto do Word para salvar o documento que faz parte de uma personalização de nível de documento para Word. Este exemplo se destina a ser executado a partir de `ThisDocument` classe.  
  
```vb  
Me.Save()  
```  
  
```csharp  
this.Save();  
```  
  
 Para fazer a mesma coisa de fora de `ThisDocument` classe, use o `Globals` de objeto para acessar o `ThisDocument` classe. Por exemplo, você pode adicionar este código para um arquivo de código do painel de ações, se você quiser incluir um **salvar** botão no painel Ações da interface do usuário.  
  
```vb  
Globals.ThisDocument.Save()  
```  
  
```csharp  
Globals.ThisDocument.Save();  
```  
  
 Porque o `ThisDocument` classe obtém a maioria de seus membros do <xref:Microsoft.Office.Tools.Word.Document> item de host, o `Save` método é chamado neste código é realmente o <xref:Microsoft.Office.Tools.Word.Document.Save%2A> método do <xref:Microsoft.Office.Tools.Word.Document> item de host. Esse método corresponde do <xref:Microsoft.Office.Interop.Word._Document.Save%2A> método o <xref:Microsoft.Office.Interop.Word.Document> objeto no modelo de objeto do Word.  
  
 Para obter mais informações sobre como usar os modelos de objeto do Word e Excel, consulte [visão geral de modelo de objeto do Word](../vsto/word-object-model-overview.md) e [visão geral do modelo de objeto do Excel](../vsto/excel-object-model-overview.md).  
  
 Para obter mais informações sobre o `Globals` de objeto, consulte [acesso Global a objetos em projetos do Office](../vsto/global-access-to-objects-in-office-projects.md).  
  
## <a name="adding-controls-to-documents"></a>Adicionando controles a documentos  
 Para personalizar a interface do usuário do documento, você pode adicionar controles de formulários do Windows ou *hospedar controles* à superfície do documento. Combinando conjuntos diferentes de controles e escrever código, que você pode vincular os controles a dados, coletar informações do usuário e responder a ações do usuário.  
  
 Controles de host são classes que estendem alguns dos objetos no modelo de objeto do Word e Excel. Por exemplo, o <xref:Microsoft.Office.Tools.Excel.ListObject> controle de host fornece toda a funcionalidade do <xref:Microsoft.Office.Interop.Excel.ListObject> no Excel. No entanto, o <xref:Microsoft.Office.Tools.Excel.ListObject> controle de host também tem eventos adicionais e recursos de associação de dados.  
  
 Para obter mais informações, consulte [itens de Host e visão geral dos controles de Host](../vsto/host-items-and-host-controls-overview.md) e [controles dos Windows Forms na visão geral de documentos do Office](../vsto/windows-forms-controls-on-office-documents-overview.md).  
  
## <a name="combining-vba-and-document-level-customizations"></a>Combinando VBA e personalizações no nível do documento  
 Você pode usar o código VBA em um documento que faz parte de uma personalização no nível do documento. Você pode chamar o código do VBA no documento do assembly de personalização, e você também pode configurar seu projeto para habilitar o código do VBA no documento para chamar o código no assembly de personalização.  
  
 Para obter mais informações, consulte [combinando VBA e personalizações no nível do documento](../vsto/combining-vba-and-document-level-customizations.md).  
  
## <a name="managing-documents-on-a-server"></a>Gerenciando documentos em um servidor  
 Você pode gerenciar vários aspectos diferentes de personalizações de nível de documento em um servidor que não tenha o Microsoft Office Word ou o Microsoft Office Excel instalado. Por exemplo, você pode acessar e modificar dados no cache de dados do documento. Você também pode gerenciar o assembly de personalização que é associado ao documento. Por exemplo, você pode remover programaticamente o assembly do documento para que o documento não executa o seu código, ou programaticamente você pode anexar um assembly a um documento.  
  
 Para obter mais informações, consulte [gerenciar documentos em um servidor usando a classe ServerDocument](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md).  
  
## <a name="customizing-the-user-interface-of-microsoft-office-applications"></a>Personalizando a Interface do usuário dos aplicativos do Microsoft Office  
 Usando uma personalização no nível do documento, você pode personalizar a interface do usuário do Word e Excel das seguintes maneiras:  
  
-   Adicione controles de host ou controles de formulários do Windows para a superfície do documento.  
  
     Para obter mais informações, consulte [automatizando o Word usando objetos estendidos](../vsto/automating-word-by-using-extended-objects.md), [automatizando o Excel usando objetos estendidos](../vsto/automating-excel-by-using-extended-objects.md), e [na visão geral de documentos do OfficecontrolesdosWindowsForms](../vsto/windows-forms-controls-on-office-documents-overview.md).  
  
-   Adicione um painel de ações para o documento.  
  
     Para obter mais informações, consulte [visão geral do painel de ações](../vsto/actions-pane-overview.md).  
  
-   Adicione guias personalizadas para a faixa de opções.  
  
     Para obter mais informações, consulte [visão geral da faixa de opções](../vsto/ribbon-overview.md).  
  
-   Adicione grupos personalizados a uma guia interna na faixa de opções.  
  
     Para obter mais informações, consulte [como: personalizar uma guia interna](../vsto/how-to-customize-a-built-in-tab.md).  
  
 Para obter mais informações sobre como personalizar os aplicativos de interface do usuário do Microsoft Office, consulte [personalização da interface do usuário do Office](../vsto/office-ui-customization.md).  
  
## <a name="getting-extended-objects-from-native-office-objects-in-document-level-customizations"></a>Obtendo objetos estendidos de objetos do Office nativo em personalizações no nível do documento  
 Vários manipuladores de eventos para eventos de Office recebem um objeto nativo do Office que representa a pasta de trabalho, planilha ou documento que gerou o evento. Em alguns casos, convém executar algum código somente se a pasta de trabalho ou o documento em sua personalização no nível do documento gerou o evento. Por exemplo, uma personalização de nível de documento para Excel, você talvez queira executar algum código quando o usuário ativar uma das planilhas na pasta de trabalho personalizada, mas não quando o usuário ativar uma planilha em outra pasta que é aberta ao mesmo tempo.  
  
 Quando você tiver um objeto nativo do Office, você pode testar se o objeto tiver sido estendido para um *item de host* ou *controle de host* uma personalização de nível de documento. Itens de host e controles de host são tipos fornecidos pelo [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] que adiciona a funcionalidade para objetos que existem nativamente em modelos de objeto do Word ou Excel (chamado *objetos nativos do Office*). Coletivamente, itens de host e controles de host também são chamados de *objetos estendidos*. Para obter mais informações sobre itens de host e controles de host, consulte [itens de Host e visão geral dos controles de Host](../vsto/host-items-and-host-controls-overview.md).  
  
## <a name="understanding-the-getvstoobject-and-hasvstoobject-methods"></a>Noções básicas sobre os métodos de HasVstoObject e GetVstoObject  
 Para testar um objeto nativo do Office, use os métodos HasVstoObject e GetVstoObject em seu projeto:  
  
-   Use o método HasVstoObject para determinar se o objeto nativo do Office tem um objeto estendido em sua personalização. Este método retorna **true** se o objeto nativo do Office tem um objeto estendido, e **false** caso contrário.  
  
-   Use o método GetVstoObject se você deseja obter o objeto estendido para um objeto nativo do Office. Este método retorna um <xref:Microsoft.Office.Tools.Excel.ListObject>, <xref:Microsoft.Office.Tools.Excel.Workbook>, <xref:Microsoft.Office.Tools.Excel.Worksheet>, ou <xref:Microsoft.Office.Tools.Word.Document> objeto se o objeto nativo Office especificado tem um. Caso contrário, retornará GetVstoObject **nulo**. Por exemplo, o método GetVstoObject retorna um <xref:Microsoft.Office.Tools.Word.Document> se especificado <xref:Microsoft.Office.Interop.Word.Document> é o objeto subjacente para o documento em seu projeto de documento do Word.  
  
 Em projetos de nível de documento, você não pode usar o método GetVstoObject para criar um novo <xref:Microsoft.Office.Tools.Excel.Workbook>, <xref:Microsoft.Office.Tools.Excel.Worksheet>, ou <xref:Microsoft.Office.Tools.Word.Document> item de host em tempo de execução. Você pode usar esse método somente para acessar itens de host existentes que são gerados no seu projeto em tempo de design. Se você quiser criar novos itens de host em tempo de execução, você deve desenvolver um projeto de suplemento do VSTO. Para obter mais informações, consulte [limitações programáticas de itens de Host e controles de Host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md) e [Estendendo documentos do Word e pastas de trabalho do Excel no suplemento do VSTO em tempo de execução](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
## <a name="using-the-getvstoobject-and-hasvstoobject-methods"></a>Usando os métodos de HasVstoObject e GetVstoObject  
 Para chamar o método HasVstoObject e GetVstoObject, use o método Globals.Factory.GetVstoObject ou Globals.Factory.HasVstoObject e passar o objeto nativo do Word ou Excel (como um <xref:Microsoft.Office.Interop.Word.Document> ou <xref:Microsoft.Office.Interop.Excel.Worksheet>) que você deseja testar.  
  
## <a name="see-also"></a>Consulte também  
 [Controles em documentos do Office](../vsto/controls-on-office-documents.md)   
 [Combinando VBA e personalizações no nível do documento](../vsto/combining-vba-and-document-level-customizations.md)   
 [Gerenciando documentos em um servidor usando a classe ServerDocument](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md)   
 [Escrevendo código em soluções do Office](../vsto/writing-code-in-office-solutions.md)  
  
  