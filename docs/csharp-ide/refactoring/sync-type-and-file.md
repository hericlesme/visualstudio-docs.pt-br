---
title: "Sincronizar o tipo e o nome do arquivo - refatoração (c#) | Microsoft Docs"
ms.custom: 
ms.date: 02/27/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 48172dd7-24a5-4884-8a73-f92497ad6a0d
author: gewarren
ms.author: gewarren
manager: ghogen
dev_langs: CSharp
ms.workload: dotnet
ms.openlocfilehash: 2ec97bfc67735af08e80d7b6e8e67080d5b9af6a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="sync-a-type-to-a-filename-or-a-filename-to-a-type-in-c"></a>Sincronizar um tipo para um nome de arquivo ou um nome de arquivo a um tipo em c# #

<!-- VERSIONLESS -->
**Este recurso está disponível no Visual Studio de 2017 e posterior.  Além disso, os projetos .NET padrão ainda não há suporte para esta refatoração.**

**O que:** permite que você renomear um tipo para coincidir com o nome do arquivo, ou renomear um nome de arquivo para corresponder ao tipo que ele contém.

**Quando:** você tiver renomeado um arquivo ou o tipo e ainda não tiver atualizado o arquivo correspondente ou o tipo a ser correspondido. 

**Motivo:** colocando um tipo em um arquivo com um nome diferente, ou vice-versa, difícil encontrar o que você está procurando.  Renomeando o tipo ou o nome de arquivo, o código se torna mais legível e mais fácil de navegar.

**Como:**

1. Realçar ou coloque o cursor do texto dentro do nome do tipo para sincronizar:

   ![Código realçado](media/synctype_highlight.png)

1. Em seguida, siga um destes procedimentos:
   * **Teclado**
     * Pressione **Ctrl +.** para disparar o **ações rápidas e refatorações** menu e selecione **renomear o arquivo para *TypeName*. CS** de pop-up janela de visualização onde *TypeName* é o nome do tipo selecionado.
     * Pressione **Ctrl +.** para disparar o **ações rápidas e refatorações** menu e selecione **Renomear tipo para _Filename_**  de pop-up janela de visualização onde *Filename* é o nome do arquivo atual.
   * **Mouse**
     * Clique com botão direito do código, selecione o **ações rápidas e refatorações** menu e selecione **renomear o arquivo para *TypeName*. CS** de pop-up janela de visualização onde *TypeName* é o nome do tipo selecionado.
     * Clique com botão direito do código, selecione o **ações rápidas e refatorações** menu e selecione **Renomear tipo para _Filename_**  de pop-up janela de visualização onde  *Nome de arquivo* é o nome do arquivo atual.

   O tipo ou o arquivo será renomeado instantaneamente.  No exemplo a seguir, o arquivo **MyClass.cs** foi renomeada para **MyNewClass.cs** para corresponder ao nome de tipo.

   ![Resultados inline](media/synctype_result.png)

## <a name="see-also"></a>Consulte também  
[Refatoração (C#)](../refactoring-csharp.md)
