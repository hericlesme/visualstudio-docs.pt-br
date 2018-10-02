---
title: IDebugExtendedField | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IDebugExtendedField interface
ms.assetid: b491499c-af57-47da-87d6-34b7398f6591
caps.latest.revision: 7
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ace5f36ccebc5861c7fe31bba9be41b35a8fdcf5
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47462262"
---
# <a name="idebugextendedfield"></a>IDebugExtendedField
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [IDebugExtendedField](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugextendedfield).  
  
Estende os tipos de campos que estão disponíveis para oferecer suporte a genéricos de código gerenciado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
IDebugExtendedField : IDebugField  
```  
  
## <a name="methods"></a>Métodos  
 Além dos métodos na [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) interface, essa interface implementa os seguintes métodos:  
  
|Método|Descrição|  
|------------|-----------------|  
|[GetExtendedKind](../../../extensibility/debugger/reference/idebugextendedfield-getextendedkind.md)|Recupera o tipo de campo estendidas especificado.|  
|[IsClosedType](../../../extensibility/debugger/reference/idebugextendedfield-isclosedtype.md)|Determina se o campo representa um tipo fechado.|  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: Sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

