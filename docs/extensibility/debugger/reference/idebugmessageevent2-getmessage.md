---
title: IDebugMessageEvent2::GetMessage | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugMessageEvent2::GetMessage
helpviewer_keywords:
- GetMessage method
- IDebugMessageEvent2::GetMessage method
ms.assetid: 9fca7285-f7f1-422d-8565-92bf0e0db60a
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 511826e54e4331084c3cbd5c34814b73d0e80078
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="idebugmessageevent2getmessage"></a>IDebugMessageEvent2::GetMessage
Obtém a mensagem a ser exibida.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetMessage(   
   MESSAGETYPE* pMessageType,  
   BSTR*        pbstrMessage,  
   DWORD*       pdwType,  
   BSTR*        pbstrHelpFileName,  
   DWORD*       pdwHelpId  
);  
```  
  
```csharp  
int GetMessage(   
   out enum_MESSAGETYPE pMessageType,  
   out string           pbstrMessage,  
   out uint             pdwType,  
   out string           pbstrHelpFileName,  
   out uint             dwHelpId  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pMessageType`  
 [out] Retorna um valor da [MESSAGETYPE](../../../extensibility/debugger/reference/messagetype.md) enumeração que descreve o tipo da mensagem.  
  
 `pbstrMessage`  
 [out] Retorna a mensagem.  
  
 `pdwType`  
 [out] Retorna o tipo da mensagem, usando as convenções do Win32 `MessageBox` função. Consulte o [AfxMessageBox](http://msdn.microsoft.com/Library/d66d0328-cdcc-48f6-96a4-badf089099c8) função para obter detalhes.  
  
 `pbstrHelpFileName`  
 [out no] Retorna o nome do arquivo de Ajuda. Pode ser um valor vazio (c#) ou o nulo (C++), se não houver nenhum arquivo de Ajuda.  
  
 `pdwHelpId`  
 [out no] Retorna o identificador da Ajuda. Pode ser 0 se não houver nenhuma ajuda associada com esta mensagem.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retorna `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugMessageEvent2](../../../extensibility/debugger/reference/idebugmessageevent2.md)   
 [MESSAGETYPE](../../../extensibility/debugger/reference/messagetype.md)   
 [AfxMessageBox](http://msdn.microsoft.com/Library/d66d0328-cdcc-48f6-96a4-badf089099c8)