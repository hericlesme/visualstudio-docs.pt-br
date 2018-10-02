---
title: IDebugProperty2::SetValueAsString | Microsoft Docs
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
- IDebugProperty2::SetValueAsString
helpviewer_keywords:
- IDebugProperty2::SetValueAsString
ms.assetid: 9e6a5054-41b7-4223-b509-b93689d366a5
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f94ad530988ca354a1dd7618df0c7911987511e2
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47475346"
---
# <a name="idebugproperty2setvalueasstring"></a>IDebugProperty2::SetValueAsString
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [IDebugProperty2::SetValueAsString](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugproperty2-setvalueasstring).  
  
Define o valor de uma propriedade de uma determinada cadeia de caracteres.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT SetValueAsString (   
   LPCOLESTR pszValue,  
   UINT      nRadix,  
   DWORD     dwTimeout  
);  
```  
  
```csharp  
int SetValueAsString (   
   string pszValue,  
   uint   nRadix,  
   uint   dwTimeout  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pszValue`  
 [in] Uma cadeia de caracteres que contém o valor a ser definido.  
  
 `nRadix`  
 [in] Uma base a ser usado na interpretação de todas as informações numéricas. Isso pode ser 0 para tentar determinar a base automaticamente.  
  
 `dwTimeout`  
 [in] Especifica o tempo máximo, em milissegundos, para aguardar antes de retornar do método. Use `INFINITE` para aguardar indefinidamente.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retornará o código de erro. A tabela a seguir mostra os outros valores possíveis.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`E_SETVALUE_VALUE_CANNOT_BE_SET`|A cadeia de caracteres não pôde ser convertida em um valor de propriedade ou não foi possível definir o valor da propriedade.|  
|`E_SETVALUE_VALUE_IS_READONLY`|A propriedade é somente leitura.|  
  
## <a name="see-also"></a>Consulte também  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)

