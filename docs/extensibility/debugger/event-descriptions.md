---
title: "Descrições de eventos | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], events
ms.assetid: 09f61652-7e16-4bb0-8055-f61a84bf384e
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 6ec084c0d985ce5cc3cb0a886bd1fdcaf6cc3e54
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="event-descriptions"></a>Descrições de eventos
Cada tipo de evento tem uma finalidade específica.  
  
## <a name="events-and-the-reasons-for-their-use"></a>Eventos e os motivos para seu uso  
  
|evento|Descrição|  
|-----------|-----------------|  
|Ativar eventos do documento|Ocorre quando o mecanismo de depuração (DE) quer o IDE para abrir ou colocar um documento para o primeiro plano.|  
|Ponto de interrupção associado ou eventos de erro do ponto de interrupção|Enviado quando um ponto de interrupção está associado ou quando não é possível associar um ponto de interrupção e um erro será retornado.|  
|Eventos de ponto de interrupção não associado|Ocorrem quando um ponto de interrupção associado desvincula do código.|  
|Pode interromper eventos|Enviado para o IDE para determinar se o usuário deseja parar em um momento específico no código.|  
|Eventos de ponto de interrupção|Ocorre quando um código ou dados de ponto de interrupção.|  
|Eventos de texto do documento|Ocorre quando o texto em um documento é alterado. Esses eventos não são enviados por meio de `IDebugEventCallBack2::Event` método.|  
|Mecanismo de criar eventos|Enviado quando um mecanismo é criado pela primeira vez.|  
|Eventos de ponto de entrada|Enviado quando o programa que está sendo depurado tem executar seu código de inicialização e atingiu seu primeiro ponto de entrada do usuário.|  
|Eventos de exceção|Enviado quando um programa em execução atinge uma exceção.|  
|Eventos de conclusão de avaliação de expressão|Enviado quando a avaliação de expressão assíncrona for concluída.|  
|Localizar eventos de símbolo|Enviado sempre que o DE precisa perguntar ao usuário para localizar símbolos para um módulo.|  
|Eventos de conclusão de carga|Enviado apenas quando a carga inicial do programa for concluída e o primeiro código está prestes a ser executado no programa.|  
|Eventos de mensagem|Enviado quando mensagens são enviadas aos usuários.|  
|Eventos de carregamento de módulo|Enviado quando um novo módulo é carregado e descarregado.|  
|Eventos de cadeia de caracteres de saída|Enviado quando o programa grava a saída de depuração.|  
|Criar e destruir eventos|Enviado para anunciar a criação ou destruição de processos, programas, propriedades, sessões e os threads, portanto o IDE do Visual Studio pode acompanhar o estado dos programas que está sendo depurado.|  
|Eventos de conclusão da etapa|Enviado quando uma etapa for concluída.|  
|Eventos de alteração do nome do thread|Enviado quando o usuário altera o nome de um thread.|  
|Eventos de alteração de nome de programa|Enviado quando o usuário altera o nome de um programa.|  
  
## <a name="see-also"></a>Consulte também  
 [Enviar eventos](../../extensibility/debugger/sending-events.md)