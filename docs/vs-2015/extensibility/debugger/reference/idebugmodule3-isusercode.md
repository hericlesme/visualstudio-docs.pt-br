---
title: IDebugModule3::IsUserCode | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugModule3::IsUserCode
helpviewer_keywords:
- IDebugModule3::IsUserCode
ms.assetid: 77022946-bb8b-4114-aa81-614df6e54b13
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f6e633006cd41cfd88c85d8213498786c13fad9b
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47466315"
---
# <a name="idebugmodule3isusercode"></a>IDebugModule3::IsUserCode
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [IDebugModule3::IsUserCode](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugmodule3-isusercode).  
  
Recupera informações sobre se o módulo representa o código do usuário ou não.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT IsUserCode(  
   BOOL* pfUser  
);  
```  
  
```csharp  
int IsUserCode(  
   out int pfUser  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pfUser`  
 [out] Diferente de zero (`TRUE`) se o módulo representa o código do usuário, zero (`FALSE`) se não existir.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retornará o código de erro.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)

