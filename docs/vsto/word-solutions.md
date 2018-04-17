---
title: Soluções do Word | Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- solutions [Office development in Visual Studio], Word
- Office projects [Office development in Visual Studio], Word
- application-level add-ins [Office development in Visual Studio], Word
- Word [Office development in Visual Studio]
- projects [Office development in Visual Studio], Word
- Word [Office development in Visual Studio], about Word solutions
- Office solutions [Office development in Visual Studio], Word
- Word [Office development in Visual Studio], application-level add-ins
- documents [Office development in Visual Studio], Word
- Office development in Visual Studio, Word solutions
- add-ins [Office development in Visual Studio], Word
- Word [Office development in Visual Studio], document-level customizations
- user interfaces [Office development in Visual Studio], Word
- Office documents [Office development in Visual Studio, Word
- document-level customizations [Office development in Visual Studio], Word
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 44cd5633d7cc03fb78c6508c24a117a0500fa142
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="word-solutions"></a>Soluções do Word
  O Visual Studio fornece modelos de projeto, que você pode usar para criar personalizações no nível do documento e suplementos do VSTO para o Microsoft Office Word. Você pode usar essas soluções para automatizar o Word, estender os recursos do Word e personalizar a interface do usuário do Word (IU). Para obter mais informações sobre as diferenças entre as personalizações no nível do documento e suplementos do VSTO, consulte [visão geral de desenvolvimento de soluções do Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
> [!NOTE]  
>  Interessado em desenvolvimento de soluções que estendem a experiência do Office em [várias plataformas](https://dev.office.com/add-in-availability)? Confira a nova [modelo de suplementos do Office](https://dev.office.com/docs/add-ins/overview/office-add-ins). Suplementos do Office têm uma superfície pequena em comparação com suplementos do VSTO e soluções, e você pode criá-los usando quase qualquer tecnologia, como JavaScript, HTML5, CSS3 e XML de programação da web.  
  
 Este tópico fornece as seguintes informações:  
  
-   [Automatizando o Word](#automating).  
  
-   [Desenvolvimento de personalizações no nível de documento para Word](#doclevel).  
  
-   [Desenvolvimento de suplementos do VSTO para Word](#applevel).  
  
-   [Personalizando a interface do usuário do Word](#UI).  
  
##  <a name="automating"></a> Automatizando o Word  
 O modelo de objeto do Word expõe vários tipos que você pode usar para automatizar o Word. Por exemplo, você pode programaticamente criar tabelas, formatar documentos e definir o texto em intervalos e parágrafos. Para obter mais informações, consulte [visão geral de modelo de objeto do Word](../vsto/word-object-model-overview.md).  
  
 Ao desenvolver soluções do Word no Visual Studio, você também pode usar *itens de host* e *hospedar controles* em suas soluções. Esses são objetos que estendem determinados objetos usados no modelo de objeto do Word, como o <xref:Microsoft.Office.Interop.Word.Document> e <xref:Microsoft.Office.Interop.Word.ContentControl> objetos. Os objetos estendidos se comportam como os objetos do Word que eles se baseiam, mas adicionar eventos adicionais e recursos de associação de dados para os objetos. Para obter mais informações, consulte [automatizando o Word usando objetos estendidos](../vsto/automating-word-by-using-extended-objects.md).  
  
##  <a name="doclevel"></a> Desenvolvimento de personalizações no nível de documento para Word  
 Uma personalização no nível do documento para o Microsoft Office Word consiste em um assembly que está associado um documento específico. O assembly normalmente estende o documento Personalizando a interface do usuário e automatizando o Word. Ao contrário de um VSTO suplemento, que é associado com a palavra em si, funcionalidade que implementam uma personalização está disponível somente quando o documento associado é aberto no Word.  
  
 Para criar um projeto de personalização de nível de documento para Word, usar os modelos de projeto de documento do Word ou o modelo do Word no **novo projeto** caixa de diálogo do Visual Studio. Para obter mais informações, consulte [como: criar projetos do Office no Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
 Para obter mais informações sobre o trabalho de personalizações no nível do documento como, [arquitetura de personalizações em nível de documento](../vsto/architecture-of-document-level-customizations.md).  
  
### <a name="word-customization-programming-model"></a>Personalização do modelo de programação do Word  
 Quando você cria um projeto de nível de documento para Word, o Visual Studio gera uma classe chamada `ThisDocument`, que é a base da sua solução. Essa classe representa o documento que está associado com sua solução, e ele fornece um ponto de partida para escrever seu código.  
  
 Para obter mais informações sobre o `ThisDocument` classe e outros recursos que você pode usar em um projeto de nível de documento, consulte [personalizações de programação de nível de documento](../vsto/programming-document-level-customizations.md).  
  
##  <a name="applevel"></a> Desenvolvimento de suplementos do VSTO para Word  
 Um suplemento do VSTO para o Microsoft Office Word consiste em um assembly que é carregado por palavra. O assembly normalmente estende palavra Personalizando a interface do usuário e automatizando o Word. Diferentemente de uma personalização no nível do documento, que é associada um documento específico, a funcionalidade que você implementar em um suplemento do VSTO não está restrita a um único documento.  
  
 Para criar um projeto de suplemento do VSTO para Word, usar os modelos de projeto do suplemento do Word no **novo projeto** caixa de diálogo do Visual Studio. Para obter mais informações, consulte [como: criar projetos do Office no Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
 Para obter informações gerais sobre o funcionam dos suplementos do VSTO, consulte [suplementos da arquitetura do VSTO](../vsto/architecture-of-vsto-add-ins.md).  
  
### <a name="word-add-in-programming-model"></a>Word adicionar no modelo de programação  
 Quando você cria um projeto de suplemento do VSTO do Word, o Visual Studio gera uma classe chamada `ThisAddIn`, que é a base da sua solução. Essa classe fornece um ponto de partida para escrever seu código e também expõe o modelo de objeto do Word para o suplemento do VSTO.  
  
 Para obter mais informações sobre o `ThisAddIn` classe e outros recursos que você pode usar em um VSTO suplemento, consulte [Programando suplementos do VSTO](../vsto/programming-vsto-add-ins.md).  
  
##  <a name="UI"></a> Personalizando a Interface do usuário do Word  
 Há várias maneiras diferentes de personalizar a interface do usuário do Word. Algumas opções estão disponíveis para todos os tipos de projeto e outras opções estão disponíveis somente para suplementos do VSTO ou personalizações no nível do documento.  
  
### <a name="options-for-all-project-types"></a>Opções para todos os tipos de projeto  
 A tabela a seguir lista as opções de personalização que estão disponíveis para personalizações no nível do documento e suplementos do VSTO.  
  
|Tarefa|Para obter mais informações|  
|----------|--------------------------|  
|Personalize a faixa de opções.|[Visão geral da faixa de opções](../vsto/ribbon-overview.md)|  
|Adicione controles de formulários do Windows ou controles estendidos de palavras para o documento personalizado (para uma personalização no nível do documento) ou para qualquer documento aberto (para um Add-in do VSTO).|[Como adicionar controles do Windows Forms a documentos do Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)<br /><br /> [Como adicionar controles de conteúdo a documentos do Word](../vsto/how-to-add-content-controls-to-word-documents.md)<br /><br /> [Como adicionar controles de indicador a documentos do Word](../vsto/how-to-add-bookmark-controls-to-word-documents.md)|  
  
### <a name="options-for-document-level-customizations"></a>Opções para personalizações no nível do documento  
 A tabela a seguir lista as opções de personalização que estão disponíveis apenas para personalizações no nível do documento.  
  
|Tarefa|Para obter mais informações|  
|----------|--------------------------|  
|Adicione um painel de ações para o documento.|[Visão geral do painel Ações](../vsto/actions-pane-overview.md)<br /><br /> [Como adicionar um painel Ações a documentos do Word ou pastas de trabalho do Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)|  
|Adicione controles XMLNode e XMLNodes estendidos para a superfície do documento.|[Como adicionar controles XMLNode a documentos do Word](../vsto/how-to-add-xmlnode-controls-to-word-documents.md)<br /><br /> [Como adicionar controles XMLNodes a documentos do Word](../vsto/how-to-add-xmlnodes-controls-to-word-documents.md)|  
  
### <a name="options-for-vsto-add-ins"></a>Opções para suplementos VSTO  
 A tabela a seguir lista as opções de personalização que estão disponíveis somente para suplementos do VSTO.  
  
|Tarefa|Para obter mais informações|  
|----------|--------------------------|  
|Crie um painel tarefa personalizada.|[Painéis de tarefas personalizados](../vsto/custom-task-panes.md)|  
  
### <a name="related-topics"></a>Tópicos relacionados  
  
|Título|Descrição|  
|-----------|-----------------|  
|[Visão geral do modelo de objeto do Word](../vsto/word-object-model-overview.md)|Fornece uma visão geral dos principais tipos fornecidos pelo modelo de objeto do Word.|  
|[Automatizando o Word usando objetos estendidos](../vsto/automating-word-by-using-extended-objects.md)|Fornece informações sobre objetos estendidos (fornecido pelo [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]) que você pode usar em soluções do Word.|  
|[Visão geral de controles do Windows Forms em documentos do Office](../vsto/windows-forms-controls-on-office-documents-overview.md)|Descreve como adicionar controles de Windows Forms a documentos do Word.|  
|[Instruções passo a passo: criando a primeira personalização no nível de documento para Word](../vsto/walkthrough-creating-your-first-document-level-customization-for-word.md)|Demonstra como criar uma personalização básica de nível de documento para Word.|  
|[Instruções passo a passo: criando o seu primeiro suplemento VSTO para o Word](../vsto/walkthrough-creating-your-first-vsto-add-in-for-word.md)|Demonstra como criar um Add-in básico do VSTO para Word.|  
|[Instruções passo a passo: adicionando controles a um documento no tempo de execução em um suplemento do VSTO](../vsto/walkthrough-adding-controls-to-a-document-at-run-time-in-a-vsto-add-in.md)|Demonstra como adicionar um Windows Forms botão e uma <xref:Microsoft.Office.Tools.Word.RichTextContentControl> para um documento em tempo de execução usando um suplemento do VSTO.|  
|[Word 2010 no desenvolvimento do Office](http://go.microsoft.com/fwlink/?LinkId=199020)|Fornece links para artigos e documentação de referência sobre como desenvolver soluções do Word (não específicas ao desenvolvimento do Office usando o Visual Studio).|  
  
  