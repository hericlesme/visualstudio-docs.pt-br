---
title: "Extrair interface - refatoração (Visual Basic) | Microsoft Docs"
ms.custom: 
ms.date: 11/17/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.devlang: VB
ms.assetid: db857fb1-3e22-46e2-b15a-56ef9f329235
author: gewarren
ms.author: gewarren
manager: ghogen
f1_keywords: vs.csharp.refactoring.extractinterface
dev_langs: VB
ms.workload: multiple
ms.openlocfilehash: 08bbae629dbd0e1098eca67107926d290ffe7fb3
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="extract-an-interface-in-visual-basic"></a>Extrair uma interface no Visual Basic
**O que:** permite que você crie uma interface usando membros existentes de uma classe, struct ou interface.

**Quando:** ter várias classes, estruturas ou interfaces com métodos que podem ser feitos comuns e usado por outras classes, estruturas ou interfaces.

**Motivo:** Interfaces são ótimas construções para designs orientada a objeto.  Imagine-se de ter classes para vários animais (Cat, cachorro pássaro) que podem ter métodos comuns, como Eat, Bebida, suspensão.  Usando uma interface como IAnimal permitiria Dog Cat e pássaro tenha um comum "assinatura" para esses métodos.  

**Como:**

1. Realce o nome da classe para executar a ação na ou simplesmente colocar o cursor de texto em algum lugar no nome de classe.

   ![Código realçado](media/extractinterface_highlight.png)

1. Em seguida, siga um destes procedimentos:
   * **Teclado**
     * Pressione **Ctrl + R**, em seguida, **Ctrl + I**.  (Observe que o atalho de teclado pode ser diferente com base no perfil selecionado.)
     * Pressione **Ctrl +.** para disparar o **ações rápidas e refatorações** menu e selecione **extrair Interface** do popup da janela de visualização.
   * **Mouse**
     * Selecione **Editar > Refatorar > Extrair Interface**.
     * Clique no nome da classe, selecione o **ações rápidas e refatorações** menu e selecione **extrair Interface** do popup da janela de visualização.

1. No **extrair Interface** caixa de diálogo pop-up, insira as informações solicitadas: ![extrair Interface](media/extractinterface_dialog.png)
   | Campo | Descrição |
   | --- | --- |
   | **Novo nome da interface** | O nome da interface a ser criado. O padrão é*ClassName*, onde *ClassName* é o nome da classe selecionada acima. |
   | **Novo nome de arquivo** | O nome do arquivo que será gerado com a interface. Como com o nome da interface, o padrão é*ClassName*, onde *ClassName* é o nome da classe selecionada acima. |
   | **Selecionar membros públicos para formar interface** | Os itens para extrair para a interface.  Você pode selecionar quantos desejar. |

1. Clique em **OK**.

   A interface será criada imediatamente no arquivo o nome especificado.  Além disso, a classe que você selecionou agora implementar essa interface.

   ![Classe resultante](media/extractinterface_class.png)
   ![Interface resultante](media/extractinterface_interface.png)

## <a name="see-also"></a>Consulte também
[Refatoração (Visual Basic)](../refactoring-vb.md)