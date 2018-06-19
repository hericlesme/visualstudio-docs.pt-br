---
title: Designer de fluxo de trabalho - desativando o depurador do Visual Studio para Windows Workflow Foundation (legados)
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
helpviewer_keywords:
- workflows, disabling debugger
- debugging workflows, disabling debugger
- workflow debugger, disabling
ms.assetid: 9da96d0e-f941-4fa9-a1a5-6bab50adfec9
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 473ee507e35f5ec5df902df64ee34326dcf90a2b
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31969959"
---
# <a name="disabling-the-visual-studio-debugger-for-windows-workflow-foundation-legacy"></a>Desativando o depurador do Visual Studio para Windows Workflow Foundation (legados)

Este tópico descreve como desabilitar o depurador do Visual Studio usando o arquivo de configuração ao criar aplicativos do Windows Workflow Foundation (WF) no Designer de fluxo de trabalho herdado do Windows. Use o Designer de fluxo de trabalho herdado quando você precisa direcionar o .NET Framework versão 3.5 ou o WinFX.

 Por padrão, o Visual Studio depurador para Windows Workflow Foundation (WF) está habilitado para um processo de host. Para desabilitar a depuração de fluxo de trabalho, você deve explicitamente desativá-lo adicionando uma entrada de "DisableWorkflowDebugging"  **\<switches >** elemento o  **\<System. Diagnostics >** seção do arquivo de configuração de host.

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