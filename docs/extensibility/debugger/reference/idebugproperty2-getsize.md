---
title: IDebugProperty2::GetSize | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProperty2::GetSize
helpviewer_keywords: IDebugProperty2::GetSize
ms.assetid: 0deb8ec5-d6fb-4622-bb14-0c46b9459cc6
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 94b38051d8a605bb92e8ac8cdabb463a7daf7431
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="idebugproperty2getsize"></a>IDebugProperty2::GetSize
Obtém o tamanho, em bytes, do valor da propriedade.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetSize (   
   DWORD* pdwSize  
);  
```  
  
```csharp  
int GetSize (   
   out uint pdwSize  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pdwSize`  
 [out] Retorna o tamanho, em bytes, do valor da propriedade.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retorna `S_OK`; caso contrário, retorna o código de erro. Retorna `S_GETSIZE_NO_SIZE` se a propriedade não tem nenhum tamanho.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)