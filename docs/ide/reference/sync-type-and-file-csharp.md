---
title: Renomear um nome de arquivo para corresponder a um tipo em C# no Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 02/27/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: ghogen
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: ada7044ebb6718dc0380b387a130ea7b2334e443
ms.sourcegitcommit: b01406355e3b97547b7cbf8ce3960f101b165cec
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/06/2018
---
# <a name="sync-a-type-to-a-filename-or-a-filename-to-a-type-in-c"></a>Sincronizar um tipo para um nome de arquivo, ou um nome de arquivo para um tipo, em C# #

<!-- VERSIONLESS -->
**Esse recurso está disponível no Visual Studio 2017 e posterior.  Além disso, os projetos do .NET Standard ainda não têm suporte para esta refatoração.**

**O quê:** permite que você renomeie um tipo para corresponder ao nome do arquivo, ou renomeie um nome de arquivo para corresponder ao tipo que ele contém.

**Quando:** você renomeou um arquivo ou tipo e ainda não atualizou o arquivo correspondente ou tipo a ser correspondido. 

**Por quê:** se você colocar um tipo em um arquivo com um nome diferente, ou vice-versa, será difícil encontrar o que está procurando.  Se você renomear o tipo ou nome de arquivo, o código se tornará mais legível e mais fácil de navegar.

**Como:**

1. realce ou coloque o cursor do texto dentro do nome do tipo para sincronizar:

   ![Código realçado](media/synctype-highlight-cs.png)

1. Depois, siga um destes procedimentos:
   * **Teclado**
     * Pressione **Ctrl +.** para disparar o menu **Ações Rápidas e Refatorações** e selecionar **Renomear o arquivo para *TypeName*.cs** no pop-up da janela Visualização, onde *TypeName* é o nome do tipo selecionado.
     * Pressione **Ctrl +.** para disparar o menu **Ações Rápidas e Refatorações** e selecione **Renomear tipo para _Filename_** no pop-up da janela Visualização, onde *Filename* é o nome do arquivo atual.
   * **Mouse**
     * Clique com o botão direito do mouse no código, selecione o menu **Ações Rápidas e Refatorações** e selecione **Renomear o arquivo para *TypeName*.cs** no pop-up da janela Visualização, onde *TypeName* é o nome do tipo selecionado.
     * Clique com o botão direito do mouse no código, selecione o menu **Ações Rápidas e Refatorações** e selecione **Renomear o tipo para _Filename_** no pop-up da janela Visualização, onde *Filename* é o nome do arquivo atual.

   O tipo ou arquivo será renomeado instantaneamente.  No exemplo a seguir, o arquivo **MyClass.cs** foi renomeado para **MyNewClass.cs** para corresponder ao nome do tipo.

   ![Resultado embutido](media/synctype-result-cs.png)

## <a name="see-also"></a>Consulte também

[Refatoração](../refactoring-in-visual-studio.md)
