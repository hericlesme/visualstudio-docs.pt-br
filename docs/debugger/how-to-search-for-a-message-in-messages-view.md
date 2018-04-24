---
title: 'Como: procurar uma mensagem na exibição de mensagens | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Message Search dialog box
- Messages view
- messages, searching for
ms.assetid: 732b7ccc-54ea-41db-823b-2b96e3e4083e
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 368d10f2285c94f053e536da77966e9b2fb26da9
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2018
---
# <a name="how-to-search-for-a-message-in-messages-view"></a>Como procurar uma mensagem na exibição de mensagens
Você pode procurar uma mensagem específica no modo de exibição de mensagens usando seu identificador, o tipo ou a ID de mensagem como critério de pesquisa. Qualquer uma dessas — ou uma combinação — será critérios de pesquisa válido. A direção inicial da pesquisa também pode ser especificada. Os campos na caixa de diálogo são pré-carregados com os atributos da mensagem selecionada no momento.  
  
### <a name="to-search-for-a-message-in-messages-view"></a>Para pesquisar uma mensagem na exibição de mensagens  
  
1.  Organizar as janelas assim que Spy + + e ativo [exibição de mensagens](../debugger/messages-view.md) janela são visíveis.  
  
2.  Do **pesquisa** menu, escolha **localizar mensagem**.  
  
     O [caixa de diálogo de pesquisa de mensagens](../debugger/message-search-dialog-box.md) é aberto.  
  
3.  Arraste o **ferramenta localizador** sobre a janela desejada. Quando você arrasta a ferramenta, o **mensagem pesquisa** caixa de diálogo exibe detalhes sobre a janela selecionada.  
  
     - ou –  
  
     Se você tiver o identificador da janela cujas mensagens que você deseja examinar, digite-o para o **tratar** caixa de texto.  
  
     - ou –  
  
     Se você souber o tipo de mensagem e/ou a ID da mensagem, selecione-os a **tipo** e **mensagem** menus suspensos e desmarque o **tratar** caixa de texto.  
  
4.  Limpe todos os campos para os quais você não deseja especificar valores.  
  
    > [!TIP]
    >  Para reduzir a desordem, selecione o **Spy ocultar** opção. Esta opção oculta a janela principal do Spy + +, deixando apenas o **encontrar janela** caixa de diálogo visível na parte superior de outros aplicativos. A janela principal do Spy + + é restaurada quando você clicar em **Okey** ou **Cancelar**, ou quando você desmarca o **ocultar Spy + +** opção.  
  
5.  Escolha **backup** ou **para baixo** para a direção inicial da pesquisa.  
  
6.  Clique em **OK**.  
  
 Se uma mensagem correspondente for encontrada, ele é realçado na janela de exibição de mensagens. Consulte [a exibição de mensagens](../debugger/messages-view.md).