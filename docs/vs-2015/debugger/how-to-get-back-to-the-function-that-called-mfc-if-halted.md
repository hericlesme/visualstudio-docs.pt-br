---
title: 'Como: obter de volta para a função que chamou MFC em caso de interrupção | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.mfc
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- functions [C++], debugging
- function calls, returning to calling function
- debugging [MFC], returning to calling function
- debugging [MFC], functions
- Break command
- programs, halting
- functions [debugger]
ms.assetid: d254a5a9-afbd-4923-9d7a-7422d824cabf
caps.latest.revision: 21
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d9148fb0f3431f7edc0d4b69fdf83ef4b629789f
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47466486"
---
# <a name="how-to-get-back-to-the-function-that-called-mfc-if-halted"></a>Como retornar à função que chamou MFC em caso de parada
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [como: Voltar para a função que chamado MFC se interrompida](https://docs.microsoft.com/visualstudio/debugger/how-to-get-back-to-the-function-that-called-mfc-if-halted).  
  
OBSERVAÇÃO]
>  As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas. Para alterar as configurações, escolha Importar e Exportar Configurações no menu Ferramentas. Para obter mais informações, consulte [Personalizando configurações de desenvolvimento no Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 Se você tiver usado o **quebrar** comando as **depurar** menu para interromper o programa e terminou no MFC, e você se o problema está no seu código, você pode usar a janela pilha de chamadas para navegar de volta para sua função. Para obter mais informações, consulte [como: usar a janela pilha de chamadas](../debugger/how-to-use-the-call-stack-window.md).  
  
 Às vezes seu código pode ser interrompido na bomba da mensagem. Nesse caso, não há nenhum código de usuário na pilha de chamadas. Para evitar esse problema, você pode usar pontos de interrupção (possivelmente com condições e contagens de ocorrências) em vez do **quebrar** comando. Para obter mais informações, consulte [pontos de interrupção e Tracepoints](http://msdn.microsoft.com/en-us/fe4eedc1-71aa-4928-962f-0912c334d583)).  
  
### <a name="to-navigate-to-the-function-from-which-mfc-was-called"></a>Para navegar até a função da qual o MFC foi chamado  
  
-   Use o **pilha de chamadas** janela.  
  
## <a name="see-also"></a>Consulte também  
 [Perguntas frequentes do código nativo de depuração](../debugger/debugging-native-code-faqs.md)   
 [Depurando código nativo](../debugger/debugging-native-code.md)



