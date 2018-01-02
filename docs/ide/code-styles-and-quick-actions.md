---
title: "Preferências de estilo de código do Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 03/10/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
author: gewarren
ms.author: gewarren
manager: ghogen
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.CSharp.Code_Style.General
- VS.ToolsOptionsPages.Text_Editor.Basic.Code_Style.General
ms.openlocfilehash: 24470f4fdb1a75d6ebd2743b2ade72e6195842b4
ms.sourcegitcommit: ebe9fb5eda724936f7a059d35d987c29dffdb50d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/07/2017
---
# <a name="code-style-preferences"></a>Preferências de estilo de código

As preferências de estilo de código podem ser definidas em seus projetos em C# e do Visual Basic, abrindo a caixa de diálogo **Opções** no menu **Ferramentas**. Selecione **Editor de Texto**, **C#** ou **Básico**, **Estilo do Código**, **Geral**. As opções definidas nessa janela são aplicáveis ao computador local. Cada item da lista mostrará uma visualização da preferência quando selecionado, conforme mostrado abaixo.

![Opções de Estilo de Código](media/code-style-quick-actions-dialog.png)

Para cada item, é possível definir a **Preferência** e a **Gravidade** usando as listas suspensas de cada linha. A gravidade pode ser definida como **Nenhuma**, **Sugestão**, **Aviso** ou **Erro** e o Visual Studio terá o comportamento apropriado. Se desejar usar as [Ações Rápidas](quick-actions.md) com esses estilos de código para reescrever o código automaticamente no estilo preferencial, verifique se a configuração está definida com uma opção diferente de **Nenhum**, para que o ícone de lâmpada ![Ícone de lâmpada pequeno](media/vs2015_lightbulbsmall.png "VS2017_LightBulbSmall") seja exibido quando os estilos não preferenciais forem usados. Em seguida, essas preferências poderão ser aplicadas clicando no ícone de Lâmpada ou pressionando **Ctrl + .** quando o cursor estiver sobre a linha de código apropriada.

As configurações de Estilo de Código para o .NET também podem ser gerenciadas com um arquivo [EditorConfig](../ide/editorconfig-code-style-settings-reference.md). Nesse caso, as configurações no arquivo EditorConfig têm precedência sobre as opções selecionadas na caixa de diálogo **Opções**. É possível usar um arquivo EditorConfig para impor e configurar o estilo de codificação de todo o repositório ou projeto.

## <a name="see-also"></a>Consulte também

[Ações rápidas](quick-actions.md)  
[Configurações de convenção de codificação do .NET para o EditorConfig](../ide/editorconfig-code-style-settings-reference.md)