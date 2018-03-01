---
title: "Configurando identificadores no código | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.BookmarkWindow
ms.assetid: a752ed5f-5cf9-4bf2-865a-2131ca600ed5
caps.latest.revision: 
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 8bf8367b3e4f0d20db435e16f9843e6d431c068b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="setting-bookmarks-in-code"></a>Definindo identificadores no código

Você pode usar indicadores para marcar linhas em seu código para que você possa retornar rapidamente para um local específico e alternar entre locais. Os comandos de indicador e os ícones estão disponíveis em dois locais: na janela de indicadores (**Exibição** > **Janela de Indicadores**) e na barra de ferramentas do editor de texto.

## <a name="managing-bookmarks"></a>Gerenciando indicadores

Para adicionar um indicador, coloque o cursor na linha que você deseja marcar. Clique no botão de **Alternância** ou pressione CTRL + K. Isso adiciona o indicador. Se você clicar no botão de Alternância (ou pressionar CTRL + K) novamente, o indicador será removido. Você também pode excluir indicadores clicando no botão **Excluir** na janela de indicadores.

> [!IMPORTANT]
> O indicador é definido como o número de linha e não como o código. Se você modificar o código, o indicador será mantido no número de linha e não será movido com o código.

Você pode navegar entre marcadores usando os botões **Próximo Indicador** e **Indicador Anterior** na janela de indicadores.

Você pode organizar indicadores em pastas virtuais, clicando em **Nova Pasta** na janela de indicadores e arrastando os indicadores selecionados para a nova pasta.

Você pode desligar indicadores (sem removê-los) clicando no botão **Desabilitar Todos os Indicadores** na janela de indicadores. Você pode reabilitá-los clicando no mesmo botão (que agora é chamado de **Habilitar Todos os Indicadores**).

## <a name="see-also"></a>Consulte também

[Gravando código no editor](../ide/writing-code-in-the-code-and-text-editor.md)