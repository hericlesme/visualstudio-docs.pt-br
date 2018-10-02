---
title: IDebugProgramHost2::GetHostName | Microsoft Docs
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
- IDebugProgramHost2::GetHostName
helpviewer_keywords:
- IDebugProgramHost2::GetHostName
ms.assetid: 48bbb089-e59a-471a-9965-24b42a8dabf3
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 420a25be81a124c89bc4139d80ae881b1f519726
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47474622"
---
# <a name="idebugprogramhost2gethostname"></a>IDebugProgramHost2::GetHostName
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [IDebugProgramHost2::GetHostName](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugprogramhost2-gethostname).  
  
Obtém o título, o nome amigável ou o nome do arquivo do processo de hospedagem desse programa.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT GetHostName(   
   DWORD dwType,  
   BSTR* pbstrHostName  
);  
```  
  
```csharp  
int GetHostName(   
   uint dwType,  
   out string pbstrHostName  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `dwType`  
 [in] Um valor a partir de [GETHOSTNAME_TYPE](../../../extensibility/debugger/reference/gethostname-type.md) enumeração.  
  
 `pbstrHostName`  
 [out] Retorna o nome solicitado do processo de hospedagem.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Em uma implementação típica desse método, o `dwType` parâmetro será ignorado e um nome amigável do computador host é retornado. Outra implementação possível é transmitir o `dwType` parâmetro para uma chamada para o [GetHostName](../../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md) método para obter o nome.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugProgramHost2](../../../extensibility/debugger/reference/idebugprogramhost2.md)   
 [GetHostName](../../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md)

