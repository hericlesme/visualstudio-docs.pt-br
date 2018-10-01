---
title: Guia geral, caixa de diálogo Propriedades do Thread | Microsoft Docs
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
- threading [Visual Studio], thread properties
- thread properties
ms.assetid: 46b6c668-6786-456e-97dc-337bcac0d812
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2610e76710d2c3138d981e3a2df83345cac418bd
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47460691"
---
# <a name="general-tab-thread-properties-dialog-box"></a>Guia Geral, Caixa de diálogo Propriedades do Thread
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [guia geral, caixa de diálogo de propriedades do Thread](https://docs.microsoft.com/visualstudio/debugger/general-tab-thread-properties-dialog-box).  
  
Use essa caixa de diálogo para obter mais informações sobre um segmento específico. Para exibir essa caixa de diálogo, mova o foco para um [exibição de Threads](../debugger/threads-view.md) janela ou abra [exibição de mensagens](../debugger/messages-view.md) e expandir uma mensagem. Selecione qualquer nó de segmento na árvore e escolha **propriedades** da **exibição** menu.  
  
 O **propriedades do Thread** caixa de diálogo contém um painel, o **geral** guia. As configurações a seguir estão disponíveis:  
  
|Entrada|Descrição|  
|-----------|-----------------|  
|**Nome do Módulo**|O nome do módulo.|  
|**ID do Thread**|A ID exclusiva deste thread. Observe que os números de ID de thread são reutilizados; elas identificam um thread somente para o tempo de vida do thread em questão.|  
|**ID do Processo**|A ID exclusiva desse processo. Números de ID de processo são reutilizados, eles identificam um processo somente para o tempo de vida do processo. O tipo de objeto de processo é criado quando um programa é executado. Todos os threads em um processo compartilham o mesmo espaço de endereço e têm acesso aos mesmos dados. Escolha esse valor para exibir as propriedades de ID do processo.|  
|**Estado de thread**|O estado atual do thread. Um thread de execução é utilizar um processador. um thread em espera está prestes a usar um. Um Thread pronto está esperando para usar um processador como um não é gratuito. Um thread em transição está aguardando um recurso a ser executado, como aguardar sua pilha de execução ser paginada do disco. Um thread em espera não é necessário o processador porque está aguardando uma operação periférica ser concluída ou um recurso seja liberado.|  
|**Motivo de espera**|Isso é aplicável somente quando o thread está em estado de espera. Pares de eventos são usados para se comunicar com subsistemas protegidos.|  
|**Tempo de CPU**|Tempo total de CPU gasto sobre esse processo e seus threads. Igual ao tempo de usuário + tempo privilegiado.|  
|**Tempo do usuário**|O tempo total decorrido que esse thread gastou executando código no modo de usuário. Aplicativos executam no modo de usuário, como fazem os subsistemas, como o Gerenciador de janelas e o mecanismo gráfico.|  
|**Tempo privilegiado**|O tempo total decorrido que esse thread gastou executando código em modo privilegiado. Quando um serviço de sistema do Windows é chamado, o serviço geralmente será executado em modo privilegiado para obter acesso aos dados privados do sistema. Esses dados são protegidos contra acesso por threads em execução no modo de usuário. Chamadas para o sistema podem ser explícitas ou podem ser implícitas, como quando ocorre uma falha de página ou uma interrupção.|  
|**Tempo decorrido**|O tempo total decorrido (em segundos) esse thread está sendo executado.|  
|**Prioridade atual**|A prioridade dinâmica atual deste thread. Threads dentro de um processo podem aumentar e diminuir sua própria prioridade básica em relação a prioridade base do processo.|  
|**Prioridade básica**|A prioridade base atual deste thread.|  
|**Endereço inicial**|Iniciando endereço virtual para este thread.|  
|**PC do usuário**|O contador de programa do usuário para o thread.|  
|**Alternâncias de contexto**|O número de alternâncias de um thread para outro. Alternâncias de thread podem ocorrer dentro de um único processo ou entre processos. Um comutador de thread pode ser causado por um thread solicitando informações a outro, ou por um thread sendo apropriado quando um thread de prioridade mais alta se torna pronto para ser executado.|



