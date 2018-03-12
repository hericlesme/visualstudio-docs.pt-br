---
title: Desativando o depurador do Visual Studio para Windows Workflow Foundation (legados) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- workflows, disabling debugger
- debugging workflows, disabling debugger
- workflow debugger, disabling
ms.assetid: 9da96d0e-f941-4fa9-a1a5-6bab50adfec9
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: d3ec3d87952f17feb8a59ae8acbda603451fbf4d
ms.sourcegitcommit: 37c87118f6f41e832da96f21f6b4cc0cf8fee046
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2018
---
# <a name="disabling-the-visual-studio-debugger-for-windows-workflow-foundation-legacy"></a>Desativando o depurador do Visual Studio para Windows Workflow Foundation (legados)

Este tópico descreve como desabilitar o [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] usando o arquivo de configuração durante a criação do depurador [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] aplicativos no Designer de fluxo de trabalho herdado do Windows. Use [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] herdado quando você precisa definir como alvo [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] ou [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].

 Por padrão, o depurador de [!INCLUDE[vs_current_long](../misc/includes/vs_current_long_md.md)] para [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] é habilitado para um processo host. Para desabilitar a depuração de fluxo de trabalho, você deve explicitamente desativá-lo adicionando uma entrada de "DisableWorkflowDebugging"  **\<switches >** elemento o  **\<System. Diagnostics >**seção do arquivo de configuração de host.

 O exemplo a seguir mostra como modificar o arquivo de configuração do host para desativar a depuração de fluxo de trabalho.

```xml
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

- [Invocando o depurador do Visual Studio para Windows Workflow Foundation (herdado)](../workflow-designer/invoking-the-visual-studio-debugger-for-windows-workflow-foundation-legacy.md)
- [Depurando fluxos de trabalho herdados](../workflow-designer/debugging-legacy-workflows.md)