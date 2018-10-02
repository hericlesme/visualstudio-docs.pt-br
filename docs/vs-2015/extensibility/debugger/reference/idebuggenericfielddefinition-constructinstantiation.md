---
title: IDebugGenericFieldDefinition::ConstructInstantiation | Microsoft Docs
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
- ConstructInstantiation
- IDebugGenericFieldDefinition::ConstructInstantiation
ms.assetid: ef8ae261-a98b-4dc2-93b3-7c5191818ba2
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8c5bd1d6164019414bc7cc299e418c38365dbc95
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47475249"
---
# <a name="idebuggenericfielddefinitionconstructinstantiation"></a>IDebugGenericFieldDefinition::ConstructInstantiation
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [IDebugGenericFieldDefinition::ConstructInstantiation](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebuggenericfielddefinition-constructinstantiation).  
  
Constrói uma instância do campo considerando uma matriz de argumentos de tipo.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT ConstructInstantiation(  
   ULONG32       cArgs,  
   IDebugField** ppArgs,  
   IDebugField** ppConstructedField  
);  
```  
  
```csharp  
int ConstructInstantiation(  
   uint            cArgs,  
   IDebugField[]   ppArgs,  
   out IDebugField ppConstructedField  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `cArgs`  
 [in] Número de argumentos no `ppArgs` matriz.  
  
 `ppArgs`  
 [in] Matriz que contém os argumentos de tipo. Os argumentos de tipo devem ser tipos fechados (genéricos não genéricas ou totalmente instanciados).  
  
 `ppConstructedField`  
 [out] Retorna o [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) interface que representa o novo campo.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 As restrições não são verificadas.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugGenericFieldDefinition](../../../extensibility/debugger/reference/idebuggenericfielddefinition.md)

