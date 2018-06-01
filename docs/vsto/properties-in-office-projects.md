---
title: Propriedades em projetos do Office
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Trust Assemblies Location property
- Cache in Document property
- properties [Office development in Visual Studio]
- Namespace for Host Item property
- Office projects [Office development in Visual Studio], properties
- projects [Office development in Visual Studio], properties
- Value2 property
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 2b5c5e0719f7b619fa00a3a0f4333ae0080c0715
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/01/2018
ms.locfileid: "34692766"
---
# <a name="properties-in-office-projects"></a>Propriedades em projetos do Office
  Há várias propriedades importantes que estão disponíveis para projetos do Office no Visual Studio. Essas propriedades podem ser acessadas de **propriedades** janela.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## <a name="namespace-for-host-item"></a>Namespace para item de host  
 Use o **Namespace para Item de Host** propriedade para alterar o namespace para classes de item de host (por exemplo, o `ThisAddIn`, `ThisWorkbook`, ou `ThisDocument` classes) em projetos Visual c#. Esta propriedade aparece no **propriedades** janela quando você seleciona o nó de documento em um projeto no nível de documento (como *ExcelWorkbook1.xlsx* ou *WordDocument1.docx* ) ou o nó de aplicativo em um projeto do suplemento do VSTO (como o Excel ou Word) em **Gerenciador de soluções**.  
  
 Quando você cria um projeto do Visual c# Office, itens de host recebem um namespace com base no nome do projeto. É recomendável que você use o **Namespace para Item de Host** arquivos de propriedade para alterar o namespace em vez de editar o código diretamente. Quando você usar essa propriedade, o namespace é alterado nos arquivos de código (oculto) gerado, bem como nos arquivos de código visível.  
  
## <a name="cacheindocument"></a>CacheInDocument  
 O **CacheInDocument** propriedade aparece no **propriedades** janela para projetos de nível de documento, quando você seleciona uma instância de um <xref:System.Data.DataSet> no designer do Visual Studio. Somente membros públicos podem ser armazenados em cache; Certifique-se de que o **modificadores** está definida como **pública** se você desejar armazenar em cache um <xref:System.Data.DataSet>.  
  
 Essa propriedade tem um valor booliano:  
  
-   Selecione **true** para armazenar em cache o conjunto de dados no documento.  
  
-   Selecione **false** se você não quiser que o conjunto de dados a ser armazenado em cache no documento.  
  
 Para obter mais informações sobre o cache de dados, consulte [armazenado em cache dados em personalizações no nível do documento](../vsto/cached-data-in-document-level-customizations.md).  
  
## <a name="value2"></a>Value2  
 O **Value2** propriedade só está disponível para projetos de modelo ou pasta de trabalho do Excel. Aparece sob o **Databindings** nó de propriedade no **propriedades** janela quando você seleciona um <xref:Microsoft.Office.Tools.Excel.NamedRange> controle no designer de planilha.  
  
 Use o **Value2** propriedade no **propriedades** window para vincular o <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> propriedade do <xref:Microsoft.Office.Tools.Excel.NamedRange> para um campo na fonte de dados.  
  
## <a name="see-also"></a>Consulte também  
 [Projetar e criar soluções do Office](../vsto/designing-and-creating-office-solutions.md)   
 [Visão geral de modelos de projeto do Office](../vsto/office-project-templates-overview.md)   
 [Eventos em projetos do Office](../vsto/events-in-office-projects.md)  
  
  