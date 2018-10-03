---
title: IPropertyProxyEESide::CreateReplacementObject | Microsoft Docs
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
- IPropertyProxyEESide::CreateReplacementObject
helpviewer_keywords:
- IPropertyProxyEESide::CreateReplacementObject
ms.assetid: 0cfe79b8-c3f1-48b0-a225-e39dee2c92fe
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 048fe0e60422d5d787424256009ef585a133c914
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47462954"
---
# <a name="ipropertyproxyeesidecreatereplacementobject"></a>IPropertyProxyEESide::CreateReplacementObject
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [IPropertyProxyEESide::CreateReplacementObject](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject).  
  
Cria uma cópia de um objeto de dados específicos para o avaliador de expressão (EE).  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT CreateReplacementObject(  
   IEEDataStorage*  dataIn,  
   IEEDataStorage** dataOut  
);  
```  
  
```csharp  
int CreateReplacementObject(  
   IEEDataStorage     dataIn,  
   out IEEDataStorage dataOut  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `dataIn`  
 [in] Uma [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) objeto que contém os dados a serem copiados.  
  
 `dataOut`  
 [out] Retorna um novo `IEEDataStorage` objeto.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Esse método é fornecido um [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) objeto que representa uma matriz de bytes. Normalmente, esse objeto de dados de entrada não é implementado pelo EE. No entanto, o objeto retornado por esse método sempre é implementado pelo EE, que permite que o implemente EE o `IEEDataStorage` interface em qualquer classe for desejada.  
  
 Observe que os dados fornecidos pela entrada `IEEDataStorage` objeto deve ser os mesmos dados em que a saída `IEEDataStorage` objeto.  
  
## <a name="see-also"></a>Consulte também  
 [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)   
 [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)

