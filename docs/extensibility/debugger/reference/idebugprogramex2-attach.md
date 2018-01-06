---
title: IDebugProgramEx2::Attach | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProgramEx2::Attach
helpviewer_keywords: IDebugProgramEx2::Attach
ms.assetid: 33b22b2f-431e-4205-9441-d28a9c928c97
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 440a4ce6b008efe541187d1d99d886f4c7c5f9ab
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="idebugprogramex2attach"></a>IDebugProgramEx2::Attach
Anexe uma sessão em um programa.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT Attach(   
   IDebugEventCallback2* pCallback,  
   DWORD                 dwReason,  
   IDebugSession2*       pSession  
);  
```  
  
```  
[C#]  
int Attach(   
   IDebugEventCallback2 pCallback,  
   uint                 dwReason,  
   IDebugSession2       pSession  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pCallback`  
 [in] Um [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) objeto que representa a função de retorno de chamada que o mecanismo de depuração anexado envia eventos para.  
  
 `dwReason`  
 [in] Um valor da [ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md) enumeração que descreve o motivo para a operação de anexação.  
  
 `pSession`  
 [in] Um valor que identifica exclusivamente a sessão que está anexando ao programa.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retorna `S_OK`; caso contrário, retorna um código de erro. Esse método deve retornar `E_ATTACH_DEBUGGER_ALREADY_ATTACHED` se o programa já está anexado.  
  
## <a name="remarks"></a>Comentários  
 A porta que contém o programa pode usar o valor em `pSession` para determinar qual sessão está tentando a conexão para o programa. Por exemplo, se uma porta permite que a sessão de depuração somente uma anexar a um processo por vez, a porta pode determinar se a mesma sessão já está anexada a outros programas no processo.  
  
> [!NOTE]
>  A interface passado `pSession` deve ser tratada apenas como um cookie, um valor que identifica exclusivamente o Gerenciador de sessão de depuração anexar a este programa; nenhum dos métodos na interface fornecido estão funcionando.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugProgramEx2](../../../extensibility/debugger/reference/idebugprogramex2.md)