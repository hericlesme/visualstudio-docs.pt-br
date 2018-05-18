---
title: Enumeração de marker_importance | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- cvmarkersobj/Concurrency::diagnostic::marker_importance
helpviewer_keywords:
- Concurrency::diagnostic::marker_importance enumeration
ms.assetid: d5524ea0-0227-4d8e-9122-332291042df5
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9f4c87cfa1504c997cefdc68416dac9923fa10b4
ms.sourcegitcommit: 046a9adc5fa6d6d05157204f5fd1a291d89760b7
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/11/2018
---
# <a name="markerimportance-enumeration"></a>Enumeração marker_importance
Representa o nível de importância de um marcador da Visualização Simultânea.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
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