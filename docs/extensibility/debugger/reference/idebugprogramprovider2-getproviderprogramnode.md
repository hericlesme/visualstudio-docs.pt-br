---
title: IDebugProgramProvider2::GetProviderProgramNode | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugProgramProvider2::GetProviderProgramNode
helpviewer_keywords:
- IDebugProgramProvider2::GetProviderProgramNode
ms.assetid: e62e8e83-acbb-4c52-aedf-ffbd4670db29
caps.latest.revision: 13
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 150b2bc744329078319a3bf5d36dc0a97201c0c4
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="idebugprogramprovider2getproviderprogramnode"></a>IDebugProgramProvider2::GetProviderProgramNode
Recupera o nó de programa para um programa específico.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetProviderProgramNode(  
   PROVIDER_FLAGS       Flags,  
   IDebugDefaultPort2*  pPort,  
   AD_PROCESS_ID        processId,  
   REFGUID              guidEngine,  
   UINT64               programId,  
   IDebugProgramNode2** ppProgramNode  
);  
```  
  
```csharp  
int GetProviderProgramNode(  
   enum_PROVIDER_FLAGS    Flags,  
   IDebugDefaultPort2     pPort,  
   AD_PROCESS_ID          ProcessId,  
   ref Guid               guidEngine,  
   ulong                  programId,  
   out IDebugProgramNode2 ppProgramNode  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `Flags`  
 [in] Uma combinação de sinalizadores do [PROVIDER_FLAGS](../../../extensibility/debugger/reference/provider-flags.md) enumeração. Os seguintes sinalizadores são típicos para esta chamada:  
  
|Sinalizador|Descrição|  
|----------|-----------------|  
|`PFLAG_REMOTE_PORT`|Chamador está em execução no computador remoto.|  
|`PFLAG_DEBUGGEE`|No momento está sendo depurado chamador (informações adicionais sobre o empacotamento serão retornadas para cada nó).|  
|`PFLAG_ATTACHED_TO_DEBUGGEE`|Chamador foi anexado ao, mas não iniciado pelo depurador.|  
  
 `pPort`  
 [in] A porta que o processo de chamada está em execução.  
  
 `processId`  
 [in] Um [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) estrutura que contém a ID do processo que contém o programa em questão.  
  
 `guidEngine`  
 [in] GUID do mecanismo de depuração que o programa está anexado a (se houver).  
  
 `programId`  
 [in] ID do programa para o qual obter o nó de programa.  
  
 `ppProgramNode`  
 [out] Um [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) objeto que representa o nó de programa solicitado.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retorna `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)   
 [PROVIDER_FLAGS](../../../extensibility/debugger/reference/provider-flags.md)   
 [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)   
 [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)