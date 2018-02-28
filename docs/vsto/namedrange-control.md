---
title: Controle NamedRange | Microsoft Docs
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VST.Toolbox.Range
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ranges, named
- NamedRange control, events
- NamedRange control, data binding
- NamedRange control
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload:
- office
ms.openlocfilehash: 22adc003c10e95de0e701eb3f382d9e530b28acf
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/10/2018
---
# <a name="namedrange-control"></a>Controle NamedRange
  O <xref:Microsoft.Office.Tools.Excel.NamedRange> controle é um intervalo que tem um nome exclusivo, expõe eventos e pode ser associado a dados. Para obter mais informações, consulte [visão geral do modelo de objeto do Excel](../vsto/excel-object-model-overview.md).  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="creating-the-control"></a>Criando o controle  
 Você pode adicionar <xref:Microsoft.Office.Tools.Excel.NamedRange> controles a uma planilha do Excel do Microsoft Office em tempo de design ou em tempo de execução no nível de documento.  
  
 Você pode adicionar <xref:Microsoft.Office.Tools.Excel.NamedRange> controles a uma planilha em tempo de execução em um suplemento do VSTO. Para obter mais informações, consulte [como: adicionar controles NamedRange a planilhas](../vsto/how-to-add-namedrange-controls-to-worksheets.md).  
  
> [!NOTE]  
>  Por padrão, criados dinamicamente intervalos nomeados não são mantidos na planilha de forma que os controles de host quando a planilha está fechada. Para obter mais informações, consulte [adicionando controles a documentos do Office em tempo de execução](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
 <xref:Microsoft.Office.Tools.Excel.NamedRange>controles podem consistir apenas de intervalos de planilhas específicas. <xref:Microsoft.Office.Tools.Excel.NamedRange>controles não podem ter nomes relativos que se aplicam a todas as planilhas, e eles não podem consistir em intervalos que abrangem duas ou mais planilhas em uma pasta de trabalho (intervalos 3D).  
  
## <a name="binding-data-to-the-control"></a>Associação de dados ao controle  
 Um intervalo nomeado parece ser uma boa candidata para associação de dados complexos, pois ele pode ter várias células; No entanto, um intervalo é simplesmente uma coleção de células que não pode ser facilmente mapeada para uma determinada coluna de um conjunto de dados. Portanto, <xref:Microsoft.Office.Tools.Excel.NamedRange> controles oferecem suporte apenas a associação de dados simples. O <xref:Microsoft.Office.Tools.Excel.ListObject> controle pode ser usado para associação de dados complexos. Para obter mais informações, consulte [controle ListObject](../vsto/listobject-control.md).  
  
 O <xref:Microsoft.Office.Tools.Excel.NamedRange> controle pode ser vinculado a uma fonte de dados usando o <xref:System.Windows.Forms.Control.DataBindings%2A> propriedades. A propriedade de associação de dados padrão da <xref:Microsoft.Office.Tools.Excel.NamedRange> controle é <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A>.  
  
 Se os dados no conjunto de dados associado são atualizados por meio de qualquer mecanismo de <xref:Microsoft.Office.Tools.Excel.NamedRange> controle reflete as alterações.  
  
## <a name="formatting"></a>Formatação  
 Formatação que pode ser aplicado a um <xref:Microsoft.Office.Interop.Excel.Range> pode ser aplicado a um <xref:Microsoft.Office.Tools.Excel.NamedRange> controle. Isso inclui as bordas, fontes, formato de número e estilos.  
  
## <a name="renaming-the-control"></a>Renomear o controle  
 Quando você adiciona um <xref:Microsoft.Office.Tools.Excel.NamedRange> controle à sua planilha do **caixa de ferramentas**, Visual Studio gera automaticamente um nome para o controle. Você pode alterar o nome no **propriedades** janela.  
  
## <a name="events"></a>Eventos  
 Os seguintes eventos estão disponíveis para o <xref:Microsoft.Office.Tools.Excel.NamedRange> controle:  
  
-   <xref:Microsoft.Office.Tools.Excel.NamedRange.BeforeDoubleClick>  
  
-   <xref:Microsoft.Office.Tools.Excel.NamedRange.BeforeRightClick>  
  
-   <xref:Microsoft.Office.Tools.Excel.NamedRange.BindingContextChanged>  
  
-   <xref:Microsoft.Office.Tools.Excel.NamedRange.Change>  
  
-   <xref:Microsoft.Office.Tools.Excel.NamedRange.Deselected>  
  
-   <xref:System.ComponentModel.Component.Disposed>  
  
-   <xref:Microsoft.Office.Tools.Excel.NamedRange.Selected>  
  
-   <xref:Microsoft.Office.Tools.Excel.NamedRange.SelectionChange>  
  
## <a name="see-also"></a>Consulte também  
 [Automatizando o Excel usando objetos estendidos](../vsto/automating-excel-by-using-extended-objects.md)   
 [Explicações passo a passo e exemplos de desenvolvimento do office](../vsto/office-development-samples-and-walkthroughs.md)   
 [Associando dados a controles em soluções do Office](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Estendendo documentos do Word e pastas de trabalho do Excel em suplementos do VSTO em tempo de execução](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Controles em documentos do Office](../vsto/controls-on-office-documents.md)   
 [Adicionando controles a documentos do Office em tempo de execução](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Como: adicionar controles NamedRange a planilhas](../vsto/how-to-add-namedrange-controls-to-worksheets.md)   
 [Como: redimensionar controles NamedRange](../vsto/how-to-resize-namedrange-controls.md)   
 [Associando dados a controles em soluções do Office](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Passo a passo: Programando em eventos de um controle NamedRange](../vsto/walkthrough-programming-against-events-of-a-namedrange-control.md)   
 [Limitações programáticas de itens de Host e Controles de Host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  