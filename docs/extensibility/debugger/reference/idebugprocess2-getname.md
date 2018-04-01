---
title: IDebugProcess2::GetName | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugProcess2::GetName
helpviewer_keywords:
- IDebugProcess2::GetName
ms.assetid: a2f66ab5-53e5-4cdc-a1b5-3b8afa8ee646
caps.latest.revision: 11
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: b6434d8a06e776c31e944eead27a4f83dc04a32b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
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