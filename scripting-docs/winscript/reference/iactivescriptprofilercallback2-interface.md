---
title: Interface IActiveScriptProfilerCallback2 | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IActiveScriptProfilerCallback2 interface
ms.assetid: 8f2e62e4-c232-4dc3-a2c0-54dd06298306
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2dc9fcd8ca4afec0fb474c0f3a7317b608c7c9f6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptprofilercallback2-interface"></a>Interface IActiveScriptProfilerCallback2
Fornece métodos que são usados pelo mecanismo de script para notificar um objeto do criador de perfil, quando ocorrem eventos de modelo de objeto de documento (DOM). Essa interface é implementada pelo objeto do criador de perfil.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[IActiveScriptProfilerCallback2::OnFunctionEnterByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionenterbyname.md)|Notifica o objeto do criador de perfil que o mecanismo de script para executar uma chamada de função do DOM.|  
|[IActiveScriptProfilerCallback2::OnFunctionExitByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionexitbyname.md)|Notifica o criador de perfil de objeto que o script do mecanismo terminar de executar uma chamada de função do DOM.|  
  
## <a name="remarks"></a>Comentários  
 O `IActiveScriptProfilerCallback2` interface lançado com o Internet Explorer 9.  
  
 Notificação de chamadas de função que não são chamadas no DOM é fornecida pelo [IActiveScriptProfilerCallback Interface](../../winscript/reference/iactivescriptprofilercallback-interface.md).  
  
> [!NOTE]
>  Para adicionar a capacidade de iniciar e interromper a criação de perfil quando um script é executado, chame os métodos a seguir. Usando esses métodos, você pode obter a pilha de chamadas completa se [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] estiver em execução quando você iniciar ou interromper a criação de perfil.  
>   
>  -   Chamar [IActiveScriptProfilerControl2::CompleteProfilerStart](../../winscript/reference/iactivescriptprofilercontrol2-completeprofilerstart.md) para notificar o criador de perfil que você tiver começado a criação de perfil.  
> -   Chamar [IActiveScriptProfilerControl2::PrepareProfilerStop](../../winscript/reference/iactivescriptprofilercontrol2-prepareprofilerstop.md) para notificar o criador de perfil que você assim parar criação de perfil.  
  
## <a name="see-also"></a>Consulte também  
 [Interfaces do criador de perfil de script ativo](../../winscript/reference/active-script-profiler-interfaces.md)