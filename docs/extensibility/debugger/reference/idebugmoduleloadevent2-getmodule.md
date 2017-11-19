---
title: IDebugModuleLoadEvent2::GetModule | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugModuleLoadEvent2::GetModule
helpviewer_keywords: IDebugModuleLoadEvent2::GetModule
ms.assetid: c86482bb-9ce5-4e63-bbe0-969b50169424
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e4bd5ebf74bb3818aff06e01b7c6d181760510f9
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="idebugmoduleloadevent2getmodule"></a>IDebugModuleLoadEvent2::GetModule
Obtém o módulo que está sendo carregado e descarregado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetModule(   
   IDebugModule2** pModule,  
   BSTR*           pbstrDebugMessage,  
   BOOL*           pbLoad  
);  
```  
  
```csharp  
int GetModule(   
   out IDebugModule2 pModule,  
   ref string        pbstrDebugMessage,  
   ref int           pbLoad  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pModule`  
 [out] Retorna um [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) objeto que representa o módulo de carregamento ou descarregamento.  
  
 `pbstrDebugMessage`  
 [out no] Retorna uma mensagem opcional que descreve esse evento. Se esse parâmetro for um valor nulo, nenhuma mensagem é solicitada.  
  
 `pbLoad`  
 [out no] Diferente de zero (`TRUE`) se o módulo está sendo carregado e zero (`FALSE`) se o módulo está descarregando. Se esse parâmetro for um valor nulo, nenhum status é solicitado.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retorna `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md)   
 [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)