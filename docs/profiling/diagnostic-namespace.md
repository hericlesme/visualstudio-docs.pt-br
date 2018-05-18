---
title: Namespace diagnostic | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- cvmarkersobj/Concurrency::diagnostic
helpviewer_keywords:
- Concurrency::diagnostic namespace
ms.assetid: ad786b19-7c4c-46ee-bfb6-c4752b373a09
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3c3e6909bcb7299f4fd6d725334c26d2b59e0edb
ms.sourcegitcommit: 046a9adc5fa6d6d05157204f5fd1a291d89760b7
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/11/2018
---
# <a name="diagnostic-namespace"></a>Namespace de diagnóstico
O namespace `diagnostics` fornece funcionalidade para emitir marcadores de Visualização Simultânea.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
namespace diagnostic;  
```  
  
## <a name="members"></a>Membros  
  
### <a name="classes"></a>Classes  
  
|Nome|Descrição|  
|----------|-----------------|  
|[Classe marker_series](../profiling/marker-series-class.md)|Representa um canal serial de eventos gerados por um único provedor.|  
|[Classe span](../profiling/span-class.md)|Define uma fase do aplicativo.|  
  
### <a name="enumerations"></a>Enumerações  
  
|Nome|Descrição|  
|----------|-----------------|  
|[Enumeração marker_importance](../profiling/marker-importance-enumeration.md)|Representa o nível de importância de um marcador da Visualização Simultânea.|  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** cvmarkersobj.h  
  
 **Namespace:** Simultaneidade  
  
## <a name="see-also"></a>Consulte também  
 [Namespace de simultaneidade (Visualização Simultânea)](../profiling/concurrency-namespace-concurrency-visualizer.md)