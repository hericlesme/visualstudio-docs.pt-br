---
title: 'Como: adicionar uma referência de saída do projeto | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- project output references [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, project output references
- SharePoint development in Visual Studio, advanced packaging tools
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 97bfe044ef89691afdb1a8e845867ce2e177dbb9
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/05/2018
ms.locfileid: "34767956"
---
# <a name="how-to-add-a-project-output-reference"></a>Como: adicionar uma referência de saída do projeto
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
  
  