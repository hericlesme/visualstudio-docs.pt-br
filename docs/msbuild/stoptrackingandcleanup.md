---
title: StopTrackingAndCleanup | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: conceptual
apiname:
- StopTrackingAndCleanup
apilocation:
- filetracker.dll
apitype: COM
helpviewer_keywords:
- StopTrackingAndCleanup
ms.assetid: 9f8c5994-2dfc-43c3-a5fb-89b2f8990429
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 731e8091a91c49c8e17dbcd00c3aea32001115a0
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/19/2018
ms.locfileid: "31567893"
---
# <a name="stoptrackingandcleanup"></a>StopTrackingAndCleanup
Interrompe o acompanhamento e libera a memória usada pela sessão de acompanhamento.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp 
HRESULT WINAPI StopTrackingAndCleanup(void);  
```  
  
## <a name="return-value"></a>Valor retornado  
 Retorna um **HRESULT** com o conjunto de bits **SUCCEEDED** se o acompanhamento tiver sido interrompido.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** FileTracker.h  
  
## <a name="see-also"></a>Consulte também  
 [StartTrackingContext](../msbuild/starttrackingcontext.md)