---
title: Preferências de estilo de código do Visual Studio
ms.date: 03/10/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.CSharp.Code_Style.General
- VS.ToolsOptionsPages.Text_Editor.Basic.Code_Style.General
ms.workload:
- multiple
ms.openlocfilehash: 6dd046fa8a01cde7abdc33484da3ff8227eda966
ms.sourcegitcommit: 046a9adc5fa6d6d05157204f5fd1a291d89760b7
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/11/2018
ms.locfileid: "34063678"
---
# <a name="code-style-preferences"></a>Preferências de estilo de código

As preferências de estilo de código podem ser definidas em seus projetos em C# e do Visual Basic, abrindo a caixa de diálogo **Opções** no menu **Ferramentas**. Selecione **Editor de Texto** > **C#** ou **Básico** > **Estilo do Código** > **Geral**. As opções definidas nessa janela são aplicáveis ao computador local.

Cada item na lista mostra uma versão prévia da preferência quando selecionada:

![Opções de estilo de código](media/code-style-quick-actions-dialog.png)

## <a name="preference-and-severity"></a>Preferência e gravidade

Para cada item, é possível definir os valores **Preferência** e **Severidade** usando as listas suspensas de cada linha. A severidade pode ser definida como **Nenhuma**, **Sugestão**, **Aviso** ou **Erro**. Se você quiser habilitar [Ações Rápidas](../ide/quick-actions.md) para um estilo de código, verifique se a configuração de **Severidade** está definida como algo diferente de **Nenhuma**. O ícone de lâmpada de Ações Rápidas ![Pequeno ícone de lâmpada](media/vs2015_lightbulbsmall.png) será exibido quando um estilo não preferencial for usado, e você poderá escolher uma opção na lista de Ações Rápidas para automaticamente reescrever o código para o estilo preferencial.

## <a name="editorconfig-files"></a>Arquivos EditorConfig

As configurações de estilo de código para o .NET também podem ser gerenciadas com um arquivo [EditorConfig](../ide/editorconfig-code-style-settings-reference.md). As configurações no arquivo EditorConfig têm precedência sobre as opções selecionadas na caixa de diálogo **Opções**. É possível usar um arquivo EditorConfig para impor e configurar o estilo de codificação de todo o repositório ou projeto.

## <a name="see-also"></a>Consulte também

- [Ações rápidas](../ide/quick-actions.md)
- [Configurações de convenção de codificação do .NET para o EditorConfig](../ide/editorconfig-code-style-settings-reference.md)