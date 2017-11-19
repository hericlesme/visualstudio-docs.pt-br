---
title: IDebugCoreServer2::GetMachineUtilities_V7 | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugCoreServer2::GetMachineUtilities_V7
helpviewer_keywords: IDebugCoreServer2::GetMachineUtilities_V7
ms.assetid: 64c1f08f-853b-4498-9810-29791581ef2f
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 301af8eb2e6b317a532fec6dfdd5ac64f62d12a9
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="idebugcoreserver2getmachineutilitiesv7"></a>IDebugCoreServer2::GetMachineUtilities_V7
Esse método obtém os utilitários de máquina para um servidor.  
  
> [!NOTE]
>  Este método está obsoleto: não use ([!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] sempre retorna `E_NOTIMPL` se esse método é chamado). Ele é mantido por razões históricas.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetMachineUtilities_V7(  
   IDebugMDMUtil2_V7** ppUtil  
);  
```  
  
```csharp  
int GetMachineUtilities_V7(  
   out IDebugMDMUtil2_V7 ppUtil  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `ppUtil`  
 [out] Retorna um `IDebugMDMUtil2_V7` interface que representa as informações de utilitários de máquina.  
  
## <a name="return-value"></a>Valor de retorno  
 Sempre retorna `E_NOTIMPL`, indicando que o método não está implementado.  
  
## <a name="remarks"></a>Comentários  
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]sempre retorna `E_NOTIMPL` se esse método for chamado.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)