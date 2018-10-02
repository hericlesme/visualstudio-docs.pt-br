---
title: FIELD_INFO_FIELDS | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- FIELD_INFO_FIELDS
helpviewer_keywords:
- FIELD_INFO_FIELDS enumeration
ms.assetid: a69487d2-e701-4165-804a-8a011df9a3bd
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c181d1483dc33e8931436c24fc3cf681d182ab34
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47473215"
---
# <a name="fieldinfofields"></a>FIELD_INFO_FIELDS
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [FIELD_INFO_FIELDS](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/field-info-fields).  
  
Especifica quais informações devem ser recuperadas sobre um [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) objeto.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
enum enum_FIELD_INFO_FIELDS {   
   FIF_FULLNAME  = 0x0001,  
   FIF_NAME      = 0x0002,  
   FIF_TYPE      = 0x0004,  
   FIF_MODIFIERS = 0x0008,  
   FIF_ALL       = 0xffffffff,  
   FIF_NONE      = 0x0000  
};  
typedef DWORD FIELD_INFO_FIELDS;  
```  
  
```csharp  
public enum enum_FIELD_INFO_FIELDS {  
   FIF_FULLNAME  = 0x0001,  
   FIF_NAME      = 0x0002,  
   FIF_TYPE      = 0x0004,  
   FIF_MODIFIERS = 0x0008,  
   FIF_ALL       = 0xffffffff,  
   FIF_NONE      = 0x0000  
};  
```  
  
## <a name="members"></a>Membros  
 FIF_FULLNAME  
 Inicialização/usar o `bstrFullName` campo de [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md) estrutura.  
  
 FIF_NAME  
 Inicialização/usar o `bstrName` campo o `FIELD_INFO` estrutura.  
  
 FIF_TYPE  
 Inicialização/usar o `bstrType` campo o `FIELD_INFO` estrutura.  
  
 FIF_MODIFIERS  
 Inicialização/usar o `bstrModifiers` campo o `FIELD_INFO` estrutura.  
  
## <a name="remarks"></a>Comentários  
 Esses valores também são passados como um argumento para o [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md) método para especificar quais campos da [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md) são de estrutura a ser inicializado.  
  
 Esses valores também são usados na `dwFields` membro o `FIELD_INFO` estrutura para indicar quais campos são usados e válido.  
  
 Esses sinalizadores podem ser combinados com um bit a bit `OR`.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Enumerações](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md)

