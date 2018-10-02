---
title: MESSAGETYPE | Microsoft Docs
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
- MESSAGETYPE
helpviewer_keywords:
- MESSAGETYPE enumeration
ms.assetid: 800cc77d-3c27-4763-a9df-552a9384bd49
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f4e6bb32aa3387d79ea233e8751c5805537947fe
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47463283"
---
# <a name="messagetype"></a>MESSAGETYPE
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [MESSAGETYPE](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/messagetype).  
  
Especifica o tipo de mensagem e o motivo.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
enum enum_MESSAGETYPE {   
   MT_OUTPUTSTRING      = 0x0000001,  
   MT_MESSAGEBOX        = 0x00000002,  
   MT_TYPE_MASK         = 0x000000FF,  
   MT_REASON_EXCEPTION  = 0x00000100,  
   MT_REASON_TRACEPOINT = 0x00000200,  
   MT_REASON_MASK       = 0x0000FF00  
};  
typedef DWORD MESSAGETYPE;  
```  
  
```csharp  
public enum enum_MESSAGETYPE {   
   MT_OUTPUTSTRING      = 0x0000001,  
   MT_MESSAGEBOX        = 0x00000002,  
   MT_TYPE_MASK         = 0x000000FF,  
   MT_REASON_EXCEPTION  = 0x00000100,  
   MT_REASON_TRACEPOINT = 0x00000200,  
   MT_REASON_MASK       = 0x0000FF00  
};  
```  
  
## <a name="members"></a>Membros  
 MT_OUTPUTSTRING  
 Indica que a mensagem deve ser enviada para a janela de saída. Isso é mutuamente exclusivo de `MT_MESSAGEBOX`.  
  
 MT_MESSAGEBOX  
 Indica que a mensagem deve ser mostrada em uma caixa de mensagem. Isso é mutuamente exclusivo de `MT_OUTPUTSTRING`.  
  
 MT_TYPE_MASK  
 Um valor de máscara para isolar o destino da mensagem.  
  
 MT_REASON_EXCEPTION  
 Indica que uma caixa de mensagem está sendo mostrada como resultado de uma exceção. Isso é mutuamente exclusivo de `MT_REASON_TRACEPOINT`.  
  
 MT_REASON_TRACEPOINT  
 Indica que uma caixa de mensagem está sendo mostrada como resultado de atingir um tracepoint. Isso é mutuamente exclusivo para `MT_REASON_EXCEPTION`.  
  
 MT_REASON_MASK  
 Um valor de máscara para isolar o motivo para a mensagem que está sendo mostrado.  
  
## <a name="remarks"></a>Comentários  
 Esses valores são retornados a partir de [GetMessage](../../../extensibility/debugger/reference/idebugmessageevent2-getmessage.md) e [GetErrorMessage](../../../extensibility/debugger/reference/idebugerrorevent2-geterrormessage.md) métodos.  
  
 Um dos valores de motivo pode ser combinado com um dos valores de destino de saída usando um bit a bit `OR`.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Enumerações](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetMessage](../../../extensibility/debugger/reference/idebugmessageevent2-getmessage.md)   
 [GetErrorMessage](../../../extensibility/debugger/reference/idebugerrorevent2-geterrormessage.md)

