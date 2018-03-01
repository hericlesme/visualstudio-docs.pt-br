---
title: Classe marker_series | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- cvmarkersobj/Concurrency::diagnostic::marker_series
helpviewer_keywords:
- Concurrency::diagnostic::marker_series class
ms.assetid: b8445ed0-c512-4f92-b6b4-3d05c044f939
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 9bb2cbe0a87e61a50f3f2b071aef9ef9e12663a0
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="markerseries-class"></a>Classe marker_series
Representa um canal serial de eventos gerados por um único provedor.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
class marker_series;  
```  
  
## <a name="members"></a>Membros  
  
### <a name="public-constructors"></a>Construtores públicos  
  
|Nome|Descrição|  
|----------|-----------------|  
|[marker_series::Construtor de marker_series](../profiling/marker-series-marker-series-constructor.md)|Inicializa uma nova instância da classe `marker_series`.|  
|[marker_series::Destruidor ~marker_series](../profiling/marker-series-tilde-marker-series-destructor.md)|Destrói o objeto marker_series e libera todos os recursos alocados.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nome|Descrição|  
|----------|-----------------|  
|[marker_series::is_enabled Method](../profiling/marker-series-is-enabled-method.md)|Determina se alguma sessão habilitou o provedor.|  
|[marker_series::write_alert Method](../profiling/marker-series-write-alert-method.md)|Grava um alerta para o arquivo de rastreamento da Visualização Simultânea.|  
|[marker_series::write_flag Method](../profiling/marker-series-write-flag-method.md)|Grava um sinalizador para o arquivo de rastreamento da Visualização Simultânea.|  
|[marker_series::write_message Method](../profiling/marker-series-write-message-method.md)|Grava uma mensagem para o arquivo de rastreamento da Visualização Simultânea.|  
  
## <a name="inheritance-hierarchy"></a>Hierarquia de herança  
 `marker_series`  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** cvmarkersobj.h  
  
 **Namespace:** Concurrency::diagnostic  
  
## <a name="see-also"></a>Consulte também  
 [Namespace de diagnóstico](../profiling/diagnostic-namespace.md)