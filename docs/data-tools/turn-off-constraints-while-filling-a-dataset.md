---
title: "Desativar restrições ao preencher um conjunto de dados | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- DataRow.BeginEdit
- DataRow.EndEdit
- DataRow.CancelEdit
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- updating datasets, constraints
- constraints [Visual Basic], datasets
- datasets [Visual Basic], constraints
- constraints [Visual Basic], suspending during dataset update
ms.assetid: 553f7d0c-2faa-4c17-b226-dd02855bf1dc
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.workload: data-storage
ms.openlocfilehash: 88c8687511dd600802cc7c6ecdc12f0827fd7f6f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="turn-off-constraints-while-filling-a-dataset"></a>Desativar restrições ao preencher um conjunto de dados
Se um conjunto de dados contiver restrições (como restrições de chave estrangeira), eles podem gerar erros relacionados à ordem de operações que são executadas no conjunto de dados. Por exemplo, o carregamento de registros filho antes de carregar relacionado registros pai podem violar uma restrição e causar um erro. Assim que você carregue um registro filho, a restrição verifica o registro pai relacionado e gera um erro.  
  
 Se não houver nenhum mecanismo para permitir a suspensão de restrição temporária, um erro será gerado sempre que você tentou carregar um registro na tabela filho. Outra maneira de suspender todas as restrições em um conjunto de dados é com o <xref:System.Data.DataRow.BeginEdit%2A>, e <xref:System.Data.DataRow.EndEdit%2A> propriedades.  
  
> [!NOTE]
>  Eventos de validação (por exemplo, <xref:System.Data.DataTable.ColumnChanging> e<xref:System.Data.DataTable.RowChanging>) não serão gerados quando restrições estão desativadas.  
  
### <a name="to-suspend-update-constraints-programmatically"></a>Para suspender restrições de atualização programaticamente  
  
-   O exemplo a seguir mostra como desativar temporariamente a restrição de verificação em um conjunto de dados:  
  
     [!code-csharp[VbRaddataEditing#10](../data-tools/codesnippet/CSharp/turn-off-constraints-while-filling-a-dataset_1.cs)]
     [!code-vb[VbRaddataEditing#10](../data-tools/codesnippet/VisualBasic/turn-off-constraints-while-filling-a-dataset_1.vb)]  
  
### <a name="to-suspend-update-constraints-using-the-dataset-designer"></a>Para suspender restrições de atualização usando o Designer de conjunto de dados  
  
1.  Abra o conjunto de dados de **Dataset Designer**. Para obter mais informações, consulte [passo a passo: Criando um conjunto de dados no Designer de conjunto de dados](walkthrough-creating-a-dataset-with-the-dataset-designer.md).  
  
2.  No **propriedades** janela, defina o <xref:System.Data.DataSet.EnforceConstraints%2A> propriedade `false`.  
  
## <a name="see-also"></a>Consulte também  
 [Preencher conjuntos de dados usando TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md)   
 [Relacionamentos em conjuntos de dados](../data-tools/relationships-in-datasets.md)