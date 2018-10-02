---
title: IDebugBinder3::FindAlias | Microsoft Docs
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
- IDebugBinder3::FindAlias
helpviewer_keywords:
- IDebugBinder3::FindAlias method
ms.assetid: b8333701-2718-4983-8513-0875fb7cb730
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d638ed77b2ddcab54431862a26cdbab8a356e4ea
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47466686"
---
# <a name="idebugbinder3findalias"></a>IDebugBinder3::FindAlias
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [IDebugBinder3::FindAlias](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugbinder3-findalias).  
  
Esse método localiza um alias, dado um nome. Isso irá procurar todos os aliases no programa.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT FindAlias(  
   LPCOLESTR     pcstrName,  
   IDebugAlias** ppAlias  
);  
```  
  
```csharp  
int FindAlias(  
   string          pcstrName,  
   out IDebugAlias ppAlias  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pcstrName`  
 [in] Nome do alias para localizar.  
  
 `ppAlias`  
 [out] Alias encontrada (se houver) representado pela [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md) interface.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna `S_FALSE` (se o alias não for encontrado) ou um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Esse método inicializa o objeto de destino para nulo antes de chamar; em seguida, ele testa um valor nulo determinar se o alias foi encontrado.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)   
 [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)

