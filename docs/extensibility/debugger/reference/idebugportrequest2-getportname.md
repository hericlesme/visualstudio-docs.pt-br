---
title: IDebugPortRequest2::GetPortName | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugPortRequest2::GetPortName
helpviewer_keywords:
- IDebugPortRequest2::GetPortName
ms.assetid: 53e2a3a4-bb34-4a02-a983-6bd84ea70587
caps.latest.revision: 10
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 5906560574836390656254055130af3275fa4f76
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="idebugportrequest2getportname"></a>IDebugPortRequest2::GetPortName
Obtém o nome da porta.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetPortName(   
   BSTR* pbstrPortName  
);  
```  
  
```csharp  
int GetPortName(   
   out string pbstrPortName  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pbstrPortName`  
 [out] Retorna o nome da porta.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retorna `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 O [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md) interface é normalmente passada de um pacote de depuração (cliente) para um fornecedor de porta (o servidor) para obter uma conexão a uma porta. O pacote de depuração e o fornecedor de porta estão cientes de opções possíveis para a porta. Se uma cadeia de caracteres simple pode descrever a porta, o `IDebugPortRequest2::GetPortName` método tem informações suficientes para fazer a conexão. Caso contrário, as interfaces adicionais podem ser fornecidas pelo cliente, o que pode ser obtido usando o servidor `IDebugPortRequest2::QueryInterface`.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)