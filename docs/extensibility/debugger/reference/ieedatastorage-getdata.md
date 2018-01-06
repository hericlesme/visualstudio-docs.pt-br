---
title: IEEDataStorage::GetData | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IEEDataStorage::GetData
helpviewer_keywords: IEEDataStorage::GetData
ms.assetid: 4d384039-73d4-40b4-ace6-a2474c546397
caps.latest.revision: "7"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: e18b51c20d2eaf324782574bf007ce32fdc6df2e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ieedatastoragegetdata"></a>IEEDataStorage::GetData
Recupera o número especificado de bytes do objeto.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
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
 [out no] Matriz a ser preenchida com os dados solicitados.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retorna `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 É recomendado o uso desse método para recuperar todos os bytes de dados em uma matriz de local, pois não é possível ignorar bytes no processo de recuperação. Nesse caso, o parâmetro `dataSize` deve ser o valor retornado pelo [GetSize](../../../extensibility/debugger/reference/ieedatastorage-getsize.md) método.  
  
## <a name="see-also"></a>Consulte também  
 [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)   
 [GetSize](../../../extensibility/debugger/reference/ieedatastorage-getsize.md)