---
title: Guia mensagens, caixa de diálogo de opções de mensagem | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- message options, Messages
ms.assetid: fb9fa211-e82c-40a5-9e4b-ba8de07313c0
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8048c63ed9b9f049ed171002dfcc612fc9361569
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47466965"
---
# <a name="messages-tab-message-options-dialog-box"></a>Guia Mensagens, Caixa de diálogo Opções da Mensagem
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [guia mensagens, caixa de diálogo de opções de mensagem](https://docs.microsoft.com/visualstudio/debugger/messages-tab-message-options-dialog-box).  
  
Use o **mensagens** tab para selecionar qual mensagem tipos à lista na [exibição de mensagens](../debugger/messages-view.md)e para especificar critérios de pesquisa da mensagem. Para exibir o [caixa de diálogo de opções de mensagem](../debugger/message-options-dialog-box.md), escolha **mensagens de Log** do **Spy** menu.  
  
 Normalmente, você seleciona pela primeira vez **grupos de mensagens**e, em seguida, ajustar a seleção selecionando individuais **mensagens para o modo de exibição**. O **todos os** botão Seleciona todos os tipos de mensagem e o **None** botão limpa todos os tipos.  
  
 As seguintes configurações estão disponíveis sobre o **mensagens** guia:  
  
 **Mensagens para o modo de exibição**  
 Selecione mensagens específicas para a exibição. Quando você cria uma nova janela de mensagens, ele pode exibir todas as mensagens. Quando você filtra mensagens do **mensagens** guia, esse filtro se aplica somente a novas mensagens, não as mensagens que já foram exibidas na exibição do Windows.  
  
 **Grupos de mensagens**  
 Selecione os grupos de mensagens para a exibição. Os grupos disponíveis incluem:  
  
-   WM_USER: com um código de maior que ou igual a WM_USER  
  
-   Registrado: registrado com o **RegisterWindowMessage** chamar  
  
-   Desconhecido: mensagens desconhecidas no intervalo de 0 a (WM_USER – 1)  
  
 Observe que esses **grupos de mensagens** não são mapeadas para as entradas específicas sob **exibição de mensagens para**. Quando você seleciona um grupo, a seleção é aplicada diretamente ao fluxo de mensagens.  
  
 Uma caixa de seleção esmaecida dentro **grupos de mensagens** indica que o **exibição de mensagens para** caixa de listagem foi modificada para mensagens nesse grupo; nem todos os tipos de mensagem nesse grupo são selecionados.  
  
 **Salvar configurações como padrão**  
 Salve as configurações atuais para uso posterior como opções de pesquisa da mensagem. Essas configurações também são salvas ao sair Spy + +.



