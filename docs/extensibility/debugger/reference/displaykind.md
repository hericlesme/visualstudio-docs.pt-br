---
title: DisplayKind | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: DisplayKind enumeration
ms.assetid: 940968c5-6065-4bda-8ee6-c31597db4d71
caps.latest.revision: "5"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 230be9a3c1d7e3bcbddc85bc37226a2a2baef6a3
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="displaykind"></a>DisplayKind
Enumera os valores válidos que representam os tipos de informações para colocar um [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) de objeto e exibir para o usuário.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
enum enum_DisplayKind  
{  
   DisplayKind_Value = 0x1,  
   DisplayKind_Name = 0x2,  
   DisplayKind_Type = 0x3,  
};  
typedef DWORD DisplayKind;  
```  
  
```csharp  
public enum enum_DisplayKind  
{  
   DisplayKind_Value = 0x1,  
   DisplayKind_Name = 0x2,  
   DisplayKind_Type = 0x3,  
};  
```  
  
#### <a name="parameters"></a>Parâmetros  
 DisplayKind_Value  
 Valor do campo.  
  
 DisplayKind_Name  
 Nome do campo.  
  
 DisplayKind_Type  
 Tipo de campo.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: Ee.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Enumerações](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetValueDisplayStringCount](../../../extensibility/debugger/reference/ieevisualizerservice-getvaluedisplaystringcount.md)