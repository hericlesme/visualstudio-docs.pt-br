---
title: IDebugProcess2::GetName | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProcess2::GetName
helpviewer_keywords: IDebugProcess2::GetName
ms.assetid: a2f66ab5-53e5-4cdc-a1b5-3b8afa8ee646
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7d8382cf5e356725f5ca50348d422290b4363c35
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="idebugprocess2getname"></a>IDebugProcess2::GetName
Obtém o título, o nome amigável ou o nome de arquivo do processo.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetName(   
   GETNAME_TYPE  gnType,  
   BSTR*         pbstrName  
);  
```  
  
```csharp  
int GetName(   
   enum_GETNAME_TYPE  gnType,  
   out string         pbstrName  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `gnType`  
 [in] Um valor da [GETNAME_TYPE](../../../extensibility/debugger/reference/getname-type.md) enumeração que especifica o tipo de nome a ser retornado.  
  
 `pbstrName`  
 [out] Retorna o nome do processo.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retorna `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [GETNAME_TYPE](../../../extensibility/debugger/reference/getname-type.md)