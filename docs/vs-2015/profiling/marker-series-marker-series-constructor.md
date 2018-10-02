---
title: Construtor marker_series::marker_series | Microsoft Docs
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
- cvmarkersobj/Concurrency::diagnostic::marker_series::marker_series
helpviewer_keywords:
- Concurrency::diagnostic::marker_series constructor
ms.assetid: 042c7d23-f1d8-4e09-9e76-a21c30243790
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2aafa01d18255e5ea36aed0451a0bb041b5db1f2
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47467830"
---
# <a name="markerseriesmarkerseries-constructor"></a>Construtor marker_series::marker_series
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [marker_series:: marker_series construtor](https://docs.microsoft.com/visualstudio/profiling/marker-series-marker-series-constructor).  
  
Inicializa uma nova instância da classe `marker_series`.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
marker_series();  
marker_series(  
   _In_ LPCTSTR _SeriesName  
);  
marker_series(  
   _In_ const GUID* _ProviderGuid  
);  
marker_series(  
   _In_ const GUID* _ProviderGuid,  
   _In_ LPCTSTR _SeriesName  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `_SeriesName`  
 O nome da série a ser criada.  
  
 `_ProviderGuid`  
 O GUID do provedor da série.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** cvmarkersobj.h  
  
 **Namespace:** Concurrency::diagnostic  
  
## <a name="see-also"></a>Consulte também  
 [Classe marker_series](../profiling/marker-series-class.md)



