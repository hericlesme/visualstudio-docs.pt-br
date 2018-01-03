---
title: Namespace diagnostic | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: cvmarkersobj/Concurrency::diagnostic
helpviewer_keywords: Concurrency::diagnostic namespace
ms.assetid: ad786b19-7c4c-46ee-bfb6-c4752b373a09
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 3fb9b831562e2d9e4ce7d686f49ac484d58f6804
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="diagnostic-namespace"></a>Namespace de diagnóstico
O namespace `diagnostics` fornece funcionalidade para emitir marcadores de Visualização Simultânea.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
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