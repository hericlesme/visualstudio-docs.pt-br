---
title: Usando a lista de tarefas | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
f1_keywords:
- TaskListWindow
- VS.TaskList
- tasklist
helpviewer_keywords:
- task list
- Visual Studio, task list
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ef9b3904ce06c498518d55b0d62b8e9393c75239
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="using-the-task-list"></a>Usando a lista de tarefas

Use a **Lista de Tarefas** para rastrear comentários de código que usam tokens, como `TODO` e `HACK`, ou tokens personalizados, e para gerenciar atalhos que levarão você diretamente a um local predefinido no código. Clique no item na lista para ir até seu local no código-fonte.

## <a name="the-task-list-window"></a>A janela Lista de Tarefas

Quando a **Lista de Tarefas** é aberta, ela aparece na parte inferior da janela do aplicativo.

### <a name="to-open-the-task-list"></a>Para abrir a Lista de Tarefas

- No menu **Exibir**, escolha **Lista de Tarefas** (Teclado: Ctrl+\\,T).

    ![Janela Lista de Tarefas](../ide/media/vs2015_task_list.png "vs2015_task_list")

### <a name="to-change-the-sort-order-of-the-list"></a>Para alterar a ordem de classificação da lista

- Clique no cabeçalho de qualquer coluna. Para refinar ainda mais os resultados da pesquisa, pressione Shift e clique em um segundo cabeçalho de coluna.

     Se preferir, no menu de atalho, escolha **Classificar por** e escolha um cabeçalho. Para refinar ainda mais os resultados da pesquisa, pressione Shift e escolha um segundo cabeçalho.

### <a name="to-show-or-hide-columns"></a>Para mostrar ou ocultar colunas

- No menu de atalho, escolha **Mostrar Colunas**. Escolha as colunas que você deseja mostrar ou ocultar.

### <a name="to-change-the-order-of-the-columns"></a>Para alterar a ordem das colunas

- Arraste o cabeçalho de qualquer coluna para o local desejado.

## <a name="user-tasks"></a>Tarefas do usuário

O recurso de tarefa do usuário foi removido desde o Visual Studio 2015. Quando você abre uma solução que tem dados de tarefa de usuário do Visual Studio 2013 e anteriores, os dados de tarefa do usuário em seu arquivo .suo não serão afetados, mas as tarefas do usuário não serão exibidas na lista de tarefas.

Se você quiser continuar a acessar e atualizar os dados de tarefa do usuário, abra o projeto no Visual Studio 2013 e copie o conteúdo de quaisquer tarefas do usuário para sua ferramenta de gerenciamento de projeto preferida (como o Team Foundation Server).

## <a name="tokens-and-comments"></a>Tokens e comentários

Um comentário no código precedido por um marcador de comentário e um token predefinido também será exibido na janela **Lista de Tarefas**. Por exemplo, o seguinte comentário do C# tem três partes distintas:

- O marcador de comentário (`//`)

- O token, por exemplo (`TODO`)

- O comentário (o restante do texto)

```csharp
// TODO: Load state from previously suspended application
```

Uma vez que `TODO` é um token pré-definido, esse comentário aparece como uma tarefa `TODO` na lista.

###  <a name="customTokens"></a> Tokens personalizados

Por padrão, o Visual Studio inclui os seguintes tokens: HACK, TODO, UNDONE, NOTE. Eles não diferenciam maiúsculas de minúsculas.

Também é possível criar seus próprios tokens personalizados.

#### <a name="to-create-a-custom-token"></a>Para criar um token personalizado

1. No menu **Ferramentas**, escolha **Opções**.

2. Abra a pasta **Ambiente** e escolha **Lista de Tarefas**.

     A [página de opções da lista de tarefas](../ide/reference/task-list-environment-options-dialog-box.md) é exibida.

     ![Lista de tarefas do Visual Studio](../ide/media/vs2015_task_list_options.png "vs2015_task_list_options")

3. Na categoria **Tokens**, na caixa de texto **Nome**, insira o nome do seu token, por exemplo, “BUG”.

4. Na lista suspensa **Prioridade**, escolha uma prioridade padrão para o novo token. Escolha o botão **Adicionar**.

###  <a name="cppComments"></a> Comentários TODO em C++

Por padrão, os comentários TODO em C++ são exibidos na janela **Lista de Tarefas**. Você pode alterar esse comportamento.

#### <a name="to-turn-off-c-todo-comments"></a>Para desligar os comentários TODO em C++

No menu **Ferramentas**, selecione **Opções** > **Editor de Texto** > **C/C++** > **Exibir** > **Enumerar Tarefas de Comentário** e defina o valor como false.

## <a name="shortcuts"></a>Atalhos

Um *atalho* é um indicador no código que é controlado na **Lista de Tarefas**; ele tem um ícone diferente de um indicador normal. Clique duas vezes no atalho na **Lista de Tarefas** para ir até o local correspondente no código.

![Ícone de atalho de lista de tarefas do Visual Studio](../ide/media/vs2015_task_list_bookmark.png "vs2015_task_list_bookmark")

### <a name="to-create-a-shortcut"></a>Para criar um atalho

Para criar um atalho, insira o ponteiro no código no local em que deseja colocar um atalho. Escolha **Editar** > **Indicadores** > **Adicionar Atalho da Lista de Tarefas** ou pressione **Ctrl** + **K**, **Ctrl** + **H**.

Para navegar pelos atalhos no código, escolha um atalho na lista e escolha **Próxima Tarefa** ou **Tarefa Anterior** no menu de atalho.

## <a name="see-also"></a>Consulte também

[Caixa de diálogo Lista de Tarefas, Ambiente, Opções](../ide/reference/task-list-environment-options-dialog-box.md)