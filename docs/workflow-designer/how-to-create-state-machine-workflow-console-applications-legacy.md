---
title: "Como: criar aplicativos de Console de fluxo de trabalho de máquina de estado (o legados) | Microsoft Docs"
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- console applications, state machine workflows
- state machine workflow console applications
- state machine workflows, console applicationa
ms.assetid: d6170b5d-5d4f-48e1-8257-c78604f27eac
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 1d345afcddaae2e3a139fbf7861b78f57774ead6
ms.sourcegitcommit: 37c87118f6f41e832da96f21f6b4cc0cf8fee046
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2018
---
# <a name="how-to-create-state-machine-workflow-console-applications-legacy"></a>Como: Criar aplicativos de console do fluxo de trabalho do computador de estado (o legados)
Siga estas etapas para criar um projeto de aplicativo de Console de fluxo de trabalho de máquina de estado usando o Designer de fluxo de trabalho herdado do Windows fornecida pelo [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)]. Use [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] herdado quando você precisa definir como alvo [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] ou [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].

### <a name="to-create-a-state-machine-application-project"></a>Para criar um projeto de aplicativo do computador de estado

1.  Inicie o Visual Studio.

2.  Sobre o **arquivo** , aponte para **novo**e, em seguida, selecione **projeto**.

     A caixa de diálogo **Novo Projeto** é aberta.

3.  Selecione o **.NET Framework 3.0** opção ou **.NET Framework 3.5** opção no menu suspenso na parte superior da lista da **novo projeto** janela para acessar o designer herdado.

    > [!NOTE]
    > A opção padrão na [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)] é **.NET Framework 4**. Essa opção é usada criar aplicativos de [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] que direcionam [!INCLUDE[netfx40_short](../workflow-designer/includes/netfx40_short_md.md)] e usa o designer herdado.

4.  No **tipos de projeto** painel, selecione Visual c# ou Visual Basic (em **outras linguagens**) e, em seguida, selecione **fluxo de trabalho**.

5.  No **modelos** painel, selecione **aplicativo de Console de fluxo de trabalho de máquina de estado**.

6.  No **nome** , digite um nome descritivo para o seu projeto tornar mais fácil de identificar.

7.  No **local** , digite o diretório no qual você deseja salvar o projeto ou clique em **procurar** para navegar até ele.

     Se você desejar um diretório da solução para o projeto, selecione o **criar diretório para solução** caixa de seleção e insira um nome no **nome da solução** caixa.

8.  Clique em **OK**.

## <a name="see-also"></a>Consulte também

- [Criando projetos herdados de fluxo de trabalho](../workflow-designer/creating-legacy-workflow-projects.md)
- [Como criar uma biblioteca de fluxo de trabalho da máquina de estado (herdado)](../workflow-designer/how-to-create-a-state-machine-workflow-library-legacy.md)