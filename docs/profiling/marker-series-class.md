---
title: Classe marker_series | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- cvmarkersobj/Concurrency::diagnostic::marker_series
helpviewer_keywords:
- Concurrency::diagnostic::marker_series class
ms.assetid: b8445ed0-c512-4f92-b6b4-3d05c044f939
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 075a81dc81bb202be913f5a06e8213a8a68a010f
ms.sourcegitcommit: 046a9adc5fa6d6d05157204f5fd1a291d89760b7
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/11/2018
---
# <a name="markerseries-class"></a>Classe marker_series
Representa um canal serial de eventos gerados por um único provedor.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
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