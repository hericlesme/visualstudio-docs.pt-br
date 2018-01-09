---
title: "Como visualizar uma associação de coleção (Designer de Classe) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.classdesigner.collectionassociationline
- vs.classdesigner.ShowAssociationException
helpviewer_keywords:
- collection associations
- collections, collection associations
- Class Designer [Visual Studio], collection associations
ms.assetid: 54e39838-2fc9-4dc2-85b6-7e88a743108e
caps.latest.revision: "6"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 234c70896b28f27815b7563b814fb6b4bd933ebd
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-visualize-a-collection-association-class-designer"></a>Como visualizar uma associação de coleção (Designer de Classe)
Propriedades e campos que são coleções de outros tipos podem ser exibidos no diagrama de classe como uma associação de coleção. Diferentemente de uma associação regular, que exibe um campo ou uma propriedade como uma linha que vincula a classe proprietária ao tipo do campo, uma associação de coleção é exibida como uma linha que vincula a classe proprietária ao tipo coletado.  
  
### <a name="to-create-a-collection-association"></a>Para criar uma associação de coleção  
  
1.  No código, crie uma propriedade ou campo cujo tipo seja uma coleção fortemente tipada.  
  
2.  No diagrama de classe, expanda a classe de modo que os campos e as propriedades sejam mostrados.  
  
3.  Na classe, clique com o botão direito do mouse no campo ou propriedade e escolha **Mostrar como Associação de Coleção**.  
  
     A propriedade ou o campo é mostrado como uma linha de associação vinculando ao tipo coletado.  
  
## <a name="see-also"></a>Consulte também
[Como criar associações entre tipos](how-to-create-associations-between-types.md)   
[Projetando classes e tipos](designing-classes-and-types.md)   
[Exibindo tipos e relações](viewing-types-and-relationships.md)