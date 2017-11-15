---
title: "Função JsGetArrayBufferStorage | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 712ae298-36a9-47ef-b089-e51835c056bc
caps.latest.revision: "2"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a667325eb4d1d9540751a52232e5e06b3004b8b5
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="jsgetarraybufferstorage-function"></a>Função JsGetArrayBufferStorage
Obtém o armazenamento subjacente de memória usado por uma `ArrayBuffer`.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
JsErrorCode STDAPI_ JsGetArrayBufferStorage(  
   _In_ JsValueRef arrayBuffer,  
   _Outptr_result_bytebuffer_(*bufferLength) BYTE **buffer,  
   _Out_ unsigned int *bufferLength  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `arrayBuffer`  
 A instância do ArrayBuffer.  
  
 `buffer`  
 O buffer do ArrayBuffer. O tempo de vida do buffer retornado é o mesmo que o tempo de vida da `ArrayBuffer`. O ponteiro de buffer não conta como uma referência para a `ArrayBuffer` para fins de coleta de lixo.  
  
 `bufferLength`  
 O número de bytes no buffer.  
  
## <a name="return-value"></a>Valor de retorno  
 O código `JsNoError` se a operação foi bem-sucedida, caso contrário, um código de falha.  
  
## <a name="remarks"></a>Comentários  
 Exige um contexto de script ativo.  
  
 Essa API tem suporte apenas no modo de Borda.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** jsrt.h  
  
## <a name="see-also"></a>Consulte também  
 [Referência (Tempo de Execução do JavaScript)](../chakra-hosting/reference-javascript-runtime.md)