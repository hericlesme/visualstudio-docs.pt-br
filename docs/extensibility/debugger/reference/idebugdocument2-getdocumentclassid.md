---
title: IDebugDocument2::GetDocumentClassID | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugDocument2::GetDocumentClassID
helpviewer_keywords: IDebugDocument2::GetDocumentClassID
ms.assetid: 111c2b85-ebfa-487f-b896-2ec4a3eac4d1
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e216cf5af1ad22acf81f46ca385f7092e8ee8316
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="idebugdocument2getdocumentclassid"></a>IDebugDocument2::GetDocumentClassID
Obtém o identificador de classe do documento.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetDocumentClassID(   
   CLSID* pclsid  
);  
```  
  
```csharp  
int GetDocumentClassID(   
   out Guid pclsid  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pclsid`  
 [out] Retorna um GUID que é a ID de classe do documento.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retorna `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 A classe GUID pode ser usada para criar uma instância de classes individuais de cada um deles representa um documento.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)