---
title: IDebugProgram2::CauseBreak | Microsoft Docs
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
- IDebugProgram2::CauseBreak
helpviewer_keywords:
- IDebugProgram2::CauseBreak
ms.assetid: 07d353fc-68ab-4297-a18f-3d3c7a80e121
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a1bfd8c2094c6ef9d961eb5375aae7cf5c6d13da
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47463270"
---
# <a name="idebugprogram2causebreak"></a>IDebugProgram2::CauseBreak
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [IDebugProgram2::CauseBreak](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugprogram2-causebreak).  
  
Solicitações que o programa parar a execução a próxima hora em que uma das suas tentativas de threads para executar.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT CauseBreak(   
   void   
);  
```  
  
```csharp  
int CauseBreak();  
```  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Uma [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md) evento é enviado quando o programa tenta executar código após esse método é chamado em seguida.  
  
 Esse método é assíncrono, em que o método retornará imediatamente sem esperar que o programa pare necessariamente.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md)

