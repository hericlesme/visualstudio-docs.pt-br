---
title: "Como: adicionar uma referência de saída do projeto | Microsoft Docs"
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
- VB
- CSharp
helpviewer_keywords:
- project output references [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, project output references
- SharePoint development in Visual Studio, advanced packaging tools
ms.assetid: 9d6bc25e-bf0d-4483-a691-2ad7a796fa80
caps.latest.revision: "15"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 7ced5627420f5ac90da2cae1a2930dbd0b973dbc
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-add-a-project-output-reference"></a>Como adicionar itens a uma referência de saída do projeto
  Para implantar assemblies de projeto do SharePoint não (ou arquivos. xap em projetos do Silverlight) para o SharePoint, adicioná-los como uma referência de saída do projeto.  
  
 Esse processo cria uma dependência de compilação de solução entre os dois projetos. Projetos associados com as referências de saída do projeto são compilados antes do projeto do SharePoint é criado e implantado.  
  
### <a name="to-add-a-project-output-reference"></a>Para adicionar uma referência de saída do projeto  
  
1.  Carregar uma solução que contém pelo menos um projeto do SharePoint e um projeto do SharePoint.  
  
2.  Em **Solution Explorer**, escolha um item no nó de projeto do SharePoint.  
  
3.  No **propriedades** janela, escolha o **referências de saída do projeto** propriedade e, em seguida, escolha o botão de reticências (![elipse ASP.NET Mobile Designer](../sharepoint/media/mwellipsis.gif "ASP. Elipse de NET Mobile Designer")) botão ao lado dele.  
  
4.  No **referências de saída do projeto** caixa de diálogo caixa, escolha o **adicionar** botão.  
  
5.  No painel Propriedades, clique na seta ao lado de **tipo de implantação** propriedade e, em seguida, escolha um valor apropriado para o item do SharePoint não estiver referenciando, tais como **ElementFile**.  
  
6.  Clique na seta ao lado de **nome do projeto**, escolha o nome do item de projeto do SharePoint e, em seguida, escolha o **Okey** botão.  
  
## <a name="see-also"></a>Consulte também  
 [Fornecimento de empacotamento e informações de implantação em itens de projeto](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)   
 [Como: marcar controles como controles seguros](../sharepoint/how-to-mark-controls-as-safe-controls.md)   
 [Empacotando e implantando recursos do SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  