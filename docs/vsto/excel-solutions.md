---
title: "Soluções do Excel | Microsoft Docs"
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
helpviewer_keywords:
- application-level add-ins [Office development in Visual Studio], Excel
- Excel [Office development in Visual Studio], application-level add-ins
- Office solutions [Office development in Visual Studio], Excel
- solutions [Office development in Visual Studio], Excel
- add-ins [Office development in Visual Studio], Excel
- Excel [Office development in Visual Studio], about Excel solutions
- Excel [Office development in Visual Studio]
- documents [Office development in Visual Studio], Excel
- Office documents [Office development in Visual Studio, Excel
- projects [Office development in Visual Studio], Excel
- Excel [Office development in Visual Studio], document-level customizations
- user interfaces [Office development in Visual Studio], Excel
- Office development in Visual Studio, Excel solutions
- document-level customizations [Office development in Visual Studio], Excel
- Office projects [Office development in Visual Studio], Excel
ms.assetid: 34444d54-d7b6-479a-b5b7-a946267081e9
caps.latest.revision: "34"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: f12823ecb3fdc8d90d9f7c3651c6e04e6b0f6635
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="excel-solutions"></a>Soluções do Excel
  O Visual Studio fornece modelos de projeto, que você pode usar para criar personalizações no nível do documento e suplementos do VSTO para o Microsoft Office Excel. Você pode usar essas soluções para automatizar o Excel, estender os recursos do Excel e personalizar a interface de usuário (IU) do Excel. Para obter mais informações sobre as diferenças entre as personalizações no nível do documento e suplementos do VSTO, consulte [visão geral de desenvolvimento de soluções do Office &#40; VSTO &#41; ](../vsto/office-solutions-development-overview-vsto.md).  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
> [!NOTE]  
>  Interessado em desenvolvimento de soluções que estendem a experiência do Office em [várias plataformas](https://dev.office.com/add-in-availability)? Confira a nova [modelo de suplementos do Office](https://dev.office.com/docs/add-ins/overview/office-add-ins). Suplementos do Office têm uma superfície pequena em comparação com suplementos do VSTO e soluções, e você pode criá-los usando quase qualquer tecnologia, como JavaScript, HTML5, CSS3 e XML de programação da web.  
  
 Este tópico fornece as seguintes informações:  
  
-   [Automatizando o Excel](#automating).  
  
-   [Desenvolvimento de personalizações no nível de documento para Excel](#doclevel).  
  
-   [Desenvolvimento de suplementos do VSTO para Excel](#applevel).  
  
-   [Personalizando a interface do usuário do Excel](#UI).  
  
##  <a name="automating"></a>Automatizando o Excel  
 O modelo de objeto do Excel expõe vários tipos que você pode usar para automatizar o Excel. Por exemplo, você pode programaticamente criar gráficos, formatar planilhas e defina os valores de intervalos e células. Para obter mais informações, consulte [visão geral do modelo de objeto do Excel](../vsto/excel-object-model-overview.md).  
  
 Ao desenvolver soluções do Excel no Visual Studio, você também pode usar *itens de host* e *hospedar controles* em suas soluções. Esses são objetos que estendem determinados objetos usados no modelo de objeto do Excel, como o <xref:Microsoft.Office.Interop.Excel.Worksheet> e <xref:Microsoft.Office.Interop.Excel.Range> objetos. Os objetos estendidos se comportam como os objetos do Excel se baseiam, mas adicionar eventos adicionais e recursos de associação de dados para os objetos. Para obter mais informações, consulte [automatizando o Excel usando objetos estendidos](../vsto/automating-excel-by-using-extended-objects.md).  
  
##  <a name="doclevel"></a>Desenvolvimento de personalizações no nível de documento para Excel  
 Uma personalização de nível de documento do Microsoft Office Excel consiste em um assembly que está associado uma pasta de trabalho específica. O assembly normalmente estende a pasta de trabalho, personalizando a interface do usuário e automatizando o Excel. Ao contrário de um VSTO suplemento, que é associado com o Excel em si, funcionalidade que implementam uma personalização está disponível somente quando a pasta de trabalho associada é aberta no Excel.  
  
 Para criar um projeto de personalização de nível de documento para Excel, use os modelos de projeto de modelo do Excel ou de pasta de trabalho do Excel no **novo projeto** caixa de diálogo do Visual Studio. Para obter mais informações, consulte [como: criar projetos do Office no Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
 Para obter mais informações sobre o trabalho de personalizações no nível do documento como, consulte [arquitetura de personalizações em nível de documento](../vsto/architecture-of-document-level-customizations.md).  
  
### <a name="excel-customization-programming-model"></a>Modelo de programação de personalização do Excel  
 Quando você cria um projeto de nível de documento para Excel, o Visual Studio gera várias classes que são a base de sua solução: `ThisWorkbook`, `Sheet1`, `Sheet2`, e `Sheet3`. Essas classes representam a pasta de trabalho e planilhas que estão associadas a sua solução e eles fornecem um ponto de partida para escrever seu código.  
  
 Para obter mais informações sobre esses gerado classes e outros recursos que você pode usar em um projeto de nível de documento, consulte [personalizações de programação de nível de documento](../vsto/programming-document-level-customizations.md).  
  
##  <a name="applevel"></a>Desenvolvimento de suplementos do VSTO para Excel  
 Um suplemento do VSTO para o Microsoft Office Excel consiste em um assembly que é carregado pelo Excel. O assembly normalmente estende o Excel Personalizando a interface do usuário e automatizando o Excel. Ao contrário de uma personalização no nível do documento, que é associada uma pasta de trabalho específica, a funcionalidade que você implementar em um suplemento do VSTO não está restrita a única pasta de trabalho.  
  
 Para criar um projeto de suplemento do VSTO para Excel, use os modelos de projeto de modelo do Excel ou de pasta de trabalho do Excel no **novo projeto** caixa de diálogo do Visual Studio. Para obter mais informações, consulte [como: criar projetos do Office no Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
 Para obter informações gerais sobre o funcionam dos suplementos do VSTO, consulte [suplementos da arquitetura do VSTO](../vsto/architecture-of-vsto-add-ins.md).  
  
 ![link para vídeo](../vsto/media/playvideo.gif "link para vídeo") para uma demonstração de vídeo relacionada, consulte [como fazer i: automatizar PowerPoint de um suplemento do Excel?](http://go.microsoft.com/fwlink/?LinkID=130300).  
  
### <a name="excel-add-in-programming-model"></a>Modelo de programação de suplemento do Excel  
 Quando você cria um projeto de suplemento do VSTO do Excel, o Visual Studio gera uma classe chamada `ThisAddIn`, que é a base da sua solução. Essa classe fornece um ponto de partida para escrever seu código e também expõe o modelo de objeto do Excel para o suplemento do VSTO.  
  
 Para obter mais informações sobre o `ThisAddIn` classe e outros recursos do Visual Studio que você pode usar em um VSTO suplemento, consulte [Programando suplementos do VSTO](../vsto/programming-vsto-add-ins.md).  
  
##  <a name="UI"></a>Personalizando a Interface do usuário do Excel  
 Há várias maneiras diferentes de personalizar a interface do usuário do Excel. Algumas opções estão disponíveis para todos os tipos de projeto e outras opções estão disponíveis somente para suplementos do VSTO ou personalizações no nível do documento.  
  
### <a name="options-for-all-project-types"></a>Opções para todos os tipos de projeto  
 A tabela a seguir lista as opções de personalização que estão disponíveis para personalizações no nível do documento e suplementos do VSTO.  
  
|Tarefa|Para obter mais informações|  
|----------|--------------------------|  
|Personalize a faixa de opções.|[Visão geral da faixa de opções](../vsto/ribbon-overview.md)|  
|Adicione controles de formulários do Windows ou controles estendidos do Excel em uma planilha na pasta de trabalho personalizada para uma personalização no nível do documento, ou em qualquer pasta de trabalho para um suplemento do VSTO.|[Como adicionar controles do Windows Forms a documentos do Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)<br /><br /> [Como adicionar controles de gráfico a planilhas](../vsto/how-to-add-chart-controls-to-worksheets.md)<br /><br /> [Como adicionar controles ListObject a planilhas](../vsto/how-to-add-listobject-controls-to-worksheets.md)<br /><br /> [Como adicionar controles NamedRange a planilhas](../vsto/how-to-add-namedrange-controls-to-worksheets.md)|  
  
### <a name="options-for-document-level-customizations"></a>Opções para personalizações no nível do documento  
 A tabela a seguir lista as opções de personalização que estão disponíveis apenas para personalizações no nível do documento.  
  
|Tarefa|Para obter mais informações|  
|----------|--------------------------|  
|Adicione um painel de ações para a pasta de trabalho.|[Visão geral do painel Ações](../vsto/actions-pane-overview.md)<br /><br /> [Como adicionar um painel Ações a documentos do Word ou pastas de trabalho do Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)|  
|Adicione controles de intervalo estendido que são mapeados para nós XML em uma planilha.|[Como adicionar controles XMLMappedRange a planilhas](../vsto/how-to-add-xmlmappedrange-controls-to-worksheets.md)|  
  
### <a name="options-for-vsto-add-ins"></a>Opções para suplementos VSTO  
 A tabela a seguir lista as opções de personalização que estão disponíveis somente para suplementos do VSTO.  
  
|Tarefa|Para obter mais informações|  
|----------|--------------------------|  
|Crie um painel tarefa personalizada.|[Painéis de tarefas personalizados](../vsto/custom-task-panes.md)|  
  
### <a name="related-topics"></a>Tópicos relacionados  
  
|Título|Descrição|  
|-----------|-----------------|  
|[Visão geral do modelo de objeto do Excel](../vsto/excel-object-model-overview.md)|Fornece uma visão geral dos principais tipos fornecidos pelo modelo de objeto do Excel.|  
|[Automatizando o Excel usando objetos estendidos](../vsto/automating-excel-by-using-extended-objects.md)|Fornece informações sobre objetos estendidos (fornecido pelo [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]) que você pode usar em soluções do Excel.|  
|[Globalização e localização de soluções do Excel](../vsto/globalization-and-localization-of-excel-solutions.md)|Contém informações sobre considerações especiais para soluções do Excel que serão executadas em computadores que têm configurações diferentes do inglês do Windows.|  
|[Visão geral de controles do Windows Forms em documentos do Office](../vsto/windows-forms-controls-on-office-documents-overview.md)|Descreve como adicionar controles de formulários do Windows para planilhas do Excel.|  
|[Instruções passo a passo: criando a primeira personalização no nível de documento para Excel](../vsto/walkthrough-creating-your-first-document-level-customization-for-excel.md)|Demonstra como criar uma personalização básica de nível de documento para Excel.|  
|[Instruções passo a passo: criando o primeiro suplemento do VSTO para Excel](../vsto/walkthrough-creating-your-first-vsto-add-in-for-excel.md)|Demonstra como criar um básico do VSTO suplemento para Excel.|  
|[Instruções passo a passo: adicionando controles a uma planilha no tempo de execução no projeto de suplemento do VSTO](../vsto/walkthrough-adding-controls-to-a-worksheet-at-run-time-in-vsto-add-in-project.md)|Demonstra como adicionar um botão dos Windows Forms, um <xref:Microsoft.Office.Tools.Excel.NamedRange>e um <xref:Microsoft.Office.Tools.Excel.ListObject> para uma planilha em tempo de execução usando um suplemento do VSTO.|
|[Noções básicas sobre coautoria e suplementos](./understanding-coauthoring-and-addins.md)|Descreve os ajustes que talvez você precise fazer suas soluções para acomodar coautoria.|  
|[Excel 2010 no desenvolvimento do Office](http://go.microsoft.com/fwlink/?LinkId=199011)|Fornece links para artigos e documentação de referência sobre como desenvolver soluções do Excel. Eles não são específicos para desenvolvimento do Office usando o Visual Studio.|  
  
  