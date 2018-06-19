---
title: Interface IActiveScriptProfilerCallback | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 76f9164b-b086-4b29-ac79-76f9c76f1d11
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f4dc4b9d4e3b1f83a37e64e3a85387fd378d3ca7
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24724576"
---
# <a name="iactivescriptprofilercallback-interface"></a>Interface IActiveScriptProfilerCallback
Fornece métodos que são usados pelo mecanismo de script para notificar um objeto do criador de perfil, quando ocorrem eventos. Essa interface é implementada pelo objeto do criador de perfil.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[IActiveScriptProfilerCallback::Initialize](../../winscript/reference/iactivescriptprofilercallback-initialize.md)|Chamado para inicializar o objeto do criador de perfil sempre que a criação de perfil é iniciada em um mecanismo de script.|  
|[IActiveScriptProfilerCallback::Shutdown](../../winscript/reference/iactivescriptprofilercallback-shutdown.md)|Chamado para liberar e liberar o objeto de criador de perfil sempre que a criação de perfil é interrompida em um mecanismo de script.|  
|[IActiveScriptProfilerCallback::ScriptCompiled](../../winscript/reference/iactivescriptprofilercallback-scriptcompiled.md)|Notifica o criador de perfil de objeto do mecanismo de script compilado no script.|  
|[IActiveScriptProfilerCallback::FunctionCompiled](../../winscript/reference/iactivescriptprofilercallback-functioncompiled.md)|Notifica o criador de perfil de objeto que o script do mecanismo encontrou uma função durante a compilação de um script.|  
|[IActiveScriptProfilerCallback::OnFunctionEnter](../../winscript/reference/iactivescriptprofilercallback-onfunctionenter.md)|Notifica o objeto do criador de perfil que o mecanismo de script está prestes a executar uma chamada de função não é uma chamada em modelo de objeto de documento (DOM).|  
|[IActiveScriptProfilerCallback::OnFunctionExit](../../winscript/reference/iactivescriptprofilercallback-onfunctionexit.md)|Notifica o criador de perfil de objeto que o mecanismo de script terminar de executar uma função chamada que não é uma chamada no DOM.|  
  
## <a name="remarks"></a>Comentários  
 Notificação de chamadas de função em modelo de objeto de documento (DOM) é fornecida pelo [Interface IActiveScriptProfilerCallback2](../../winscript/reference/iactivescriptprofilercallback2-interface.md).  
  
> [!NOTE]
>  Para adicionar a capacidade de iniciar e interromper a criação de perfil quando um script é executado, chame os métodos a seguir. Usando esses métodos, você pode obter a pilha de chamadas completa se [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] estiver em execução quando você iniciar ou interromper a criação de perfil.  
>   
>  -   Chamar [IActiveScriptProfilerControl2::CompleteProfilerStart](../../winscript/reference/iactivescriptprofilercontrol2-completeprofilerstart.md) para notificar o criador de perfil que você tiver começado a criação de perfil.  
> -   Chamar [IActiveScriptProfilerControl2::PrepareProfilerStop](../../winscript/reference/iactivescriptprofilercontrol2-prepareprofilerstop.md) para notificar o criador de perfil que você assim parar criação de perfil.  
  
## <a name="see-also"></a>Consulte também  
 [Interfaces do criador de perfil de script ativo](../../winscript/reference/active-script-profiler-interfaces.md)