---
title: IDebugProcess2::Attach | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProcess2::Attach
helpviewer_keywords: IDebugProcess2::Attach
ms.assetid: 40d78417-fde2-45c3-96c9-16e06bd9008d
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 840f2dee6648a84b0f7c6259049dcc701b5aef82
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="idebugprocess2attach"></a>IDebugProcess2::Attach
Anexa o Gerenciador de sessão de depuração (SDM) para o processo.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT Attach(   
   IDebugEventCallback2* pCallback,  
   GUID*                 rgguidSpecificEngines,  
   DWORD                 celtSpecificEngines,  
   HRESULT*              rghrEngineAttach  
);  
```  
  
```csharp  
int Attach(   
   IDebugEventCallback2 pCallback,  
   Guid[]               rgguidSpecificEngines,  
   uint                 celtSpecificEngines,  
   int[]                rghrEngineAttach  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pCallback`  
 [in] Um [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) objeto que é usado para notificação de eventos de depuração.  
  
 `rgguidSpecificEngines`  
 [in] Uma matriz de GUIDs de mecanismos de depuração a ser usado para depurar programas em execução no processo. Esse parâmetro pode ser um valor nulo. Consulte comentários para obter detalhes.  
  
 `celtSpecificEngines`  
 [in] O número de depuração mecanismos no `rgguidSpecificEngines` matriz e o tamanho do `rghrEngineAttach` matriz.  
  
 `rghrEngineAttach`  
 [out no] Uma matriz de códigos HRESULT retornado por mecanismos de depuração. O tamanho dessa matriz é especificado no `celtSpecificEngines` parâmetro. Cada código é normalmente `S_OK` ou `S_ATTACH_DEFERRED`. O segundo indica que o DE está atualmente anexado ao nenhum programa.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retorna `S_OK`; caso contrário, retorna um código de erro. A tabela a seguir mostra os outros valores possíveis.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`E_ATTACH_DEBUGGER_ALREADY_ATTACHED`|O processo especificado já está anexado ao depurador.|  
|`E_ATTACH_DEBUGGEE_PROCESS_SECURITY_VIOLATION`|Ocorreu uma violação de segurança durante o procedimento de anexação.|  
|`E_ATTACH_CANNOT_ATTACH_TO_DESKTOP`|Um processo de área de trabalho não é possível anexar o depurador.|  
  
## <a name="remarks"></a>Comentários  
 Anexar a um processo anexa o SDM para todos os programas em execução no processo que pode ser depurado por mecanismos de depuração (DE) especificados no `rgguidSpecificEngines` matriz. Definir o `rgguidSpecificEngines` parâmetro para um valor nulo de valor ou incluir `GUID_NULL` na matriz para anexar a todos os programas no processo.  
  
 Todos os eventos de depuração que ocorrem no processo são enviados para o determinado [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) objeto. Isso `IDebugEventCallback2` objeto é fornecido quando o SDM chama esse método.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)