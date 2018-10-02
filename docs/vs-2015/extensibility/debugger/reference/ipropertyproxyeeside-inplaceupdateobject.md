---
title: IPropertyProxyEESide::InPlaceUpdateObject | Microsoft Docs
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
- IPropertyProxyEESide::InPlaceUpdateObject
helpviewer_keywords:
- IPropertyProxyEESide::InPlaceUpdateObject
ms.assetid: abf89411-1853-4f23-b244-d5e0afa197b1
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2d806eec4d5d03b3ac589cca2de5dd6146231723
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47474944"
---
# <a name="ipropertyproxyeesideinplaceupdateobject"></a>IPropertyProxyEESide::InPlaceUpdateObject
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [IPropertyProxyEESide::InPlaceUpdateObject](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/ipropertyproxyeeside-inplaceupdateobject).  
  
Atualiza os dados do objeto com o objeto de dados fornecido e retorna um novo objeto de dados que representa os dados do objeto novo.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT InPlaceUpdateObject(  
   [in] IEEDataStorage*   dataIn,  
   [out] IEEDataStorage** dataOut  
);  
```  
  
```csharp  
int InPlaceUpdateObject(  
   IEEDataStorage     dataIn,  
   out IEEDataStorage dataOut  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `dataIn`  
 [in] Uma [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) objeto que contém os novos dados.  
  
 `dataOut`  
 [out] Retorna um novo `IEEDataStorage` objeto que contém os dados substituídos.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Na verdade, esse método atualiza os dados do objeto. Os dados em retornado [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) objeto não precisa ser o mesmo que os dados de entrada `IEEDataStorage` objeto, mas o objeto retornado deve refletir o valor da propriedade atual.  
  
 O objeto de dados de entrada não costuma ser implementado pelo EE. No entanto, o objeto retornado por esse método sempre é implementado pelo EE, que permite que o implemente EE o `IEEDataStorage` interface em qualquer classe for desejada.  
  
 O [CreateReplacementObject](../../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md) método cria um objeto de dados com base no objeto de entrada de dados, mas não afeta os dados de original da propriedade.  
  
## <a name="see-also"></a>Consulte também  
 [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)   
 [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)   
 [CreateReplacementObject](../../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md)

