---
title: IEEDataStorage::GetData | Microsoft Docs
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
- IEEDataStorage::GetData
helpviewer_keywords:
- IEEDataStorage::GetData
ms.assetid: 4d384039-73d4-40b4-ace6-a2474c546397
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f3461ec27c00148bf70617856ea900094bd3c78b
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47463303"
---
# <a name="ieedatastoragegetdata"></a>IEEDataStorage::GetData
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [IEEDataStorage::GetData](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/ieedatastorage-getdata).  
  
Recupera o número especificado de bytes do objeto.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT GetData(  
   ULONG  dataSize,  
   ULONG* sizeGotten,  
   BYTE*  data  
);  
```  
  
```csharp  
int GetData(  
   uint     dataSize,  
   out uint sizeGotten,  
   byte[]   data  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `dataSize`  
 [in] O número de bytes a serem recuperados (o `data` matriz deve conter pelo menos esse número de bytes).  
  
 `sizeGotten`  
 [out] Retorna o número de bytes realmente recuperados.  
  
 `data`  
 [no, out] Matriz a ser preenchida com os dados solicitados.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 É recomendado o uso desse método recuperar todos os bytes de dados em uma matriz local, já que não há nenhuma maneira de ignorar bytes no processo de recuperação. Nesse caso, o parâmetro `dataSize` deve ser o valor retornado pelo [GetSize](../../../extensibility/debugger/reference/ieedatastorage-getsize.md) método.  
  
## <a name="see-also"></a>Consulte também  
 [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)   
 [GetSize](../../../extensibility/debugger/reference/ieedatastorage-getsize.md)

