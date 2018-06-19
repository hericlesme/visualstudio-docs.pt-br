---
title: Acessibilidade
description: Este artigo apresenta as funcionalidades de acessibilidade do Visual Studio para Mac e como elas podem ser habilitadas.
author: asb3993
ms.author: amburns
ms.date: 08/15/2017
ms.assetid: 2C4AAC2E-3B4A-4496-8BE0-1F5A7F81D1CA
ms.openlocfilehash: b1b2cb26f6e42486e8740bf9610baeeb308a9b66
ms.sourcegitcommit: 33c954fbc8e05f7ba54bfa2c0d1bc1f9bbc68876
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33870532"
---
# <a name="accessibility"></a>Acessibilidade

Além dos recursos e utilitários no macOS, o Visual Studio para Mac tem os seguintes recursos que o tornam mais acessível para pessoas portadoras de deficiência:

- Ampliação de Texto nos Painéis Editor e de Soluções
- Opções de tamanho de texto em editores
- Personalização de cor em editores
- Personalização de atalhos de teclado
- Preenchimento de código para métodos e parâmetros 

Para obter mais informações sobre recursos de acessibilidade no macOS, confira o [site da Apple](https://www.apple.com/accessibility/mac/).

## <a name="using-accessibility-features-in-visual-studio-for-mac"></a>Usar recursos de Acessibilidade no Visual Studio para Mac

Os recursos de Acessibilidade no Visual Studio para Mac estão desativados por padrão. Para habilitá-los, siga estas etapas:

1. Vá para **Visual Studio > Preferências > Outros > Acessibilidade**.

2. Selecione a caixa de seleção **Habilitar Acessibilidade**, conforme ilustrado no diagrama a seguir:

    ![Caixa de seleção Habilitar acessibilidade](media/accessibility-image1.png)

3. Pressione o botão **Reiniciar o Visual Studio** para permitir que os recursos de acessibilidade entrem em vigor.


Como alternativa, você pode usar a linha de comando para habilitar os recursos de acessibilidade. Para isso, digite o seguinte comando no terminal: 

```bash
defaults write com.microsoft.visual-studio com.monodevelop.AccessibilityEnabled 1 
```

Depois de ativar a acessibilidade, você precisa reiniciar o Visual Studio.

## <a name="how-to-use-keyboard-navigation"></a>Como usar a Navegação por Teclado

A navegação por teclado pode ser habilitada configurando a opção Acesso Completo por Teclado em **Preferências do Sistema > Teclado > Atalhos** como **Todos os Controles**:

  ![Painel Preferências do sistema no macOS](media/accessibility-image2.png)

A configuração de acesso completo por teclado ativa o retângulo de foco. Em seguida, você pode selecionar os controles usando:
- A tecla Tab para avançar pelos controles
- Shift-Tab para voltar pelos controles
- Teclas de direção para navegar entre os controles na direção das setas. 

Pressionar a barra de espaço ativa o controle com foco.

## <a name="how-to-enable-and-use-voice-over"></a>Como habilitar e usar o VoiceOver

Para ativar ou desativar o VoiceOver pressione **Cmd+F5**

Para navegar pelos comandos da interface do usuário do VoiceOver, use os seguintes comandos:

- Mova o cursor do VoiceOver entre Controles: **Ctrl+ Alt+Seta para a esquerda/Seta para a direita**

O VoiceOver lê o nome dos controles, alguns detalhes sobre eles e o que pode ser feito com eles. 

- Insira Grupos e controles (como o Painel de Soluções, Caixa de ferramentas e outros Painéis): **Ctrl+Alt+Shift+Seta para baixo**

Quando estiver dentro do controle, use **Ctrl+Alt+Setas** para se movimentar dentro dele. 
 
Para obter informações gerais sobre como usar o VoiceOver no macOS, confira os guias a seguir:

- [Introdução ao VoiceOver](https://help.apple.com/voiceover/info/guide/10.12/)
- [Comandos de VoiceOver no macOS](http://lab.dotjay.com/notes/voiceover-commands/)
