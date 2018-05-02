---
title: Definir indicadores de código no Visual Studio
ms.date: 02/23/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- VS.BookmarkWindow
ms.assetid: a752ed5f-5cf9-4bf2-865a-2131ca600ed5
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: edeb4a012d0059f54df29fd74b093cc51ed5e6f1
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="set-bookmarks-in-code"></a>Definir indicadores no código

Você pode usar indicadores para marcar linhas em seu código para que você possa retornar rapidamente para um local específico ou alternar entre locais. Os comandos de indicador e os ícones estão disponíveis em dois locais: na **Janela de Indicadores** (**Exibição** > **Janela de Indicadores**) e na barra de ferramentas do editor de texto.

![Barra de ferramentas de indicador](media/bookmark-toolbar.png)

![Janela de Indicadores](media/bookmark-window.png)

## <a name="manage-bookmarks"></a>Gerenciar indicadores

Para adicionar um indicador, coloque o cursor na linha que você deseja marcar. Escolha o botão **Ativar/desativar um indicador** ou pressione **Ctrl**+**K**, **Ctrl**+**K**. Isso adiciona o indicador. Se você escolher o botão **Ativar/desativar um indicador** (ou pressionar **Ctrl**+**K**, **Ctrl**+**K**) novamente, o indicador será removido.

Para saber rapidamente para que um indicador específico é, você pode renomeá-lo na **Janela de Indicadores** do menu de contexto ou ao clicar com o botão direito do mouse. Você pode excluir indicadores escolhendo no botão **Excluir** na janela de indicadores.

> [!IMPORTANT]
> O indicador é definido como o número de linha e não como o código. Se você modificar o código, o indicador será mantido no número de linha e não será movido com o código.

Você pode navegar entre marcadores usando os botões **Próximo indicador** e **Indicador anterior** na janela de indicadores.

Você pode organizar indicadores em pastas virtuais escolhendo **Nova Pasta** na janela de indicadores e arrastando os indicadores selecionados para a nova pasta.

Você pode desligar indicadores (sem removê-los) escolhendo o botão **Desabilitar Todos os Indicadores** na janela de indicadores. Você pode reabilitá-los escolhendo o mesmo botão (que agora é chamado de **Habilitar Todos os Indicadores**).

## <a name="see-also"></a>Consulte também

- [Escrever o código no editor](../ide/writing-code-in-the-code-and-text-editor.md)