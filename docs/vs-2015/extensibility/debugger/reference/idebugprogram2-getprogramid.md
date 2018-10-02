---
title: IDebugProgram2::GetProgramId | Microsoft Docs
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
- IDebugProgram2::GetProgramId
helpviewer_keywords:
- IDebugProgram2::GetProgramId
ms.assetid: 2c31c0aa-2b71-46c7-849c-356e237d26f8
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ec9805ef49da0331689f34e1657327f2a836b834
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47475377"
---
# <a name="idebugprogram2getprogramid"></a>IDebugProgram2::GetProgramId
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [IDebugProgram2::GetProgramId](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugprogram2-getprogramid).  
  
Obtém um GUID para este programa.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT GetProgramId(   
   GUID* pguidProgramId  
);  
```  
  
```csharp  
int GetProgramId(   
   out Guid pguidProgramId  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pguidProgramId`  
 [out] Retorna o `GUID` para este programa.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Um mecanismo de depuração (DES) deve retornar o identificador de programa originalmente passado para o [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) ou [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) métodos. Isso permite a identificação do programa em depurador componentes.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)   
 [Anexar](../../../extensibility/debugger/reference/idebugengine2-attach.md)

