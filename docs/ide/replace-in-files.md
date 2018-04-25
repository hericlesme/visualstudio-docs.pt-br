---
title: Localizar e substituir nos arquivos do Visual Studio| Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.findreplace.replaceinfiles
- vs.replaceinfiles
helpviewer_keywords:
- text searches, replacing text
- find and replace
- replace in files
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1e8b3dbf5582d7f19af6ee8506caacff4a14f9b4
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="replace-in-files"></a>Substituir nos Arquivos

**Substituir nos Arquivos** permite pesquisar o código de um conjunto especificado de arquivos para uma cadeia de caracteres ou expressão e alterar algumas ou todas as correspondências encontradas. As correspondências encontradas e as ações executadas são listadas na janela **Localizar Resultados** selecionada em **Opções de resultado**.

> [!NOTE]
> As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas. Para alterar as configurações, por exemplo, para configurações **Gerais** ou do **Visual C++**, escolha **Ferramentas**, **Importar e exportar configurações** e, em seguida, escolha **Redefinir todas as configurações**.

É possível usar qualquer um dos métodos a seguir para exibir **Substituir nos Arquivos** na janela **Localizar e Substituir**.

## <a name="to-display-replace-in-files"></a>Para exibir Substituir nos Arquivos

1. No menu **Editar**, expanda **Localizar e Substituir**.

1. Escolha **Substituir nos Arquivos**.

   – ou —

Se a janela **Localizar e Substituir** ainda estiver aberta, na barra de ferramentas, escolha **Substituir nos Arquivos**.

## <a name="find-what"></a>Localizar

Para pesquisar uma nova cadeia de caracteres de texto ou expressão, especifique-a na caixa. Para pesquisar qualquer uma das 20 cadeias de caracteres mais pesquisadas recentemente, abra a lista suspensa e escolha a cadeia de caracteres. Escolha o botão **Construtor de Expressões** adjacente se você desejar usar uma ou mais expressões regulares na cadeia de caracteres de pesquisa. Para obter mais informações, consulte [Usando expressões regulares no Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).

> [!NOTE]
> O botão **Construtor de Expressões** só será habilitado se você tiver selecionado **Usar Expressões Regulares** em **Encontrar Opções**.

## <a name="replace-with"></a>Substituir por

Para substituir instâncias da cadeia de caracteres na caixa **Localizar** por outra cadeia de caracteres, digite a cadeia de caracteres de substituição na caixa **Substituir por**. Para excluir instâncias da cadeia de caracteres na caixa **O que localizar**, deixe esse campo em branco. Abra a lista para exibir as 20 cadeias de caracteres que você pesquisou mais recentemente. Escolha o botão **Construtor de Expressões** adjacente se você desejar usar uma ou mais expressões regulares na cadeia de caracteres de substituição. Para obter mais informações, consulte [Usando expressões regulares no Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).

## <a name="look-in"></a>Examinar

A opção escolhida na lista suspensa **Examinar** determina se **Substituir nos Arquivos** pesquisa apenas em arquivos ativos ou em todos os arquivos armazenados em determinadas pastas. Selecione um escopo da pesquisa na lista, digite um caminho de pasta ou clique no botão **Procurar (...)**  para exibir a caixa de diálogo **Escolher Pastas de Pesquisa** e escolha um conjunto de pastas a pesquisar. Também é possível digitar um caminho diretamente na caixa **Examinar**.

> [!NOTE]
> Se a opção **Examinar** selecionada fizer com que você pesquise um arquivo do qual você fez check-out do controle do código-fonte, apenas a versão desse arquivo que tiver sido baixada em seu computador local será pesquisada.

## <a name="find-options"></a>Opções de busca

É possível expandir ou recolher a seção **Localizar opções**. As opções a seguir podem ser marcadas ou desmarcadas:

Diferenciar maiúsculas de minúsculas  
Quando selecionada, as janelas **Localizar Resultados** só exibem instâncias da cadeia de caracteres **Localizar** que coincidam tanto em termos de conteúdo quanto de maiúsculas e minúsculas. Por exemplo, uma pesquisa por "MyObject" com **Coincidir com maiúsculas e minúsculas** selecionado retornará "MyObject", mas não "myobject" nem "MYOBJECT".

Coincidir palavra inteira  
Quando selecionada, as janelas **Localizar Resultados** só exibirão instâncias da cadeia de caracteres **O que localizar** que coincidam em palavras inteiras. Por exemplo, uma pesquisa por "MyObject" retornará "MyObject", mas não "CMyObject" nem "MyObjectC".

Usar Expressões Regulares  
Quando essa caixa de seleção está marcada, é possível usar notações especiais para definir padrões de texto nas caixas de texto **Localizar** ou **Substituir por**. Para obter uma lista dessas notações, consulte [Usando expressões regulares no Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).

Procurar nestes tipos de arquivos  
Essa lista indica os tipos de arquivos a serem pesquisados nos diretórios **Examinar**. Se esse campo for deixado em branco, todos os arquivos nos diretórios **Examinar** serão pesquisados.

Selecione qualquer item na lista para inserir uma cadeia de caracteres de pesquisa pré-configurada que localizará arquivos desses tipos específicos.

## <a name="result-options"></a>Opções de resultado

É possível expandir ou recolher a seção **Opções de resultado**. As opções a seguir podem ser marcadas ou desmarcadas:

Janela Localizar Resultados 1  
Quando selecionada, os resultados da pesquisa atual substituirão o conteúdo da janela **Localizar Resultados 1**. Esta janela é aberta automaticamente para exibir os resultados da pesquisa. Para abrir essa janela manualmente, selecione **Outras Janelas** no menu **Exibir** e escolha **Localizar Resultados 1**.

Janela Localizar Resultados 2  
Quando selecionada, os resultados da pesquisa atual substituirão o conteúdo da janela **Localizar Resultados 2**. Esta janela é aberta automaticamente para exibir os resultados da pesquisa. Para abrir essa janela manualmente, selecione **Outras Janelas** no menu **Exibir** e escolha **Localizar Resultados 2**.

Exibir apenas nomes de arquivos  
Quando essa caixa de seleção estiver marcada, as janelas Localizar Resultados listarão os nomes completos e os caminhos para todos os arquivos que contêm a cadeia de caracteres de pesquisa. No entanto, os resultados não incluirão a linha de código na qual a cadeia de caracteres é exibida. Essa caixa de seleção só está disponível para Localizar em Arquivos.

Manter arquivos modificados abertos após Substituir Tudo  
Quando selecionada, deixa abertos todos os arquivos nos quais foram feitas substituições, portanto, você pode desfazer ou salvar as alterações. Restrições de memória podem limitar o número de arquivos podem permanecer abertos após uma operação de substituição.

> [!CAUTION]
> Você pode usar **Desfazer** somente em arquivos que permanecem abertos para edição. Se essa opção não for selecionada, arquivos que não ainda estiverem abertos para edição permanecerão fechados e nenhuma opção **Desfazer** estará disponível nesses arquivos.

## <a name="see-also"></a>Consulte também

[Localizando e substituindo texto](../ide/finding-and-replacing-text.md)  
[Localizar em Arquivos](../ide/find-in-files.md)  
[Comandos do Visual Studio](../ide/reference/visual-studio-commands.md)