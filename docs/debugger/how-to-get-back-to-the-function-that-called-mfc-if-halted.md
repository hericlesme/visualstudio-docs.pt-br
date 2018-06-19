---
title: 'Como: Voltar para a função que chamou MFC em caso de parada | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.mfc
dev_langs:
- CSharp
- VB
- FSharp
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 356e9f4950e62f3ac1399b1e79ee2fe400cec47b
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2018
ms.locfileid: "31472875"
---
# <a name="how-to-get-back-to-the-function-that-called-mfc-if-halted"></a>Como retornar à função que chamou MFC em caso de parada
> [!NOTE]
>  As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas. Para alterar as configurações, escolha Importar e Exportar Configurações no menu Ferramentas. Para obter mais informações, confira [Personalizar o IDE do Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
 Se você usou o **quebra** comando o **depurar** menu para interromper o programa terminou em MFC e tiver certeza de que o problema está no seu código, você pode usar a janela pilha de chamadas para navegar de volta para sua função. Para obter mais informações, consulte [como: usar a janela pilha de chamadas](../debugger/how-to-use-the-call-stack-window.md).  
  
 Às vezes seu código pode ser interrompido na bomba da mensagem. Nesse caso, não há nenhum código de usuário na pilha de chamadas. Para evitar esse problema, você pode usar pontos de interrupção (possivelmente com as condições e contagens de ocorrências) em vez do **quebra** comando. Para obter mais informações, consulte [pontos de interrupção e pontos de rastreamento](http://msdn.microsoft.com/en-us/fe4eedc1-71aa-4928-962f-0912c334d583)).  
  
### <a name="to-navigate-to-the-function-from-which-mfc-was-called"></a>Para navegar até a função da qual o MFC foi chamado  
  
-   Use o **pilha de chamadas** janela.  
  
## <a name="see-also"></a>Consulte também  
 [Perguntas frequentes de código nativo de depuração](../debugger/debugging-native-code-faqs.md)   
 [Depurando código nativo](../debugger/debugging-native-code.md)