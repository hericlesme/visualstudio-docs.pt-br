---
title: Depurando fluxos de trabalho de um computador remoto (legados) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- workflows, debugging remotely
- debugging workflows, remotely
- remote debugging, workflows
- debugging, remote
ms.assetid: 44eaec8f-9959-4ae7-a374-670946f933c1
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: be8c1f6a049224cc5b79a82dc6bc100840c72fd0
ms.sourcegitcommit: 37c87118f6f41e832da96f21f6b4cc0cf8fee046
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2018
---
# <a name="debugging-workflows-from-a-remote-computer-legacy"></a>Fluxos de trabalho de depuração de um computador remoto (legados)
Este tópico descreve como depurar herdado remoto [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] aplicativos que são criados com o Designer de fluxo de trabalho herdado do Windows. Use [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] herdado quando seu aplicativo precisa definir como alvo [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] ou [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].

 Quando você instala o [!INCLUDE[vs_current_long](../misc/includes/vs_current_long_md.md)], uma das opções de instalação de componente é instalar o [!INCLUDE[vs_current_long](../misc/includes/vs_current_long_md.md)] do depurador para [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)]. Isso instala os componentes de depuração remota. Esses componentes de depuração remota devem ser instalados no computador que você está definido para depuração remota de fluxo de trabalho.

 Além disso, o assembly que contém a definição de fluxo de trabalho de fluxo de trabalho herdado que você está depurando em um computador remoto deve ser instalado no cachê global de assemblies (GAC) do computador local que você está depurando de. Por exemplo, se um fluxo de trabalho herdado está em execução em um computador remoto e você está depurando-lo do computador local B, a definição de fluxo de trabalho deve estar presente no GAC do computador B. Isso permite que o designer desserializar e exibir no computador B a marcação de fluxo de trabalho do fluxo de trabalho que está executando remotamente no computador A. Para obter mais informações sobre o cache de assembly global, consulte a biblioteca MSDN.

 depuração remota de[!INCLUDE[wf2](../workflow-designer/includes/wf2_md.md)] funciona da mesma que a depuração remota para outros componentes de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . Para obter mais informações, consulte [!INCLUDE[vs_current_long](../misc/includes/vs_current_long_md.md)] depuração remota na biblioteca MSDN.

## <a name="see-also"></a>Consulte também

- [Depurando fluxos de trabalho herdados](../workflow-designer/debugging-legacy-workflows.md)