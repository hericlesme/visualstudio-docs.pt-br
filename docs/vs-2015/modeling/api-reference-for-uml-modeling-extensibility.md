---
title: Referência da API para extensibilidade de modelagem UML | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- UML - extending
- UML API
- UML model, API
ms.assetid: 2b2ffe93-c358-4d28-a5e5-3d0474629b58
caps.latest.revision: 11
author: alexhomer1
ms.author: gewarren
manager: douge
ms.openlocfilehash: db042d59ce5f7363d9ed45e2baebbea45d3a0de4
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47467229"
---
# <a name="api-reference-for-uml-modeling-extensibility"></a>Referência de API para extensibilidade de modelagem UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [referência de API para extensibilidade de modelagem UML](https://docs.microsoft.com/visualstudio/modeling/api-reference-for-uml-modeling-extensibility).  
  
Você pode escrever o código de programa para ler e modificar os modelos que você cria com o Visual Studio. A referência de API fornece informações sobre as classes específicas para ajudá-lo com isso. Para obter mais informações e orientados a tarefas, consulte os tópicos em [modelos e diagramas UML estender](../modeling/extend-uml-models-and-diagrams.md). Para ver quais versões do Visual Studio dão suporte a modelos UML, consulte [suporte de versão para a arquitetura e ferramentas de modelagem](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
## <a name="assemblies"></a>Assemblies  
  
|Assembly|O que isso permite que você faça|  
|--------------|--------------------------------|  
|VisualStudio|-Ler e alterar os elementos de modelo como IUseCase, IAssociation e assim por diante.<br />-Navegar em relações entre elementos.<br /><br /> Os namespaces e tipos correspondem às que são definidos na especificação de UML.|  
|Microsoft.VisualStudio.ArchitectureTools.Extensibility.dll|-Criar novas instâncias de elementos de modelo<br />-Acessar e modificar formas e diagramas.|  
  
## <a name="see-also"></a>Consulte também  
 [Estender modelos e diagramas UML](../modeling/extend-uml-models-and-diagrams.md)   
 [Referência de API do SDK de Modelagem para Visual Studio](../modeling/api-reference-for-modeling-sdk-for-visual-studio.md)



