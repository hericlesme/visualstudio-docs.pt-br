---
title: MODULE_SYMBOL_SEARCH_INFO | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- MODULE_SYMBOL_SEARCH_INFO
helpviewer_keywords:
- MODULE_SYMBOL_SEARCH_INFO structure
ms.assetid: 432aff03-08a5-4c5a-b2d5-e212090fc70a
caps.latest.revision: 10
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: c4afe972f4f5218c04c1bd8a9223c7b317dc3ab3
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="modulesymbolsearchinfo"></a>MODULE_SYMBOL_SEARCH_INFO
Contém informações de status sobre os caminhos de pesquisa de símbolo que foram pesquisadas.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
typedef struct _tagSYMBOL_SEARCH_INFO  
{  
   SYMBOL_SEARCH_INFO_FIELDS dwValidFields;  
   BSTR                      bstrVerboseSearchInfo;  
} MODULE_SYMBOL_SEARCH_INFO;  
```  
  
```csharp  
public struct MODULE_SYMBOL_SEARCH_INFO {  
   public uint   dwValidFields;  
   public string bstrVerboseSearchInfo;  
}  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `dwValidFields`  
 Uma combinação de sinalizadores do [SYMBOL_SEARCH_INFO_FIELDS](../../../extensibility/debugger/reference/symbol-search-info-fields.md) enumeração que especifica o tipo de informações de pesquisa descritos nessa estrutura.  
  
 `bstrVerboseSearchInfo`  
 Caminho de pesquisa e resultados concatenados em uma única cadeia de caracteres.  
  
## <a name="remarks"></a>Comentários  
 Essa estrutura é retornada de uma chamada para o [GetSymbolInfo](../../../extensibility/debugger/reference/idebugmodule3-getsymbolinfo.md) método.  
  
 Se o `bstrVerboseSearchInfo` campo não for vazio, contém uma lista de caminhos pesquisados e os resultados da pesquisa. A lista é formatada com um caminho, seguido por um sinal de reticências ("..."), seguido pelo resultado. Se houver mais de um par de resultados de caminho, cada par é separado por um par de (carro-retorno/alimentação de linha) "\r\n". O padrão é semelhante a:  
  
 \<caminho >... \<resultado > \r\n\<caminho >... \<resultado > \r\n\<caminho >... \<resultado >  
  
 Observe que a última entrada não tem uma sequência \r\n.  
  
 Aqui está uma possível `bstrVerboseSearchInfo` cadeia de caracteres que foi enviada para saída padrão.  
  
 `c:\symbols\user32.pdb... File not found.`  
  
 `c:\winnt\symbols\user32.pdb... Version does not match.`  
  
 `\\symbols\symbols\user32.dll\0a8sd0ad8ad\user32.pdb... Symbols loaded.`  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Estruturas e uniões](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [GetSymbolInfo](../../../extensibility/debugger/reference/idebugmodule3-getsymbolinfo.md)