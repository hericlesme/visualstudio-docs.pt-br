---
title: IDebugProcess3::Continue | Microsoft Docs
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
- IDebugProcess3::Continue
helpviewer_keywords:
- IDebugProcess3::Continue
ms.assetid: 57506242-5763-4c08-adb9-8a78ce02cebb
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2cda72271a7a4654280a93e7fa7150c0dd295405
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47465774"
---
# <a name="idebugprocess3continue"></a>IDebugProcess3::Continue
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [IDebugProcess3::Continue](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugprocess3-continue).  
  
Continua a execução desse processo de um estado parado. Qualquer estado de execução anterior (por exemplo, uma etapa) é preservado, e o processo inicia a execução novamente.  
  
> [!NOTE]
>  Esse método deve ser usado em vez de [continuar](../../../extensibility/debugger/reference/idebugprogram2-continue.md).  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT Continue(  
   IDebugThread2* pThread  
);  
```  
  
```csharp  
int Continue(  
   IDebugThread2 pThread  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pThread`  
 [in] Uma [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) objeto que representa o thread a ser continuado.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retornará o código de erro.  
  
## <a name="remarks"></a>Comentários  
 Este método é chamado sobre esse processo, independentemente de quantos processos estão sendo depurados ou processo que gerou o evento de interrupção. A implementação deve manter o estado de execução anterior (por exemplo, uma etapa) e continuar a execução como se ele nunca foi interrompido antes de concluir sua execução anterior. Ou seja, se um thread nesse processo estava fazendo uma operação de percorrer e foi interrompido porque algum outro processo é interrompido e, em seguida, `Continue` foi chamado, especificado thread deve concluir a operação percorrer original.  
  
 **Aviso** envia um evento de interrupção ou um evento (síncrono) imediato [evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) ao manipular essa chamada; caso contrário, o depurador poderá parar de responder.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)

