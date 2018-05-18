---
title: Comentários da Tarefa
description: Adicionando comentários de tarefa ao seu código
author: asb3993
ms.author: amburns
ms.date: 05/06/2018
ms.assetid: 562DCB46-D8FA-4DC4-AAEA-F274448C4CD2
ms.openlocfilehash: ca74c6429ed721a6c11bd71d024668cc695274e9
ms.sourcegitcommit: 33c954fbc8e05f7ba54bfa2c0d1bc1f9bbc68876
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/08/2018
---
# <a name="task-comments"></a>Comentários da Tarefa

Ao escrever o código, é uma prática padrão comentar explicitamente código incompleto, questionável ou soluções alternativas rápidas com avisos. Os tokens de sinal padrão fornecidos pelo Visual Studio para Mac são TODO, HACK, FIXME e UNDONE. Os tokens personalizados podem ser definidos em **Visual Studio > Preferências... > Ambiente > Tarefas**, conforme ilustrado na imagem a seguir:

 ![Preferências da lista de tarefas](media/source-editor-image10.png)

Para adicionar um novo comentário de tarefa, adicione um comentário que inclui a palavra-chave da tarefa. Por exemplo:

```
//TODO: Finish this for all properties.
```

O Visual Studio para Mac chama a atenção para esses marcadores realçando-os no painel da Lista de Tarefas, que pode ser exibido navegando para **Exibir > Painéis > Tarefa**:

![Painel de lista de tarefas](media/source-editor-image11.png)