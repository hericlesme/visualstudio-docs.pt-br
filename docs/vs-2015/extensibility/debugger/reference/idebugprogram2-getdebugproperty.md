---
title: IDebugProgram2::GetDebugProperty | Microsoft Docs
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
- IDebugProgram2::GetDebugProperty
helpviewer_keywords:
- IDebugProgram2::GetDebugProperty
ms.assetid: d194224e-f0e6-46ab-85d4-9e2639e28946
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e92d0a20fb9639e3a969ff30a5b6b512019895a5
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47460453"
---
# <a name="idebugprogram2getdebugproperty"></a>IDebugProgram2::GetDebugProperty
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [IDebugProgram2::GetDebugProperty](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugprogram2-getdebugproperty).  
  
Obtém as propriedades do programa.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT GetDebugProperty(   
   IDebugProperty2** ppProperty  
);  
```  
  
```csharp  
int GetDebugProperty(   
   out IDebugProperty2 ppProperty  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `ppProperty`  
 [out] Retorna um [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) objeto que representa as propriedades do programa.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 As propriedades retornadas por esse método são específicas para o programa. Se o programa precisa retornar mais de uma propriedade, em seguida, a [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) objeto retornado por esse método é um recipiente de propriedades adicionais e chamar o [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) método retorna um lista de todas as propriedades.  
  
 Um programa pode expor qualquer número e tipo de propriedades adicionais que podem ser descritos por meio de `IDebugProperty2` interface. Um IDE pode exibir as propriedades adicionais do programa por meio de uma interface de usuário do navegador de propriedade genérica.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)

