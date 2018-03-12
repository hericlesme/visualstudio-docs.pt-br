---
title: Visual C++ IntelliSense | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 3d375ebccd96f6b8e987bd74f229abd70bfa9ab6
ms.sourcegitcommit: d16c6812b114a8672a58ce78e6988b967498c747
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/02/2018
---
# <a name="visual-c-intellisense"></a>Visual C++ IntelliSense

O IntelliSense para C++ está disponível para arquivos autônomos, bem como para arquivos que fazem parte de um projeto em C++. Em projetos multiplaforma, alguns recursos do IntelliSense estão disponíveis nos arquivos .cpp e .c no projeto de código compartilhado, mesmo quando você está em um contexto Android ou iOS.

## <a name="intellisense-features-in-c"></a>Recursos do IntelliSense em C++

IntelliSense é um nome dado a um conjunto de recursos que tornam a codificação mais conveniente. Uma vez que pessoas diferentes têm ideias diferentes sobre o que é conveniente, praticamente todos os recursos do IntelliSense podem ser habilitados ou desabilitados na caixa de diálogo **Opções**, em **Editor de Texto** > **C/C++** > **Avançado**. A caixa de diálogo **Opções** está disponível no menu **Ferramentas** na barra de menus.

![Caixa de diálogo Opções de Ferramentas](../ide/media/sintellisensecpptoolsoptions.PNG)

Você pode usar os itens de menu e os atalhos de teclado mostrados na imagem a seguir para acessar o IntelliSense.

![Menu IntelliSense](../ide/media/vs2015_cpp_intellisense_menu.png)

### <a name="statement-completion-and-member-list"></a>Lista de membro e preenchimento de declaração

Quando você começa a digitar uma palavra-chave, um tipo, uma função, um nome de variável ou outro elemento de programa que o compilador reconhece, o editor se oferece para completar a palavra para você.

Para obter uma lista de ícones e seus significados, consulte [Modo de Exibição de Classe e ícones do Pesquisador de Objetos](../ide/class-view-and-object-browser-icons.md).

