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
ms.workload: multiple
ms.openlocfilehash: 741df95afdd7c7e8b6f0ba2de75c1465cd35cc97
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/13/2018
---
# <a name="code-style-preferences"></a>Preferências de estilo de código

As preferências de estilo de código podem ser definidas em seus projetos em C# e do Visual Basic, abrindo a caixa de diálogo **Opções** no menu **Ferramentas**. Selecione **Editor de Texto** > **C#** ou **Básico** > **Estilo do Código** > **Geral**. As opções definidas nessa janela são aplicáveis ao computador local. Cada item da lista mostrará uma visualização da preferência quando selecionado, conforme mostrado abaixo.

![Opções de Estilo de Código](media/code-style-quick-actions-dialog.png)

Para cada item, é possível definir os valores de **Preferência** e a **Severidade** usando as listas suspensas de cada linha. A severidade pode ser definida como **Nenhuma**, **Sugestão**, **Aviso** ou **Erro**. Se você quiser habilitar [Ações Rápidas](../ide/quick-actions.md) para um estilo de código, verifique se a configuração de **Severidade** está definida como algo diferente de **Nenhuma**. O ícone de lâmpada de Ações Rápidas ![Pequeno ícone de lâmpada](media/vs2015_lightbulbsmall.png) será exibido quando um estilo não preferencial for usado, e você poderá escolher uma opção na lista de Ações Rápidas para automaticamente reescrever o código para o estilo preferencial.

As configurações de Estilo de Código para o .NET também podem ser gerenciadas com um arquivo [EditorConfig](../ide/editorconfig-code-style-settings-reference.md). Nesse caso, as configurações no arquivo EditorConfig têm precedência sobre as opções selecionadas na caixa de diálogo **Opções**. É possível usar um arquivo EditorConfig para impor e configurar o estilo de codificação de todo o repositório ou projeto.

## <a name="see-also"></a>Consulte também

[Ações rápidas](../ide/quick-actions.md)  
[Configurações de convenção de codificação do .NET para o EditorConfig](../ide/editorconfig-code-style-settings-reference.md)