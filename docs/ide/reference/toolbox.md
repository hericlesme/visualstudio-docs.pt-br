---
title: Janela Caixa de Ferramentas do Visual Studio
ms.date: 01/18/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vs.toolbox.general
- vs.toolbox
helpviewer_keywords:
- Toolbox [Visual Studio]
- custom controls [Visual Studio]
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3f296349a6dfda80ff402b1ede0f1da591f6caa9
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="toolbox"></a>Caixa de Ferramentas

A janela **Caixa de Ferramentas** exibe os controles que você pode adicionar a projetos do Visual Studio. Para abrir a Caixa de Ferramentas, escolha **Caixa de Ferramentas** no menu **Exibir**.

![Janela caixa de ferramentas](media/toolbox.png)

Você pode arrastar e soltar diferentes controles na superfície do designer que você está usando, redimensionar e posicionar os controles.

A Caixa de Ferramentas aparece com as exibições de designer, como a exibição de designer de um arquivo XAML. A Caixa de Ferramentas exibe apenas os controles que podem ser usados ​​no designer atual. Você pode pesquisar na Caixa de Ferramentas para filtrar ainda mais os itens que aparecem.

> [!NOTE]
> Para alguns tipos de projeto, talvez a Caixa de Ferramentas não mostre todos os itens.

A versão do .NET Framework direcionada pelo seu projeto também afeta o conjunto de controles visíveis na Caixa de Ferramentas. Você pode definir seu projeto para direcionar para uma versão diferente do .NET Framework nas páginas de propriedades do projeto. Selecione o nó do projeto no **Gerenciador de Soluções** e na barra de menus, escolha **Projeto** > **\<projeto\> Propriedades**. Na guia **Aplicativo**, use o menu suspenso **Estrutura de destino**.

## <a name="managing-the-toolbox-window-and-its-controls"></a>Gerenciar a janela Caixa de Ferramentas e seus controles

Por padrão, a Caixa de Ferramentas fica recolhida no lado esquerdo do IDE do Visual Studio e aparece quando o cursor é movido sobre ela. É possível fixar a Caixa de Ferramentas (clicando no ícone **Fixar** na barra de ferramentas dela) para que ela permaneça aberta quando você move o cursor. Você também pode desencaixar a janela da Caixa de Ferramentas e arrastá-la para qualquer lugar na tela. Você pode encaixar, desencaixar e ocultar a Caixa de Ferramentas, clicando com o botão direito na barra de ferramentas dela e selecionando uma das opções.

Você pode reorganizar os itens em uma guia de Caixa de Ferramentas ou adicionar guias e itens personalizados usando os seguintes comandos no menu de contexto:

- **Renomear Item** – renomeia o item selecionado.

- **Mostrar Todos** – mostra todos os controles possíveis (e não apenas os que se aplicam ao designer atual).

- **Exibição de Lista** – mostra os controles em uma lista vertical. Se todas as opções estiverem desmarcadas, os controles aparecem na horizontal.

- **Escolher Itens** – abre a caixa de diálogo **Escolher Itens da Caixa de Ferramentas** para que você possa especificar os itens que aparecem na **Caixa de Ferramentas**. Você pode mostrar ou ocultar um item, marcando ou desmarcando a caixa de seleção.

- **Classificar itens em ordem alfabética** – classifica os itens por nome.

- **Redefinir barra de ferramentas**: restaura as configurações e itens padrão da Caixa de Ferramentas.

- **Adicionar Guia**: adiciona uma nova guia da Caixa de Ferramentas.

- **Mover para Cima** – move o item selecionado para cima.

- **Mover para Baixo** – move o item selecionado para baixo.

## <a name="creating-and-distributing-custom-toolbox-controls"></a>Criar e distribuir controles personalizados da Caixa de Ferramentas

Você pode criar controles personalizados da Caixa de Ferramentas, começando com um modelo de projeto baseado no [Windows Presentation Foundation](../../extensibility/creating-a-wpf-toolbox-control.md) ou no [Windows Forms](../../extensibility/creating-a-windows-forms-toolbox-control.md). Depois, você pode distribuir o controle personalizado para seus colegas de equipe ou publicá-lo na Web usando o [Instalador de Controles da Caixa de Ferramentas](http://download.microsoft.com/download/8/3/6/836657BD-9CCB-4ED4-B9D2-FB769473B284/TCI_whitepaper.docx).

## <a name="help-on-toolbox-tabs"></a>Ajuda sobre as guias da Caixa de Ferramentas

Os tópicos a seguir fornecem mais informações sobre algumas das guias disponíveis na **Caixa de Ferramentas**.

- [Caixa de Ferramentas, Guia Dados](../../ide/reference/toolbox-data-tab.md)

- [Caixa de Ferramentas, Guia Componentes](../../ide/reference/toolbox-components-tab.md)

- [Caixa de Ferramentas, Guia HTML](../../ide/reference/toolbox-html-tab.md)
