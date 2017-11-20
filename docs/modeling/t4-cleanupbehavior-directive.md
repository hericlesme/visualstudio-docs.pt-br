---
title: Diretiva CleanUpBehavior T4 | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9e5a211f-a3bf-4229-bff0-7d2e45b71c64
caps.latest.revision: "2"
author: alancameronwills
ms.author: awills
manager: douge
ms.openlocfilehash: f60151ba4563c07cd9f6f6619982d8e6a8657ead
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="t4-cleanupbehavior-directive"></a>Diretiva CleanUpBehavior T4
Para excluir o appDomain depois de processar um modelo de texto, inclua a seguinte linha:  
  
```  
<#@ CleanupBehavior processor="T4VSHost" CleanupAfterProcessingtemplate="true" #>  
```  
  
 Os modelos de texto são processados em um appDomain que é separado do processo do host. Na maioria dos casos, quando um modelo de texto é processado, o appdomain é usado novamente para processar o próximo modelo. Mas se você especificar CleanupBehavior, o appDomain será excluído e o próximo modelo será processado em um novo appDomain.  
  
 Isso reduz o processamento de texto, mas pode ser útil para garantir que os recursos sejam descartados.  
  
 Essa diretiva só funciona no host do Visual Studio.