![Janela Completar Palavra do Visual CC&#43;&#43;](../ide/media/vs2015_cpp_complete_word.png "vs2015_cpp_complete_word")

Na primeira vez que a lista de membros é invocada, ela mostra apenas membros acessíveis para o contexto atual. Se você pressionar **Ctrl**+**J** depois disso, ela mostrará todos os membros, independentemente da acessibilidade. Se você invocá-la uma terceira vez, uma lista ainda maior de elementos do programa será mostrada. Você pode desativar a lista de membros na caixa de diálogo **Opções**, em **Editor de Texto** > **C/C++** > **Geral** > **Listar membros automaticamente**.

![Lista de membros do Visual C&#43;&#43;](../ide/media/vs2015_cpp_list_members.png "vs2015_cpp_list_members")

### <a name="parameter-help"></a>Ajuda do parâmetro

Quando você digita uma chave de abertura de uma chamada de função ou colchete angular em uma declaração de variável de modelo de classe, o editor mostra uma pequena janela com tipos de parâmetro para cada sobrecarga da função ou do construtor. O parâmetro "atual"&mdash;com base no local do cursor&mdash;está em negrito. Você pode desativar as informações de parâmetro na caixa de diálogo **Opções**, em **Editor de Texto** > **C/C++** > **Geral** > **Informações de parâmetro**.

![Ajuda de Parâmetro do Visual C&#43;&#43;](../ide/media/vs_2015_cpp_param_help.png "vs_2015_cpp_param_help")

### <a name="quick-info"></a>Informação Rápida

Quando você passa o cursor do mouse sobre uma variável, aparece uma pequena janela embutida que mostra as informações de tipo e o cabeçalho no qual o tipo é definido. Passe o cursor do mouse sobre uma chamada de função para ver a assinatura da função. Você pode desativar as Informações Rápidas na caixa de diálogo **Opções**, em **Editor de Texto** > **C/C++** > **Avançado** > **Informações Rápidas Automáticas**.

![Informações Rápidas do Visual C&#43;&#43;](../ide/media/vs2015_cpp_quickinfo.png "vs2015_cpp_quickInfo")

### <a name="error-squiggles"></a>Linhas onduladas de erro

Linhas onduladas em um elemento de programa (variável, palavra-chave, chave, nome do tipo e assim por diante) chamam a atenção para um erro ou erro em potencial no código. Uma linha ondulada verde é exibida quando você escreve uma declaração de encaminhamento para lembrá-lo de que você ainda precisa escrever a implementação. Uma linha ondulada roxa aparece em um projeto compartilhado quando há um erro no código que não está ativo no momento, por exemplo, quando você está trabalhando no contexto do Windows, mas digita algo que seria um erro em um contexto do Android. Uma linha ondulada vermelha indica um erro do compilador ou aviso no código ativo que você precisa resolver.

![Linhas onduladas de erro do Visual C&#43;&#43;](../ide/media/vs2015_cpp_error_quiggles.png "vs2015_cpp_error_quiggles")

### <a name="code-colorization-and-fonts"></a>Colorização e fontes de código

As fontes e cores padrão podem ser alteradas na caixa de diálogo **Opções**, em **Ambiente** > **Fontes e Cores**. Você pode alterar as fontes para muitas janelas da interface do usuário aqui, não apenas para o editor. As configurações específicas do C++ começam com "C++"; as outras configurações são para todas as linguagens.

### <a name="cross-platform-intellisense"></a>IntelliSense multiplaforma

Em um projeto de código compartilhado, alguns recursos do IntelliSense, como linhas onduladas, estão disponíveis, mesmo quando você está trabalhando em um contexto Android. Se você escrever algum código que resultaria em um erro em um projeto inativo, o IntelliSense ainda mostrará linhas onduladas, mas elas estarão em uma cor diferente das linhas onduladas para erros no contexto atual.

Há um aplicativo OpenGLES configurado para build no Android e no iOS. A ilustração mostra o código compartilhado que está sendo editado. Na primeira imagem, Android é o projeto ativo:

![O projeto Android é o projeto ativo.](../ide/media/intellisensecppcrossplatform.png "IntelliSenseCppCrossPlatform")

Observe o seguinte:

- A ramificação #else na linha 8 é esmaecida para indicar a região inativa, pois __ANDROID\_\_ está definido para o projeto Android.

- A variável de saudação na linha 11 é inicializada com o identificador HELLO, que tem uma linha ondulada roxa. Isso ocorre porque nenhum identificador HELLO é definido no projeto iOS atualmente inativo. Embora a linha de projeto 11 fosse compilada no Android, ela não seria no iOS. Uma vez que esse é um código compartilhado, que é algo que você deve alterar, embora ele compile na configuração ativa no momento.

- A Linha 12 tem linha ondulada vermelha no identificador BYE; esse identificador não está definido no projeto ativo atualmente selecionado.

Agora, altere o projeto ativo para iOS.StaticLibrary e observe como as linhas onduladas mudam.

![iOS está selecionado como o projeto ativo.](../ide/media/intellisensecppcrossplatform2.png "IntelliSenseCppCrossPlatform2")

Observe o seguinte:

- A ramificação #ifdef na linha 6 é esmaecida para indicar a região inativa, pois __ANDROID\_\_ não está definido para o projeto iOS.

- A variável de saudação na linha 11 é inicializada com o identificador HELLO, que agora tem uma linha ondulada vermelha. Isso ocorre porque nenhum identificador HELLO está definido no projeto iOS inativo no momento.

- A linha 12 tem linha ondulada roxa no identificador BYE; esse identificador não está definido no projeto Android.NativeActivity inativo no momento.

### <a name="intellisense-for-stand-alone-files"></a>IntelliSense para arquivos autônomos

Ao abrir um arquivo único fora de qualquer projeto, você ainda obtém o IntelliSense. Você pode habilitar ou desabilitar os recursos do IntelliSense específicos na caixa de diálogo **Opções**, em **Editor de Texto** > **C/C++** > **Avançado**. Para configurar o IntelliSense para arquivos únicos que não fazem parte de um projeto, procure a seção **IntelliSense e navegação para arquivos que não são de projeto**.

![IntelliSense de arquivo único do Visual C&#43;&#43;](../ide/media/vs2015_cpp_single_file_intellisense.png "vs2015_cpp_single_file_intellisense")

Por padrão, IntelliSense de arquivo único usa apenas diretórios de inclusão padrão para localizar arquivos de cabeçalho. Para adicionar mais diretórios, abra o menu de atalho no nó Solução e adicione seu diretório à lista **Depurar Código-Fonte**, como mostra a ilustração a seguir:

![Adicionando um caminho a um arquivo de cabeçalho.](../ide/media/intellisensedebugyourcode.jpg "IntelliSenseDebugYourCode")

## <a name="see-also"></a>Consulte também

[Usando o IntelliSense](../ide/using-intellisense.md)