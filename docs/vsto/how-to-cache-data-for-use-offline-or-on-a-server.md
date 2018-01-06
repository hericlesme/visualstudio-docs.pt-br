---
title: 'Como: dados armazenados em Cache para uso Offline ou em um servidor | Microsoft Docs'
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
- data caching [Office development in Visual Studio], server use
- Office applications [Office development in Visual Studio], data
- datasets [Office development in Visual Studio], caching
- offline data [Office development in Visual Studio]
- data [Office development in Visual Studio], caching
- data caching [Office development in Visual Studio], offline use
ms.assetid: 6246b187-9413-4336-821d-2259b1adec5a
caps.latest.revision: "49"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 07d467d67c78f6779a8be2d21b266f8328e30ff7
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-cache-data-for-use-offline-or-on-a-server"></a>Como armazenar dados em cache para uso offline ou em um servidor
  Você pode marcar um item de dados a ser armazenado em cache no documento, para que ele esteja disponível offline. Isso também possibilita que os dados do documento a ser manipulada por outro código quando o documento é armazenado em um servidor.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Você pode marcar um item de dados a ser armazenado em cache quando o item de dados é declarado em seu código, ou, se você estiver usando um <xref:System.Data.DataSet>, definindo uma propriedade **propriedades** janela. Se você estiver armazenando em cache um item de dados que não é um <xref:System.Data.DataSet> ou <xref:System.Data.DataTable>, certifique-se de que ele atenda aos critérios para sendo armazenado em cache no documento. Para obter mais informações, consulte [Caching Data](../vsto/caching-data.md).  
  
> [!NOTE]  
>  Conjuntos de dados criados usando o Visual Basic que são marcados como **em cache** e **WithEvents** (inclusive conjuntos de dados que são arrastados o **fontes de dados** janela ou **Ferramentas** que têm o **CacheInDocument** propriedade definida como **True**) tenha um sublinhado antecedido pelos seus nomes no cache. Por exemplo, se você criar um conjunto de dados e nomeie-o **clientes**, o <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem> nome será **_Customers** no cache. Quando você usa <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> para acessar este item em cache, você deve especificar **_Customers** em vez de **clientes**.  
  
### <a name="to-cache-data-in-the-document-using-code"></a>Os dados em cache no documento usando código  
  
1.  Declarar um campo ou propriedade pública para o item de dados como um membro de uma classe de item de host no seu projeto, como o `ThisDocumen`classe em um projeto do Word ou o `ThisWorkbook` classe em um projeto do Excel.  
  
2.  Aplicar o <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> de atributo para o membro para marcar o item de dados a ser armazenado em cache de dados do documento. O exemplo a seguir se aplica a este atributo a uma declaração de campo para um <xref:System.Data.DataSet>.  
  
     [!code-csharp[Trin_VstcoreDataExcel#11](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#11)]
     [!code-vb[Trin_VstcoreDataExcel#11](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#11)]  
  
3.  Adicione código para criar uma instância do item de dados e, se aplicável, carregá-lo do banco de dados.  
  
     O item de dados é carregado apenas quando ele é criado; Depois disso, o cache permanece com o documento e você deve escrever outro código para atualizá-lo.  
  
### <a name="to-cache-a-dataset-in-the-document-by-using-the-properties-window"></a>Para armazenar em cache um conjunto de dados no documento usando a janela Propriedades  
  
1.  Adicionar o conjunto de dados ao projeto usando ferramentas no designer do Visual Studio, por exemplo, adicionando uma fonte de dados ao seu projeto usando o **fontes de dados** janela.  
  
2.  Crie uma instância do conjunto de dados se você tiver um e selecione a instância no designer.  
  
3.  No **propriedades** janela, defina o **CacheInDocument** propriedade **True**.  
  
     Para obter mais informações, consulte [propriedades em projetos do Office](../vsto/properties-in-office-projects.md).  
  
4.  No **propriedades** janela, defina o **modificadores** propriedade **pública** (por padrão, ele é **interno**).  
  
## <a name="see-also"></a>Consulte também  
 [Cache de dados](../vsto/caching-data.md)   
 [Como: Cache programaticamente uma fonte de dados em um documento do Office](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md)   
 [Como: armazenar em Cache dados em um documento protegido por senha](../vsto/how-to-cache-data-in-a-password-protected-document.md)   
 [Acessando dados em documentos no servidor](../vsto/accessing-data-in-documents-on-the-server.md)   
 [Salvando dados](/visualstudio/data-tools/saving-data)  
  
  