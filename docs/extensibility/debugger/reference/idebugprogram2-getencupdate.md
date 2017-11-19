---
title: IDebugProgram2::GetENCUpdate | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProgram2::GetENCUpdate
helpviewer_keywords: IDebugProgram2::GetENCUpdate
ms.assetid: 9832aac8-6320-4fd8-91dd-2a0852febb00
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1d0d14d407dbff9493af0206369cfd8b9c8d556c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="idebugprogram2getencupdate"></a>IDebugProgram2::GetENCUpdate
Esse método obtém a atualização de editar e continuar (c) para este programa. Um mecanismo de depuração personalizado sempre retorna `E_NOTIMPL`.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetENCUpdate(   
   IUnknown** ppUpdate  
);  
```  
  
```csharp  
int GetENCUpdate(  
   out object ppUpdate  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `ppUpdate`  
 [out] Retorna uma interface interna que pode ser usada para atualizar este programa.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retorna `S_OK`; caso contrário, retorna um código de erro.  
  
> [!NOTE]
>  Um mecanismo de depuração personalizado deve sempre retornar `E_NOTIMPL`.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)