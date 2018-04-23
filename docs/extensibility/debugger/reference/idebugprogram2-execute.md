---
title: IDebugProgram2::Execute | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProgram2::Execute
helpviewer_keywords:
- IDebugProgram2::Execute
ms.assetid: f7205ce8-0ac6-4fcd-b6ec-b720b4fcaccf
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f7f4e26a5c892e1c796a2b6e2f9371898db21f68
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="idebugprogram2execute"></a>IDebugProgram2::Execute
Continua executando esse programa de um estado parado. Qualquer estado de execução anterior (como uma etapa) é desmarcado, e o programa inicia a execução novamente.  
  
> [!NOTE]
>  Este método é preterido. Use o [Execute](../../../extensibility/debugger/reference/idebugprocess3-execute.md) método em vez disso.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT Execute(  
   void  
);  
```  
  
```csharp  
int Execute();  
```  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retorna `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Quando o usuário inicia a execução de um estado parado no thread do outro programa, esse método é chamado neste programa. Este método também é chamado quando o usuário seleciona o **iniciar** comando o **depurar** menu no IDE. A implementação desse método pode ser tão simple quanto chamar o [retomar](../../../extensibility/debugger/reference/idebugthread2-resume.md) método no thread atual no programa.  
  
> [!WARNING]
>  Não enviar um evento de parada ou um evento (síncrono) imediato [evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) ao tratar essa chamada; caso contrário, o depurador pode travar.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [Evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)   
 [Resume](../../../extensibility/debugger/reference/idebugthread2-resume.md)