---
title: IEnumDebugCustomAttributes::Reset | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IEnumCustomAttributes::Reset
helpviewer_keywords: IEnumDebugCustomAttributes::Reset
ms.assetid: e0db6518-5a71-4adb-a407-4d2ac7a3e369
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9b593b7bcd22b5eb8c12fffb6fe277a68a9da12f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="ienumdebugcustomattributesreset"></a>IEnumDebugCustomAttributes::Reset
Redefine a sequência de enumeração para o início.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT Reset(void);  
```  
  
```csharp  
int Reset();  
```  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retorna `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Depois que este método é chamado, a próxima chamada para o [próximo](../../../extensibility/debugger/reference/ienumdebugcustomattributes-next.md) método retorna o primeiro elemento da enumeração.  
  
## <a name="see-also"></a>Consulte também  
 [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)   
 [Avançar](../../../extensibility/debugger/reference/ienumdebugcustomattributes-next.md)