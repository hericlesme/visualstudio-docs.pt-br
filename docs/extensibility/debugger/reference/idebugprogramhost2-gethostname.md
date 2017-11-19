---
title: IDebugProgramHost2::GetHostName | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProgramHost2::GetHostName
helpviewer_keywords: IDebugProgramHost2::GetHostName
ms.assetid: 48bbb089-e59a-471a-9965-24b42a8dabf3
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7f1a77c7882dd85c1c64acb492b2522d77649b54
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="idebugprogramhost2gethostname"></a>IDebugProgramHost2::GetHostName
Obtém o título, o nome amigável ou o nome do arquivo do processo de hospedagem desse programa.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
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
 [in] Um valor da [GETHOSTNAME_TYPE](../../../extensibility/debugger/reference/gethostname-type.md) enumeração.  
  
 `pbstrHostName`  
 [out] Retorna o nome solicitado do processo de hospedagem.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retorna `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Em uma implementação típica desse método, o `dwType` parâmetro será ignorado e um nome amigável da máquina de host é retornado. É outra implementação possível passar o `dwType` parâmetro para uma chamada para o [GetHostName](../../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md) método para obter o nome.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugProgramHost2](../../../extensibility/debugger/reference/idebugprogramhost2.md)   
 [GetHostName](../../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md)