---
title: SuspendTracking | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
apiname: SuspendTracking
apilocation: filetracker.dll
apitype: COM
helpviewer_keywords: SuspendTracking
ms.assetid: f5e06e5a-8083-444c-99c1-07ba834226b5
caps.latest.revision: "3"
author: kempb
ms.author: kempb
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 34aa890b8aaa4f1b4dd1f61dc79091ed81eb428c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="suspendtracking"></a>SuspendTracking
Suspende o acompanhamento no contexto atual.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp 
HRESULT WINAPI SuspendTracking(void);  
```  
  
## <a name="return-value"></a>Valor retornado  
 Um **HRESULT** com o conjunto de bits **SUCCEEDED** se o acompanhamento tiver sido suspenso.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** FileTracker.h  
  
## <a name="see-also"></a>Consulte também  
 [ResumeTracking](../msbuild/resumetracking.md)