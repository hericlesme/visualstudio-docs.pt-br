---
title: "Opções, Editor de Texto, C#, Formatação | Microsoft Docs"
ms.date: 02/09/2018
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.topic: article
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.Spacing
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.NewLines
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.Indentation
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.Wrapping
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.General
helpviewer_keywords:
- formatting options [C#]
- Text editor Options dialog box, formatting
ms.assetid: 5a7bb668-1d0c-4ffe-9508-24592813162e
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- dotnet
ms.openlocfilehash: 639082683ad0b65b294307df0740aa4d9c6069d0
ms.sourcegitcommit: 238cd48787391aa0ed1eb684f3f04e80f7958705
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/12/2018
---
# <a name="options-text-editor-c-formatting"></a>Opções, editor de texto, C#, formatação

Use a página de opções **Formatação** para definir opções para formatar o código no Editor de Código. Para acessar essa página de opções, escolha **Ferramentas** > **Opções** e, em seguida, **Editor de Texto** > **C#** > **Estilo de Código** > **Formatação**.

> [!NOTE]
> As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas. Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**. Para obter mais informações, confira [Personalizar o IDE do Visual Studio](../../ide/personalizing-the-visual-studio-ide.md).

## <a name="general-settings"></a>Configurações gerais

As configurações gerais afetam como o Editor de Código aplica as opções de formatação ao código.

## <a name="uielement-list"></a>Lista UIElement

|Rotular|Descrição|
|-----------|-----------------|
|**Formatar automaticamente ao digitar**|Quando estiver desmarcada, as opções **formatar instrução em ;** e **formatar bloco em }** estarão desabilitadas.|
|**Formatar instrução automaticamente em ;**|Quando selecionada, formata as instruções na conclusão de acordo com as opções de formatação selecionadas para o editor.|
|**Formatar bloco automaticamente em }**|Quando selecionada, formata blocos de código de acordo com as opções de formatação selecionadas para o editor assim que você conclui o bloco de código.|
|**Formatar automaticamente na devolução**|Quando selecionada, formata o texto quando **Enter** é pressionado, de acordo com as opções de formatação selecionadas para o editor.|
|**Formatar automaticamente ao colar**|Quando selecionada, formata o texto que é colado no editor de acordo com as opções de formatação selecionadas para o editor.|

## <a name="preview-window"></a>Janela de visualização

Os painéis de opções **Recuo**, **Novas Linhas**, **Espaçamento** e **Disposição** exibem uma janela de visualização. A janela de visualização mostra o efeito de cada opção. Para usar a janela de visualização, selecione uma opção de formatação. A janela de visualização mostra um exemplo da opção selecionada. Quando você altera uma configuração selecionando um botão de opção ou marcando uma caixa de seleção, a janela de visualização é atualizada para mostrar o efeito da nova configuração.

## <a name="remarks"></a>Comentários

As opções de recuo nas páginas **Guias** de cada linguagem determinam apenas onde o Editor de Códigos coloca o cursor quando você pressiona **Enter** no final de uma linha. As opções de recuo em **Formatação** são aplicadas quando o código é formatado automaticamente, por exemplo, quando você cola um código no arquivo e **Formatar automaticamente ao colar** está selecionada e quando o bloco que está sendo formatado é digitado manualmente.

## <a name="see-also"></a>Consulte também

[Caixa de diálogo Geral, Ambiente, Opções](../../ide/reference/general-environment-options-dialog-box.md)
