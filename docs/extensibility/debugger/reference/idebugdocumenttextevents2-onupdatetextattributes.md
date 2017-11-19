---
title: IDebugDocumentTextEvents2::onUpdateTextAttributes | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugDocumentTextEvents2::OnUpdateTextAttributes
helpviewer_keywords: IDebugDocumentTextEvents2::onUpdateTextAttributes
ms.assetid: eb68d69a-1ad9-4ce4-84e1-40979ef16634
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 18a6de2f4aa3bbbcfa5d6a2e4ad091d8b4e7577f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="idebugdocumenttextevents2onupdatetextattributes"></a>IDebugDocumentTextEvents2::onUpdateTextAttributes
Notifica o pacote de depuração que atributos de texto foram atualizados no documento.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT onUpdateTextAttributes(   
   TEXT_POSITION pos,  
   DWORD         dwNumToUpdate  
);  
```  
  
```csharp  
int onUpdateTextAttributes(   
   enum_TEXT_POSITION pos,  
   uint               dwNumToUpdate  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pos`  
 [in] Um [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) estrutura que indica onde os atributos de texto foram atualizados.  
  
 `dwNumToUpdate`  
 [in] Especifica o número de caracteres de texto que foram atualizadas.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retorna `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)   
 [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)