---
title: Enumeração de marker_importance | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- cvmarkersobj/Concurrency::diagnostic::marker_importance
helpviewer_keywords:
- Concurrency::diagnostic::marker_importance enumeration
ms.assetid: d5524ea0-0227-4d8e-9122-332291042df5
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1564de8b63efa48ad83b1aa09f1fce75ff3fbd75
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47474013"
---
# <a name="markerimportance-enumeration"></a>Enumeração marker_importance
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [enumeração marker_importance](https://docs.microsoft.com/visualstudio/profiling/marker-importance-enumeration).  
  
Representa o nível de importância de um marcador da Visualização Simultânea.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
enum marker_importance;  
```  
  
## <a name="members"></a>Membros  
  
### <a name="values"></a>Valores  
  
|Nome|Descrição|  
|----------|-----------------|  
|`critical_importance`|Especifica que o marcador tem importância crítica.|  
|`high_importance`|Especifica que o marcador tem alta importância.|  
|`low_importance`|Especifica que o marcador tem baixa importância.|  
|`normal_importance`|Especifica que o marcador tem importância normal.|  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** cvmarkersobj.h  
  
 **Namespace:** Concurrency::diagnostic  
  
## <a name="see-also"></a>Consulte também  
 [Namespace de diagnóstico](../profiling/diagnostic-namespace.md)



