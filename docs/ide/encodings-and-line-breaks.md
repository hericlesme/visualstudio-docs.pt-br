---
title: "Caracteres de quebra de linha e codificação do Studio Visual | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.Encoding
helpviewer_keywords:
- line breaks
- encoding
- Visual Studio, encoding
- editors, line breaks
- line break characters
- Visual Studio, line break characters
ms.assetid: 8f9b3ffc-7b8d-44f4-87cb-dc29105be12d
caps.latest.revision: 
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 8a472a09a4d4d67f59d7879d03b466932d1445e6
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="encodings-and-line-breaks"></a>Codificações e quebras de linha
Os seguintes caracteres são interpretados como quebras de linha no Visual Studio:  
  
-   CR LF: retorno de carro + alimentação de linha, caracteres Unicode 000D + 000A  
  
-   LF: alimentação de linha, caractere Unicode 000A  
  
-   NEL: próxima linha, caractere Unicode 0085  
  
-   LS: separador de linha, caractere Unicode 2028  
  
-   PS: separador de parágrafo, caractere Unicode 2029  
  
O texto copiado de outros aplicativos mantém a codificação original e os caracteres de quebra de linha. Por exemplo, quando você copia texto do Bloco de notas e o cola em um arquivo de texto no Visual Studio, o texto tem as mesmas configurações que ele tinha no Bloco de notas.  
  
Ao abrir um arquivo que tem caracteres de quebra de linha diferentes, talvez você veja uma caixa de diálogo que pergunta se os caracteres de quebra de linha inconsistentes devem ser normalizados e quais os tipo de quebras de linha você deseja escolher.

Você pode usar a caixa de diálogo **Arquivo**, **Opções Avançadas de Salvamento** para determinar o tipo de caracteres de quebra de linha que você deseja. Também é possível alterar a codificação de um arquivo com as mesmas configurações.

![Caixa de diálogo Opções Avançadas de Salvamento](media/line_endings.png)
  
> [!NOTE]
>  Se você não vir **Opções Avançadas de Salvamento** no menu **Arquivo**, você poderá adicioná-la. Escolha **Ferramentas**, **Personalizar...**  e, em seguida, escolha a guia **Comandos**. No lista suspensa da **Barra de menus**, escolha **Arquivo** e, em seguida, escolha o botão **Adicionar Comando...**. Na caixa de diálogo **Adicionar Comando**, em **Categorias**, escolha **Arquivo** e, em seguida, na lista **Comandos**, escolha **Opções Avançadas de Salvamento...**. Escolha **OK** e, em seguida, escolha o botão **Mover para Baixo** para mover o comando para qualquer local no menu. Escolha **Fechar** para fechar a caixa de diálogo **Personalizar**. Para obter mais informações, consulte [Personalizar menus e barras de ferramentas](../ide/how-to-customize-menus-and-toolbars-in-visual-studio.md#customizing_menu).

Como alternativa, você pode acessar a caixa de diálogo **Opções Avançadas de Salvamento**, escolhendo **Arquivo**, **Salvar \<arquivo\> Como...**. Na caixa de diálogo **Salvar Arquivo Como**, escolha o triângulo de lista suspensa ao lado do botão **Salvar** e escolha **Salvar com codificação...**.

## <a name="see-also"></a>Consulte também
[Escrevendo código no editor](../ide/writing-code-in-the-code-and-text-editor.md)