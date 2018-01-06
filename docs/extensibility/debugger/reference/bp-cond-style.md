---
title: BP_COND_STYLE | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: BP_COND_STYLE
helpviewer_keywords: BP_COND_STYLE enumeration
ms.assetid: a93b1412-f447-48a1-af9d-38f3dbb3092f
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: b3d7bd22633985973975cb54d54ab3eb0837e30b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="bpcondstyle"></a>BP_COND_STYLE
Especifica o estilo de condição de ponto de interrupção para pendente e associadas a pontos de interrupção.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
enum enum_BP_COND_STYLE {   
   BP_COND_NONE         = 0x0000,  
   BP_COND_WHEN_TRUE    = 0x0001,  
   BP_COND_WHEN_CHANGED = 0x0002  
};  
typedef DWORD BP_COND_STYLE;  
```  
  
```csharp  
public enum enum_BP_COND_STYLE {   
   BP_COND_NONE         = 0x0000,  
   BP_COND_WHEN_TRUE    = 0x0001,  
   BP_COND_WHEN_CHANGED = 0x0002  
};  
```  
  
## <a name="members"></a>Membros  
 BP_COND_NONE  
 Aciona o ponto de interrupção quando a posição do ponto de interrupção é atingida. Nenhuma condição de ponto de interrupção especificada.  
  
 BP_COND_WHEN_TRUE  
 Aciona o ponto de interrupção somente quando a expressão condicional associado com o ponto de interrupção é avaliada como `true`.  
  
 BP_COND_WHEN_CHANGED  
 Aciona o ponto de interrupção somente quando o valor da expressão condicional associada com o ponto de interrupção foi alterado de sua avaliação anterior.  
  
## <a name="remarks"></a>Comentários  
 Usado para o `styleCondition` membro o [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md) estrutura.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Enumerações](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md)