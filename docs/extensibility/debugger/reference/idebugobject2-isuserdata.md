---
title: IDebugObject2::IsUserData | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugObject2::IsUserData
helpviewer_keywords: IDebugObject2::IsUserData method
ms.assetid: 6ffa0d0e-f742-496d-acc7-db74c248bc45
caps.latest.revision: "7"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ac758e7e8ce4d288b347b1207883642c920059bb
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="idebugobject2isuserdata"></a>IDebugObject2::IsUserData
Determina se o objeto que representa os dados de usuário.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT IsUserData(  
   BOOL* pfUser  
);  
```  
  
```csharp  
int IsUserData(  
   out int pfUser  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pfUser`  
 [out] Retorna zero (`TRUE`) se o objeto que representa dados de usuário; zero (`FALSE`) se não existir.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará S_OK; Caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Dados de usuário são qualquer objeto que faz parte de um módulo designado como /justmycode (uma opção configurável pelo usuário que marca um módulo de código do usuário e, portanto, visíveis em um rastreamento de pilha).  
  
## <a name="see-also"></a>Consulte também  
 [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)