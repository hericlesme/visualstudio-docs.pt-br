---
title: "Escrever código no editor de código | Microsoft Docs"
ms.custom: 
ms.date: 09/27/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.texteditor
dev_langs:
- JScript
- VB
- CSharp
helpviewer_keywords:
- code editor, word wrap
- outlining
- code, editing
- squiggles
- code editor, outlining
- code editor, error and warning markers
- word wrap
- code editor, syntax coloring
- code editor, go to definition
- diff
- code editor [Visual Studio]
- code editor, diff
- error and warning markers
- code editor, navigation bar
- code editor, customizing
- comment selection
- code editor, tabify
- brace matching
- code editor, line numbers
- printing
- code editor, brace matching
- code editor, squiggles
- code editor, features
- line numbers
- go to definition
- syntax coloring
- code editor, go to
- code editor, comparing files
- code editor, zoom
- code editor
- code files
- go to line
- tabify
- zoom
- go to
- line break characters
- code editor, virtual space
- code editor, change tracking
- code editor, comment selection
- code editor, printing
- virtual space
- code editor, line break characters
- code editor, go to line
- code
ms.assetid: cb53ab9a-5b76-4759-b9e8-7bf32298ecbe
caps.latest.revision: "44"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: bde177cb8f9ec8e72a331c785addfa7fead64dc7
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/13/2018
---
# <a name="write-code-in-the-code-editor"></a>Escrever código no editor de códigos
O editor do Visual Studio fornece muitos recursos que facilitam escrever e gerenciar seu código e texto. Você pode expandir e recolher blocos de código diferentes usando a estrutura de tópicos. Você pode aprender mais sobre o código através do IntelliSense, do **Pesquisador de Objetos** e da Hierarquia de Chamada. Você pode localizar o código usando recursos como **Navegar Para**, **Ir para Definição** e **Localizar Todas as Referências**. Você pode inserir blocos de código com trechos de código e pode gerar código usando recursos como o **Gerar do uso**. Se você nunca usou o editor do Visual Studio, consulte [Editando seu Código](https://www.visualstudio.com/features/ide-vs) para obter uma visão geral rápida.  

 Você pode exibir seu código de várias maneiras diferentes. Por padrão, o **Gerenciador de Soluções** mostra seu código organizado por arquivos. Você pode clicar na guia **Modo de Exibição de Classe** na parte inferior da janela para exibir o código organizado por classes.

 Você pode pesquisar e substituir texto em um ou vários arquivos. Para obter mais informações, consulte [Localizando e substituindo texto](../ide/finding-and-replacing-text.md). É possível usar expressões regulares para localizar e substituir texto. Para obter mais informações, consulte [Usando expressões regulares no Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).  

 As diferentes linguagens do Visual Studio oferecem conjuntos de recursos diferentes e, em alguns casos, os recursos se comportam de forma diferente nas diferentes linguagens. Muitas dessas diferenças são especificadas nas descrições dos recursos, mas para obter mais informações, consulte as seções sobre as linguagens específicas do Visual Studio.  

> [!IMPORTANT]
>  A edição do Visual Studio e as configurações que você está usando podem afetar os recursos no IDE. Eles podem ser diferentes dos descritos neste tópico.  

## <a name="editor-features"></a>Recursos do Editor  

|||  
|-|-|  
|Coloração de sintaxe|Alguns elementos de sintaxe dos arquivos de código e de marcação são coloridos de maneiras diferentes para diferenciá-los. Por exemplo, palavras-chave (como `using` no C# e `Imports` no Visual Basic) são de uma cor, mas tipos (como `Console` e `Uri`) são de outra cor. Outros elementos de sintaxe também são coloridos, como comentários e literais de cadeia de caracteres. O C++ usa cores para fazer diferenciação entre tipos, enumerações e macros, entre outros tokens.<br /><br /> Você pode ver a cor padrão de cada tipo e pode alterar a cor de qualquer elemento de sintaxe específico na [caixa de diálogo Fontes e Cores, Ambiente, Opções](../ide/reference/fonts-and-colors-environment-options-dialog-box.md), que pode ser aberta no menu **Ferramentas**.|  
|Marcas de Erro e Aviso|Enquanto adiciona código e compila sua solução, você pode ver: (a)sublinhados ondulados de cores diferentes (conhecidos como rabiscos) ou (b) lâmpadas que aparecem em seu código. Rabiscos vermelhos indicam erros de sintaxe, azul indica erros de compilador, verde indica avisos e roxo indica outros tipos de erros. [As lâmpadas](../ide/perform-quick-actions-with-light-bulbs.md) sugerem correções para problemas e facilitam a aplicação da correção.<br /><br /> Você pode ver a cor padrão de cada rabisco de erro e de aviso na caixa de diálogo **Ferramentas/Opções/Ambiente/Fontes e Cores**. Procure por **Erro de Sintaxe**, **Erro do Compilador**, **Aviso** e **Outro Erro**.|  
|Correspondência de chave|Quando o ponto de inserção é colocado em uma chave de abertura em um arquivo de código, essa chave de abertura e a chave de fechamento são realçadas. Esse recurso fornece comentários imediatos sobre chaves no local incorreto ou ausentes. Você pode ativar ou desativar a correspondência de chaves com a configuração **Realce automático de delimitadores** (**Ferramentas/Opções/Editor de Texto**). Você pode alterar a cor do realce na configuração **Fontes e Cores** (**Ferramentas/Opções/Ambiente**). Procure **Correspondência de Chaves (Realce)** ou **Correspondência de Chaves (Retângulo)**.|  
|Visualizador de Estrutura|Linhas pontilhadas conectam chaves correspondentes nos arquivos de código, o que facilita ver a abertura e o fechamento de pares de chave. Isso pode ajudar a localizar o código em sua base de código mais rapidamente. Você pode ativar ou desativar essas linhas em **Mostrar diretrizes de estrutura** na seção **Exibição** da página **Ferramentas/Opções/Editor de Texto/Geral**.|
|Números de Linha|Os números de linha podem ser exibidos na margem esquerda da janela de código. Eles não são exibidos por padrão. Você poderá ativar essa opção nas configurações **Todas as Linguagens do Editor de Texto** (**Ferramentas/Opções/Editor de Texto/Todas as Linguagens**). Você pode exibir números de linha para linguagens de programação individuais, alterando as configurações para essas linguagens (**Ferramentas/Opções/Editor de Texto/\<linguagem>**). Para imprimir os números de linha é necessário selecionar **Incluir números de linha** na caixa de diálogo **Imprimir**.|  
|Controle de Alterações|A cor da margem esquerda permite que você mantenha o controle das alterações feitas em um arquivo. As alterações que foram feitas desde que o arquivo foi aberto mas não foram salvas são indicadas por uma barra amarela na margem esquerda (conhecida como a margem de seleção). Depois de salvar as alterações (mas antes de fechar o arquivo), a barra ficará verde. Se você desfizer uma alteração depois de salvar o arquivo, a barra ficará laranja. Para desativar e ativar esse recurso, altere a opção **Controlar Alterações** nas configurações **Editor de Texto** (**Ferramentas/Opções/Editor de Texto**).|  
|Seleção de código e texto|É possível selecionar texto no modo padrão de fluxo contínuo ou no modo de caixa, no qual você seleciona uma parte retangular do texto em vez de um conjunto de linhas. Para fazer uma seleção no modo de caixa, pressione a tecla ALT enquanto arrasta o mouse sobre a seleção (ou pressione ALT + SHIFT + \<tecla de direção>). A seleção inclui todos os caracteres dentro do retângulo definido pelo primeiro caractere e o último caractere na seleção. Tudo que é digitado ou colado na área selecionada é inserido no mesmo ponto em cada linha.|  
|Aplicar Zoom|Você pode ampliar ou reduzir em qualquer janela de código pressionando a tecla CTRL e, mantendo-a pressionada, mover a roda de rolagem do mouse (ou CTRL + SHIFT +. para aumentar e CTRL + SHIFT +, para diminuir). Você também pode usar a caixa de Zoom no canto inferior esquerdo da janela de código para definir um percentual específico de aplicação de zoom. O recurso de aplicar zoom não funciona em janelas de ferramentas.|  
|Espaço virtual|Por padrão, as linhas nos editores do Visual Studio terminam após o último caractere de forma que a tecla SETA PARA A DIREITA, ao final de uma linha, move o cursor para o início da próxima linha. Em alguns editores uma linha não termina depois do último caractere e é possível colocar o cursor em qualquer lugar na linha. Você pode habilitar o espaço virtual no editor nas configurações **Ferramentas/Opções/Editor de Texto/Todas as Linguagens**. Observe que você pode habilitar **Espaço virtual** ou **Quebra automática de linha**, mas não ambos.|  
|Imprimindo|Você pode usar as opções da caixa de diálogo **Imprimir** para incluir números de linha ou ocultar regiões de código recolhidas ao imprimir um arquivo. Na caixa de diálogo **Configuração de Página** também é possível imprimir o caminho completo e o nome do arquivo, escolhendo **Cabeçalho de Página**.<br /><br /> Você pode definir opções de impressão a cores na caixa de diálogo **Ferramentas/Opções/Ambiente/Fontes e Cores**. Escolha **Impressora** na lista **Mostrar configurações de** para personalizar a impressão a cores. Você pode especificar cores para imprimir um arquivo diferentes das cores para edição de um arquivo.|  
|Desfazer global e Refazer|O comandos **Desfazer Última Ação Global** e **Refazer Última Ação Global** no menu **Editar** desfazem ou refazem ações globais que afetam vários arquivos. As ações globais incluem renomeação de uma classe ou namespace, executar uma operação de localização e substituição em uma solução, refatoração de um banco de dados ou qualquer outra ação que altera vários arquivos. Você pode aplicar os comandos desfazer e refazer global para ações na sessão atual do Visual Studio, mesmo depois de fechar a solução na qual a ação foi aplicada.|  

## <a name="advanced-editing-features"></a>Recursos de edição avançada  
 Você pode encontrar uma série de recursos avançados no submenu **Editar/Avançado**. Nem todos esses recursos estão disponíveis para todos os tipos de arquivos de código.  

|||  
|-|-|  
|Formatar Documento|Define o recuo adequado das linhas de código e move as chaves para separar linhas no documento.|  
|Formatar Seleção|Define o recuo adequado das linhas de código e move as chaves para separar linhas na seleção.|  
|Tabular linhas selecionadas|Troca espaços à esquerda por tabulações quando for apropriado.|  
|Cancelar tabulação das linhas selecionadas|Troca tabulações à esquerda por espaços. Se você desejar converter todos os espaços em seu arquivo para tabulações (ou todas as tabulações para espaços), você poderá usar os comandos `Edit.ConvertSpacesToTabs` e `Edit.ConvertTabsToSpaces`. Esses comandos não aparecem nos menus do Visual Studio, mas você pode chamá-los da janela de Acesso Rápido ou na janela Comando.|  
|Colocar em Maiúsculas|Alterar todos os caracteres na seleção para maiúsculos ou se não houver nenhuma seleção, altera o caractere no ponto de inserção para maiúsculo.|  
|Colocar em Minúsculas|Alterar todos os caracteres na seleção para minúsculos ou se não houver nenhuma seleção, altera o caractere no ponto de inserção para minúsculo.|  
|Mover linhas selecionadas para cima|Move a linha selecionada uma linha para cima. Atalho: ALT + SETA PARA CIMA.|
|Mover Linhas Selecionadas para Baixo|Move a linha selecionada uma linha para baixo. Atalho: ALT + SETA PARA BAIXO.|
|Validar Documento|Valida os arquivos de código JScript.|  
|Excluir Espaço em Branco Horizontal|Exclui tabulações ou espaços ao final da linha atual.|  
|Exibir Espaço em Branco|Exibe espaços como pontos elevados e tabulações como setas. O final de um arquivo é exibido como um glifo retangular. Se **Ferramentas/Opções/Editor de Texto/Todas as Linguagens/Quebra automática de linha/Mostrar glifos visíveis para quebra automática de linha** estiver selecionado, esse glifo também será exibido.|  
|Quebra automática de linha|Faz com que todas as linhas em um documento sejam visíveis na janela de código. Você pode ativar e desativar a quebra automática de linha na configuração Todas as Linguagens do Editor de Texto (**Ferramentas/Opções/Editor de Texto/Todas as Linguagens**).|  
|Comentar Seleção|Adiciona caracteres de comentários na seleção ou na linha atual.|  
|Remover Comentários da Seleção|Remove caracteres de comentários da seleção ou da linha atual.|  
|Aumentar recuo de linha|Adiciona uma tabulação (ou os espaços equivalentes) nas linhas selecionadas ou na linha atual.|  
|Diminuir recuo de linha|Remove uma tabulação (ou os espaços equivalentes) das linhas selecionadas ou da linha atual.|  
|Selecionar Marca|Em um documento que contém marcas (por exemplo, XML ou HTML), seleciona a marca.|  
|Selecionar Conteúdo da Marca|Em um documento que contém marcas (por exemplo, XML ou HTML), seleciona o conteúdo.|  

## <a name="navigate-and-find-code"></a>Navegar e localizar código  
Você pode se mover pelo editor de códigos de várias maneiras diferentes, incluindo navegar para trás e para frente até pontos de inserção anteriores, exibir a definição de um tipo ou membro e saltar até um método específico, usando a barra de navegação. Para obter mais informações, consulte [Navegação pelo código](navigating-code.md).  

## <a name="finding-references-in-your-code-base"></a>Localizando referências em sua base de código  
Para localizar onde os elementos de código específicos são referenciados em toda a sua base de código, é possível usar o comando **Localizar Todas as Referências**. Além disso, quando você clica em um tipo ou membro, o recurso **realce de referência** destaca automaticamente todas as referências a esse tipo ou membro. Para obter mais informações, consulte [Localizando referências no código](finding-references.md).  

## <a name="customize-the-editor"></a>Personalizar o Editor  
É possível compartilhar configurações do Visual Studio com outro desenvolvedor, fazer com que suas configurações estejam em conformidade com um padrão ou retornar às configurações padrão do Visual Studio usando o comando **Assistente de Importação e Exportação de Configurações** no menu **Ferramentas**. No **Assistente de Importação e Exportação de Configurações**, é possível alterar configurações gerais selecionadas ou idioma e configurações específicas do projeto.

Para definir novas teclas de atalho ou redefinir as teclas de atalho existentes, vá até **Ferramentas**, **Opções**, **Ambiente**, **Teclado**. Para obter mais informações sobre teclas de atalho, consulte [Atalhos de teclado padrão](../ide/default-keyboard-shortcuts-in-visual-studio.md).

Para obter mais informações sobre como personalizar o editor, consulte [Personalizando o Editor](../ide/customizing-the-editor.md). Para conferir opções do editor específicas a JavaScript, veja [Opções, Editor de Texto, JavaScript, Formatação](../ide/reference/options-text-editor-javascript-formatting.md).

## <a name="see-also"></a>Consulte também

[Visual Studio IDE](../ide/visual-studio-ide.md)
