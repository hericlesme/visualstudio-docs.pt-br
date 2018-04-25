---
title: Refatoração Extrair uma interface no Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 01/26/2018
ms.technology: vs-ide-general
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: douge
f1_keywords:
- vs.csharp.refactoring.extractinterface
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 7abdc017c4d57e17685671539a4b053e6241b424
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="extract-an-interface-refactoring"></a>Refatoração Extrair uma interface

Esta refatoração aplica-se a:

- C#

- Visual Basic

**O quê:** permite que você crie uma interface usando membros existentes de uma classe, struct ou interface.

**Quando:** você tem várias classes, structs ou interfaces com métodos que podem ser comuns e usados por outras classes, structs ou interfaces.

**Por quê:** as interfaces são ótimos constructos para designs orientados a objetos. Imagine ter classes para vários animais (gato, cachorro, pássaro) que podem ter métodos comuns, como comer, beber, dormir. Usar uma interface como IAnimal permitiria que cachorro, gato e pássaro tivessem uma "assinatura" comum para esses métodos.

## <a name="how-to"></a>Como fazer

1. realce o nome da classe para executar a ação ou simplesmente coloque o cursor do texto em algum lugar no nome da classe.

   - C#:

    ![Código realçado – C#](media/extractinterface-highlight-cs.png)

   - Visual Basic:

    ![Código realçado – Visual Basic](media/extractinterface-highlight-vb.png)

1. Depois, siga um destes procedimentos:

   - **Teclado**
     - Pressione **Ctrl+R**, em seguida, **Ctrl+I**. (Observe que o atalho de teclado pode ser diferente com base no perfil selecionado.)
     - Pressione **Ctrl**+**.** para disparar o menu **Ações Rápidas e Refatorações** e selecionar **Extrair Interface** no pop-up da janela Visualização.
   - **Mouse**
     - Selecione **Editar > Refatorar > Extrair Interface**.
     - Clique com o botão direito do mouse no nome da classe, selecione o menu **Ações Rápidas e Refatorações** e selecione **Extrair Interface** no pop-up da janela Visualização.

1. Na caixa de diálogo **Extrair Interface** que é exibida, insira as informações solicitadas:

   ![Extrair Interface](media/extractinterface-dialog-cs.png)

   | Campo | Descrição |
   | --- | --- |
   | **Nome da nova interface** | O nome da interface a ser criada. O padrão é I*ClassName*, onde *ClassName* é o nome da classe selecionada acima. |
   | **Nome do novo arquivo** | O nome do arquivo que será gerado com a interface. Como acontece com o nome da interface, o padrão é I*ClassName*, onde *ClassName* é o nome da classe selecionada acima. |
   | **Selecionar membros públicos para formar a interface** | Os itens a serem extraídos para a interface. Você pode selecionar quantos desejar. |

1. Escolha **OK**.

   A interface foi criada no arquivo com o nome especificado. Além disso, a classe que você selecionou implementa essa interface.

   - C#:

    ![Classe resultante – C#](media/extractinterface-class-cs.png)
    ![Interface resultante – C#](media/extractinterface-interface-cs.png)

   - Visual Basic:

    ![Classe resultante – Visual Basic](media/extractinterface-class-vb.png)
    ![Interface resultante – Visual Basic](media/extractinterface-interface-vb.png)

## <a name="see-also"></a>Consulte também

[Refatoração](../refactoring-in-visual-studio.md)