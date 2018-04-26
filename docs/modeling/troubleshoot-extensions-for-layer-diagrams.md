---
title: Solucionar problemas de extensões para diagramas de dependência
ms.date: 11/04/2016
ms.topic: troubleshooting
helpviewer_keywords:
- dependency diagrams, extension errors
- dependency diagrams, troubleshooting extensions
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: b56ccd587df4a830eab5bee000cafcc02b0031e8
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="troubleshoot-extensions-for-dependency-diagrams"></a>Solucionar problemas de extensões para diagramas de dependência

Este tópico aborda alguns problemas que você pode encontrar ao criar extensões de modelo de camada.

## <a name="when-i-press-f5-to-debug-my-extension-my-commands-gesture-handlers-validation-extensions-or-custom-properties-do-not-appear-on-dependency-diagrams-in-the-experimental-instance-of-includevsprvscode-qualityincludesvsprvsmdmd"></a>Ao pressionar F5 para depurar a extensão do my, meu comandos, manipuladores de gesto, extensões de validação ou propriedades personalizadas não aparecem em diagramas de dependência na instância Experimental do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]

1.  Abra sua solução de extensão na instância Experimental do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]e na **criar** menu, clique em **recompilar solução**.

2.  Pressione **F5** ou **CTRL + F5** para iniciar a instância experimental do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Abra um diagrama de dependência e sua extensão de teste.

 Continue com o próximo procedimento, se necessário.

## <a name="an-old-version-of-my-extension-runs"></a>Executa uma versão antiga da extensão do my.

1.  Certifique-se de que nenhuma instância experimental do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] está em execução.

2.  Exclua a seguinte pasta: %LocalAppData%\Microsoft\VisualStudio\\\ComponentModelCache [versão]

    > [!NOTE]
    > % LocalAppData % normalmente é *DriveName*: \Users\\*UserName*\AppData\Local.

 Continue com o próximo procedimento, se necessário.

## <a name="an-old-version-of-my-validation-results-appears-or-my-validation-method-is-not-called"></a>Uma versão antiga do meu resultados de validação aparece ou meu método de validação não for chamado.

1.  Na instância experimental do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], no **criar** menu, clique em **limpar solução**. Isso limpa os resultados em cache da análise de validação anterior.

2.  Certifique-se de que as camadas em seu modelo são associadas aos elementos de código, e se há pelo menos um link de dependência no modelo. A validação não é invocada se não há nada para validar.

3.  Pontos de interrupção regulares podem não funcionar em um método de validação, porque ele é executado em um processo separado. Você deve inserir uma chamada para `System.Diagnostics.Debugger.Launch()` se você quiser passar pelo seu método.

4.  Em **source.extension.vsixmanifest** no seu projeto de validação de camada, certifique-se de que você adicionou ambos um **MEF componente** item e um **o tipo de extensão personalizada** item em **Conteúdo**.

## <a name="see-also"></a>Consulte também

- [Estender diagramas de dependência](../modeling/extend-layer-diagrams.md)
