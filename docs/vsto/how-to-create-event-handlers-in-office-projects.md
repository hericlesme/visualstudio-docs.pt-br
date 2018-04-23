---
title: 'Como: criar manipuladores de eventos em projetos do Office | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visual Basic [Office development in Visual Studio], event handlers
- event handlers [Office development in Visual Studio]
- Visual C# [Office development in Visual Studio], event handlers
- events [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 833e41979d1dac9def7e647b396161d0ac5e2b67
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-create-event-handlers-in-office-projects"></a>Como criar manipuladores de eventos em projetos do Office
  Há várias maneiras de criar manipuladores de eventos no Visual Basic e c#. No modo design, você pode criar manipuladores de eventos para controles de padrão clicando duas vezes no controle ou usar o painel de eventos do **propriedades** janela criar manipuladores para qualquer evento no controle. No entanto, se você estiver no modo de exibição de código, não convém alternar para modo de Design para criar um manipulador de eventos.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
### <a name="to-create-an-event-handler-in-visual-basic"></a>Para criar um manipulador de eventos no Visual Basic  
  
1.  Do **nome da classe** lista suspensa na parte superior do Editor de códigos, selecione o objeto que você deseja criar um manipulador de eventos.  
  
    > [!NOTE]  
    >  Se você quiser criar manipuladores de eventos para `ThisDocument` ou `ThisWorkbook`, você deve selecionar **(ThisDocument eventos)** ou **(ThisWorkbook eventos)** no **nome da classe**lista suspensa  
  
2.  Do **nome do método** lista suspensa na parte superior do Editor de códigos, selecione o evento.  
  
     Visual Studio cria o manipulador de eventos e move o ponto de inserção para o manipulador de eventos criado recentemente. Se o manipulador de eventos já existir, o ponto de inserção se move para o manipulador de eventos existente.  
  
### <a name="to-create-an-event-handler-in-c"></a>Para criar um manipulador de eventos em c#  
  
1.  Criar o delegado de evento no **inicialização** evento da classe digitando o nome qualificado do evento seguido por um espaço e, em seguida, digitando **+=** posteriormente sem espaço. Por exemplo:  
  
     `this.<object name>.<event name> +=`  
  
2.  No final da linha de código, pressione a tecla TAB duas vezes.  
  
     O Visual Studio automaticamente conclui a linha de código cria o manipulador de eventos e move o ponto de inserção para o manipulador de eventos criado recentemente.  
  
## <a name="see-also"></a>Consulte também  
 [Escrevendo código em soluções do Office](../vsto/writing-code-in-office-solutions.md)   
 [Passo a passo: Programando em eventos de um controle NamedRange](../vsto/walkthrough-programming-against-events-of-a-namedrange-control.md)   
 [Compilando soluções do Office](../vsto/building-office-solutions.md)  
  
  