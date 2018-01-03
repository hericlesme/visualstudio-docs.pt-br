---
title: "Função CvReleaseMarkerSeries | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: cvmarkers/CvReleaseMarkerSeries
helpviewer_keywords: CvReleaseMarkerSeries method
ms.assetid: 3b4711ee-e534-411d-9128-f69cd7932a48
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 3251db736e42d0b5e49d92b17720605c507d2184
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="cvreleasemarkerseries-function"></a>Função CvReleaseMarkerSeries
Libera a série de marcador. Não use um objeto de série de marcador após a liberação; caso contrário, o aplicativo poderá falhar. A falha ao liberar a série de marcador causa uma perda de memória.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT CvReleaseMarkerSeries(  
   _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pMarkerSeries`  
 Endereço da variável de objeto do provedor. O endereço não pode ser NULL; a variável pode ter qualquer valor.  
  
## <a name="return-value"></a>Valor retornado  
 S_OK quando a série de marcador é liberada com êxito ou código de erro no caso de erros. Use as macros SUCCEEDED/FAILED para verificar a condição de erro.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** cvmarkers.h  
  
## <a name="see-also"></a>Consulte também  
 [Referência de biblioteca C++](../profiling/cpp-library-reference.md)