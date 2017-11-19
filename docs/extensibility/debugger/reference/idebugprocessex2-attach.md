---
title: IDebugProcessEx2::Attach | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProcessEx2::Attach
helpviewer_keywords: IDebugProcessEx2::Attach method
ms.assetid: f3334ed7-39bf-4d02-a338-36f567b9b287
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 111895b73ee9685b9608be9812452d04d84cd48c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="idebugprocessex2attach"></a>IDebugProcessEx2::Attach
Esse método informa o processo que uma sessão agora está depurando o processo.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT Attach(   
   IDebugSession2* pSession  
);  
```  
  
```csharp  
int Attach(  
   IDebugSession2 pSession  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pSession`  
 [in] Um valor que identifica exclusivamente a sessão anexar a esse processo.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retorna `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 A interface passado `pSession` deve ser tratada apenas como um cookie, um valor que identifica exclusivamente o Gerenciador de sessão de depuração anexar a esse processo; nenhum dos métodos na interface fornecido estão funcionando.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugProcessEx2](../../../extensibility/debugger/reference/idebugprocessex2.md)