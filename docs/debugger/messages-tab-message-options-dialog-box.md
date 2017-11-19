---
title: "Guia de mensagens, caixa de diálogo de opções de mensagem | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: message options, Messages
ms.assetid: fb9fa211-e82c-40a5-9e4b-ba8de07313c0
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a8c3578db069a90baa8192af0641465dbecc790b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="messages-tab-message-options-dialog-box"></a>Guia Mensagens, Caixa de diálogo Opções da Mensagem
Use o **mensagens** tab para selecionar qual mensagem tipos à lista na [exibição de mensagens](../debugger/messages-view.md)e para especificar critérios de pesquisa de mensagem. Para exibir o [caixa de diálogo de opções de mensagem](../debugger/message-options-dialog-box.md), escolha **mensagens de Log** do **Spy** menu.  
  
 Normalmente, você primeiro selecionar **grupos de mensagens**e, em seguida, ajustar a seleção selecionando individuais **mensagens para o modo**. O **todos os** botão Seleciona todos os tipos de mensagem e o **nenhum** botão limpa todos os tipos.  
  
 As configurações a seguir estão disponíveis no **mensagens** guia:  
  
 **Mensagens para o modo de exibição**  
 Selecione mensagens específicas para exibição. Quando você cria uma nova janela de mensagens, ele pode exibir todas as mensagens. Quando você filtrar mensagens de **mensagens** guia, esse filtro se aplica apenas às novas mensagens, não as mensagens que já foram exibidas no modo de exibição do Windows.  
  
 **Grupos de mensagens**  
 Selecione os grupos de mensagem para a exibição. Os grupos disponíveis incluem:  
  
-   WM_USER: com um código de maior que ou igual a WM_USER  
  
-   Registrado: registrado com o **RegisterWindowMessage** chamar  
  
-   Desconhecido: mensagens de desconhecido no intervalo de 0 a (WM_USER - 1)  
  
 Observe que essas **grupos de mensagens** não são mapeadas para as entradas específicas em **mensagens para exibir**. Quando você seleciona um grupo, a seleção é aplicada diretamente ao fluxo de mensagens.  
  
 Uma caixa de seleção esmaecida na **grupos de mensagens** indica que o **mensagens para exibir** caixa de listagem foi modificada para mensagens nesse grupo; nem todos os tipos de mensagem nesse grupo são selecionados.  
  
 **Salvar as configurações como padrão**  
 Salve as configurações atuais para uso posterior como opções de pesquisa de mensagem. Essas configurações também são salvas quando você sair Spy + +.