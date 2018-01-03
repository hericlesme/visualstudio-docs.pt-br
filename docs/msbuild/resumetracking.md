---
title: ResumeTracking | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
apiname: ResumeTracking
apilocation: filetracker.dll
apitype: COM
helpviewer_keywords: ResumeTracking
ms.assetid: d637e019-7c50-4b0a-812e-bc822001e697
caps.latest.revision: "4"
author: kempb
ms.author: kempb
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: ae79812a700f8444002ae3b8c04c0ea816970eea
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="resumetracking"></a>ResumeTracking
Retoma o acompanhamento no contexto atual.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT WINAPI ResumeTracking();  
```  
  
## <a name="return-value"></a>Valor retornado  
 Um **HRESULT** com o conjunto de bits **SUCCEEDED** se o acompanhamento tiver sido retomado. **E_FAIL** será retornado se não for possível continuar o acompanhamento porque o contexto não estava disponível.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** FileTracker.h  
  
## <a name="see-also"></a>Consulte também  
 [SuspendTracking](../msbuild/suspendtracking.md)