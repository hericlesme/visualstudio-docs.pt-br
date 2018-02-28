---
title: IDebugMessageEvent2::GetMessage | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugMessageEvent2::GetMessage
helpviewer_keywords:
- GetMessage method
- IDebugMessageEvent2::GetMessage method
ms.assetid: 9fca7285-f7f1-422d-8565-92bf0e0db60a
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 2cb6db61048765ec577a0d14ff4079f78e013219
ms.sourcegitcommit: bd16e764134c436d2d2f46490f51234d5246ee50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/22/2018
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
 [out] Retorna o tipo da mensagem, usando as convenções do Win32 `MessageBox` função. Consulte o [AfxMessageBox](/cpp/mfc/reference/cstring-formatting-and-message-box-display#afxmessagebox) função para obter detalhes.  
  
 `pbstrHelpFileName`  
 [out no] Retorna o nome do arquivo de Ajuda. Pode ser um valor vazio (c#) ou o nulo (C++), se não houver nenhum arquivo de Ajuda.  
  
 `pdwHelpId`  
 [out no] Retorna o identificador da Ajuda. Pode ser 0 se não houver nenhuma ajuda associada com esta mensagem.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retorna `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugMessageEvent2](../../../extensibility/debugger/reference/idebugmessageevent2.md)   
 [MESSAGETYPE](../../../extensibility/debugger/reference/messagetype.md)   
 [AfxMessageBox](/cpp/mfc/reference/cstring-formatting-and-message-box-display#afxmessagebox)