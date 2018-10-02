---
title: IDebugEngineProgram2::Stop | Microsoft Docs
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
- IDebugEngineProgram2::Stop
helpviewer_keywords:
- IDebugEngineProgram2::Stop
ms.assetid: 6e1c3d56-fb67-4a5b-80f9-8ee5131972bf
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 29067ce022150f53612ba053cee5ce20c2c96fa6
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47475360"
---
# <a name="idebugengineprogram2stop"></a>IDebugEngineProgram2::Stop
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [IDebugEngineProgram2::Stop](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugengineprogram2-stop).  
  
Interrompe todos os threads em execução nesse programa.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT Stop(   
   void   
);  
```  
  
```csharp  
int Stop();  
```  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Esse método é chamado quando este programa está sendo depurado em um ambiente de vários programa. Quando um evento de interrupção de algum outro programa for recebido, este método é chamado neste programa. A implementação deste método deve ser assíncrona; ou seja, nem todos os threads devem ser necessárias para ser interrompido antes desse método retorna. A implementação desse método pode ser tão simple quanto chamar o [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md) método neste programa.  
  
 Nenhum evento de depuração é enviado em resposta a esse método.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)   
 [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)

