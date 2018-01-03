---
title: "Função CvIsEnabled | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- cvmarkers/CvIsEnabledEx
- cvmarkers/CvIsEnabled
helpviewer_keywords:
- CvIsEnabled method
- CvIsEnabledEx method
ms.assetid: 2e4fea6d-758d-4150-8744-6102a1d58c1c
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: f7459b155192869f02541d65da9cfaa80f22ddd9
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="cvisenabled-function"></a>Função CvIsEnabled
Determina se uma sessão habilitou o provedor ETW especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT CvIsEnabled(  
   _In_ PCV_PROVIDER pProvider  
);  
HRESULT CvIsEnabledEx(  
   _In_ PCV_PROVIDER pProvider,  
   _In_ CV_IMPORTANCE level,  
   _In_ int category  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `category`  
 Categoria.  
  
 `level`  
 Nível de importância.  
  
 `pProvider`  
 Objeto de provedor válido. Não pode ser NULL.  
  
## <a name="return-value"></a>Valor retornado  
 S_OK se o provedor estiver habilitado no momento. S_FALSE se o provedor estiver desabilitado no momento. Código de erro em caso de erros. Use a macro FAILED para verificar a condição de erro e depois verifique se S_OK/S_FALSE.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** cvmarkers.h  
  
## <a name="see-also"></a>Consulte também  
 [Referência de biblioteca C++](../profiling/cpp-library-reference.md)