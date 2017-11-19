---
title: Desativando o depurador do Visual Studio para Windows Workflow Foundation (legados) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- workflows, disabling debugger
- debugging workflows, disabling debugger
- workflow debugger, disabling
ms.assetid: 9da96d0e-f941-4fa9-a1a5-6bab50adfec9
caps.latest.revision: "6"
author: ErikRe
ms.author: erikre
manager: erikre
ms.openlocfilehash: 835ca509c86a9be27486ee257839c4e161221e4e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="disabling-the-visual-studio-debugger-for-windows-workflow-foundation-legacy"></a>Desativando o depurador do Visual Studio para Windows Workflow Foundation (legados)
Este tópico descreve como desativar o depurador de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] que usa o arquivo de configuração para criar aplicativos de [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] em [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)]herdado. Use [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] herdado quando você precisa definir como alvo [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] ou [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].  
  
 Por padrão, o depurador de [!INCLUDE[vs_current_long](../misc/includes/vs_current_long_md.md)] para [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] é habilitado para um processo host. Para desabilitar a depuração de fluxo de trabalho, você deve explicitamente desativá-lo adicionando uma entrada de "DisableWorkflowDebugging"  **\<switches >** elemento o  **\<System. Diagnostics >**seção do arquivo de configuração de host.  
  
 O exemplo a seguir mostra como modificar o arquivo de configuração do host para desativar a depuração de fluxo de trabalho.  
  
```  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
   <system.diagnostics>  
      <switches>  
         <add name="DisableWorkflowDebugging" value="true"/>  
      </switches>  
   </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a>Consulte também  
 [Chamar o depurador do Visual Studio para Windows Workflow Foundation (legados)](../workflow-designer/invoking-the-visual-studio-debugger-for-windows-workflow-foundation-legacy.md)   
 [Depurando fluxos de trabalho herdados](../workflow-designer/debugging-legacy-workflows.md)