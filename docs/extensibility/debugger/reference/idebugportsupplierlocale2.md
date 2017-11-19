---
title: IDebugPortSupplierLocale2 | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: IDebugPortSupplierLocale2 interface
ms.assetid: 910e7220-da2a-4339-9fff-9fb1bad3c28c
caps.latest.revision: "4"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3a16404dc9e91c6f4383ea58d84a6a1716538c46
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="idebugportsupplierlocale2"></a>IDebugPortSupplierLocale2
Fornece suporte à localidade de um fornecedor de porta.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
IDebugPortSupplierLocale2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Observações para implementadores  
 Um fornecedor de porta personalizada implementa essa interface para definir a localidade.  
  
## <a name="methods"></a>Métodos  
 A tabela a seguir mostra os métodos de **IDebugPortSupplierLocale2**.  
  
|Método|Descrição|  
|------------|-----------------|  
|[SetLocale](../../../extensibility/debugger/reference/idebugportsupplierlocale2-setlocale.md)|Define a localidade para o fornecedor de porta.|  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: Portpriv.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Interfaces de núcleo](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)   
 [IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md)