---
title: "Estilos de Código e Ações Rápidas | Microsoft Docs"
ms.custom: 
ms.date: 03/10/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.devlang: csharp
ms.assetid: 25bb9d99-aeff-4053-925d-2177f5e79574
author: gewarren
ms.author: gewarren
manager: ghogen
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.CSharp.Code_Style.General
- VS.ToolsOptionsPages.Text_Editor.Basic.Code_Style.General
ms.openlocfilehash: d42bb9165748b7282aa42f062b545add62ad1c93
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="code-styles-and-quick-actions"></a>Estilos de Código e Ações Rápidas
As preferências de estilo de código podem ser definidas para os projetos do C# e do Visual Basic abrindo a janela **Ferramentas > Opções** e, em seguida, selecionando **Editor de Texto > C#/Basic > Estilo de Código > Geral**.  As opções definidas nessa janela são aplicáveis ao computador local.  Cada item da lista mostrará uma visualização da preferência quando selecionado, conforme mostrado abaixo.

![Opções de Estilo de Código](media/code-style-quick-actions-dialog.png)

Para cada item, é possível definir a **Preferência** e a **Gravidade** usando as listas suspensas de cada linha.  A gravidade pode ser definida como **Nenhuma**, **Sugestão**, **Aviso** ou **Erro** e o Visual Studio terá o comportamento apropriado.  Se desejar usar as [Ações Rápidas](quick-actions.md) com esses estilos de código para reescrever o código automaticamente no estilo preferencial, verifique se a configuração está definida com uma opção diferente de **Nenhum**, para que o ícone de lâmpada ![Ícone de lâmpada pequeno](media/vs2015_lightbulbsmall.png "VS2017_LightBulbSmall") seja exibido quando os estilos não preferenciais forem usados.  Em seguida, essas preferências poderão ser aplicadas clicando no ícone de Lâmpada ou pressionando **Ctrl + .** quando o cursor estiver sobre a linha de código apropriada.

As configurações de Estilo de Código para o .NET também podem ser gerenciadas com um arquivo [EditorConfig](editorconfig-code-style-settings-reference.md).  Nesse caso, as configurações selecionadas na janela Opções serão as configurações de fallback, com o arquivo EditorConfig tendo precedência.  É possível usar esse arquivo para impor e configurar o estilo de codificação de todo o repositório ou toda a equipe.

## <a name="see-also"></a>Consulte também
* [Ações rápidas](quick-actions.md)