---
title: Diretiva CleanUpBehavior T4 | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9e5a211f-a3bf-4229-bff0-7d2e45b71c64
caps.latest.revision: 4
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 9b9138ab564c7597715537216333f1efd0f3fc5a
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47466717"
---
# <a name="t4-cleanupbehavior-directive"></a>Diretiva CleanUpBehavior T4
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [diretiva CleanUpBehavior T4](https://docs.microsoft.com/visualstudio/modeling/t4-cleanupbehavior-directive).  
  
Para excluir o appDomain depois de processar um modelo de texto, inclua a seguinte linha:  
  
```  
<#@ CleanupBehavior processor="T4VSHost" CleanupAfterProcessingtemplate="true" #>  
```  
  
 Os modelos de texto são processados em um appDomain que é separado do processo do host. Na maioria dos casos, quando um modelo de texto é processado, o appdomain é usado novamente para processar o próximo modelo. Mas se você especificar CleanupBehavior, o appDomain será excluído e o próximo modelo será processado em um novo appDomain.  
  
 Isso reduz o processamento de texto, mas pode ser útil para garantir que os recursos sejam descartados.  
  
 Essa diretiva só funciona no host do Visual Studio.



