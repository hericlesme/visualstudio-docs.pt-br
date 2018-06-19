---
title: Usar o sumário do Help Viewer do Visual Studio
ms.date: 11/02/2017
ms.prod: visual-studio-dev15
ms.technology: vs-help-viewer
ms.topic: conceptual
f1_keywords:
- hv_contents
helpviewer_keywords:
- Help Viewer, table of contents filtering
- Help Viewer, Contents tab
- Contents tab [Help Viewer]
- table of contents filtering [Help Viewer]
ms.assetid: 8b98464d-2b05-4710-ad68-5647e78c6b7b
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6e7d9ae19cb2a37c6fbf6595a7f3a39895d22190
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31945747"
---
# <a name="how-to-find-topics-in-the-table-of-contents"></a>Como localizar tópicos no sumário

Na guia **Sumário**, você pode usar o sumário para localizar informações. O sumário é uma lista expansível que contém todos os tópicos nos livros instalados. Para obter informações de acessibilidade sobre como navegar pelo sumário, consulte [Teclas de atalho (Visualizador da Ajuda)](../ide/shortcut-keys-help-viewer.md).

> [!IMPORTANT]
> O escopo dos tópicos disponíveis no sumário depende do filtro selecionado.

## <a name="filter-the-toc"></a>Filtrar o sumário

Você pode filtrar o sumário para restringir o escopo dos tópicos que aparecem na guia **Sumário**. Títulos aparecem na lista somente se contiverem a raiz do termo que você especificar. Por exemplo, se você especificar "solucionar" como filtro, somente títulos que contiverem "solucionar" ou "solucionar problemas" aparecerão. Nós cujos títulos não contiverem o termo serão recolhidos para um único nó com um sinal de reticências (**...**).

1.  Escolha a guia **Sumário**.

2.  Na caixa de texto **Filtrar Conteúdo**, digite um termo.

> [!NOTE]
> Se o filtro demorar muito para ser executado, você pode exibir resultados mais rapidamente usando o operador de pesquisa avançada `title:`.

## <a name="synchronize-a-topic-with-the-toc"></a>Sincronizar um tópico com o sumário

Se tiver aberto um tópico usando os recursos de pesquisa de texto completo ou o índice, você pode determinar onde este tópico está no sumário sincronizando o sumário com a janela do tópico.

1.  Exibir um tópico.

2.  Clique no botão **Mostrar Tópico no Conteúdo** na barra de ferramentas ou pressione **Ctrl**+**S**.

     A guia **Sumário** é aberta e exibe o local do tópico no Sumário.

## <a name="see-also"></a>Consulte também

- [Como localizar tópicos no índice](../ide/how-to-find-topics-in-the-index.md)
- [Como pesquisar tópicos](../ide/how-to-search-for-topics.md)
- [Microsoft Help Viewer](../ide/microsoft-help-viewer.md)