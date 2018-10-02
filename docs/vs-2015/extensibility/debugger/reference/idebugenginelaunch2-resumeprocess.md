---
title: IDebugEngineLaunch2::ResumeProcess | Microsoft Docs
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
- IDebugEngineLaunch2::ResumeProcess
helpviewer_keywords:
- IDebugEngineLaunch2::ResumeProcess
ms.assetid: 61ccc14e-75c6-44e7-aae4-57a9aac52089
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2447571d45b8d97ab9c9303be1e1804fb9c3bce3
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47475751"
---
# <a name="idebugenginelaunch2resumeprocess"></a>IDebugEngineLaunch2::ResumeProcess
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [IDebugEngineLaunch2::ResumeProcess](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugenginelaunch2-resumeprocess).  
  
Retoma a execução do processo.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT ResumeProcess (   
   IDebugProcess2* pProcess  
);  
```  
  
```csharp  
int ResumeProcess (   
   IDebugProcess2 pProcess  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pProcess`  
 [in] Uma [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) objeto que representa o processo para ser retomada.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retornará um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Esse método é chamado depois que um processo foi iniciado com uma chamada para o [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) método.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)

