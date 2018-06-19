---
title: IDebugProgramProvider2::GetProviderProcessData | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProgramProvider2::GetProviderProcessData
helpviewer_keywords:
- IDebugProgramProvider2::GetProviderProcessData
ms.assetid: 90cf7b7f-53d2-487e-b793-94501a6e24dd
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 77a6da58083feb8699c6db24207c265bf50c0f0e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31122464"
---
# <a name="idebugprogramprovider2getproviderprocessdata"></a>IDebugProgramProvider2::GetProviderProcessData
Recupera uma lista de programas em execução de um processo especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetProviderProcessData(  
   PROVIDER_FLAGS         Flags,  
   IDebugDefaultPort2*    pPort,  
   AD_PROCESS_ID          processId,  
   CONST_GUID_ARRAY       EngineFilter,  
   PROVIDER_PROCESS_DATA* pProcess  
);  
```  
  
```csharp  
int GetProviderProcessData(  
   enum_PROVIDER_FLAGS     Flags,  
   IDebugDefaultPort2      pPort,  
   AD_PROCESS_ID           ProcessId,  
   CONST_GUID_ARRAY        EngineFilter,  
   PROVIDER_PROCESS_DATA[] pProcess  
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
|`PFLAG_GET_PROGRAM_NODES`|Chamador está pedindo para obter uma lista de nós de programa a ser retornado.|  
  
 `pPort`  
 [in] A porta que o processo de chamada está em execução.  
  
 `processId`  
 [in] Um [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) estrutura que contém a ID do processo que contém o programa em questão.  
  
 `EngineFilter`  
 [in] Uma matriz de GUIDs para mecanismos de depuração atribuídos para depurar esse processo (esses serão usados para filtrar os programas que são de fato retornados com base no que suportam os mecanismos fornecidos; se nenhum mecanismo forem especificado, em seguida, serão retornados todos os programas).  
  
 `pProcess`  
 [out] Um [PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md) estrutura que é preenchida com as informações solicitadas.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retorna `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Normalmente, esse método é chamado por um processo para obter uma lista de programas em execução no processo. As informações retornadas são uma lista de [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) objetos.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)   
 [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)   
 [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)   
 [CONST_GUID_ARRAY](../../../extensibility/debugger/reference/const-guid-array.md)   
 [PROVIDER_FLAGS](../../../extensibility/debugger/reference/provider-flags.md)   
 [PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)