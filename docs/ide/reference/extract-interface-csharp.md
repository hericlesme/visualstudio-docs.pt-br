---
title: Extrair uma interface em C# | Microsoft Docs
ms.custom: 
ms.date: 11/16/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: ghogen
f1_keywords:
- vs.csharp.refactoring.extractinterface
dev_langs:
- csharp
ms.workload:
- dotnet
ms.openlocfilehash: 0e763bacb6d900fea251b3c41d33fb464479f2c4
ms.sourcegitcommit: b01406355e3b97547b7cbf8ce3960f101b165cec
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/06/2018
---
# <a name="extract-an-interface-in-c"></a>Extrair uma interface em C# #

**O quê:** permite que você crie uma interface usando membros existentes de uma classe, struct ou interface.

**Quando:** você tem várias classes, structs ou interfaces com métodos que podem ser comuns e usados por outras classes, structs ou interfaces.

**Por quê:** as interfaces são ótimos constructos para designs orientados a objetos.  Imagine ter classes para vários animais (gato, cachorro, pássaro) que podem ter métodos comuns, como comer, beber, dormir.  Usar uma interface como IAnimal permitiria que cachorro, gato e pássaro tivessem uma "assinatura" comum para esses métodos.

**Como:**

1. realce o nome da classe para executar a ação ou simplesmente coloque o cursor do texto em algum lugar no nome da classe.

   ![Código realçado](media/extractinterface-highlight-cs.png)

1. Depois, siga um destes procedimentos:
   * **Teclado**
     * Pressione **Ctrl+R**, em seguida, **Ctrl+I**.  (Observe que o atalho de teclado pode ser diferente com base no perfil selecionado.)
     * Pressione **Ctrl +.** para disparar o menu **Ações Rápidas e Refatorações** e selecionar **Extrair Interface** no pop-up da janela Visualização.
   * **Mouse**
     * Selecione **Editar > Refatorar > Extrair Interface**.
     * Clique com o botão direito do mouse no nome da classe, selecione o menu **Ações Rápidas e Refatorações** e selecione **Extrair Interface** no pop-up da janela Visualização.

1. Na caixa de diálogo **Extrair Interface** que surge, insira as informações solicitadas: ![Extrair Interface](media/extractinterface-dialog-cs.png)
   | Campo | Descrição |
   | --- | --- |
   | **Nome da nova interface** | O nome da interface a ser criada. O padrão é I*ClassName*, onde *ClassName* é o nome da classe selecionada acima. |
   | **Nome do novo arquivo** | O nome do arquivo que será gerado com a interface. Como acontece com o nome da interface, o padrão é I*ClassName*, onde *ClassName* é o nome da classe selecionada acima. |
   | **Selecionar membros públicos para formar a interface** | Os itens a serem extraídos para a interface.  Você pode selecionar quantos desejar. |

1. Clique em **OK**.

   A interface será criada imediatamente no arquivo do nome especificado.  Além disso, a classe que você selecionou agora implementará essa interface.

   ![Classe Resultante](media/extractinterface-class-cs.png)
   ![Interface Resultante](media/extractinterface-interface-cs.png)

## <a name="see-also"></a>Consulte também

[Refatoração](../refactoring-in-visual-studio.md)