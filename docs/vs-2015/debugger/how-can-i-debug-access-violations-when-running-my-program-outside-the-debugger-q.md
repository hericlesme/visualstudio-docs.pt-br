---
title: Como posso depurar violações de acesso ao executar meu programa fora do depurador? | Microsoft Docs
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
- vs.debug.access
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- access violation debugging
- debugging [Visual Studio], access violations
ms.assetid: 780a298a-132e-4245-8370-8c82ca27c6c1
caps.latest.revision: 22
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1525061210c6ef7cdda32c6204648c3944f4b889
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47461627"
---
# <a name="how-can-i-debug-access-violations-when-running-my-program-outside-the-debugger"></a>Como posso depurar violações de acesso ao executar meu programa fora do depurador?
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [como posso depurar acesso violações quando executar meu programa fora o depurador?](https://docs.microsoft.com/visualstudio/debugger/how-can-i-debug-access-violations-when-running-my-program-outside-the-debugger-q).  
  
Descrição do problema  
 Meu programa é executado corretamente no ambiente do Visual Studio, mas quando eu o executo em modo autônomo no sistema operacional Windows, ele gera uma violação de acesso. Como posso depurar esse problema?  
  
## <a name="solution"></a>Solução  
 Defina as [Just-in-time depuração](../debugger/just-in-time-debugging-in-visual-studio.md) opção e execute o programa autônomo, até que ocorra a violação de acesso. Em seguida, nos **violação de acesso** caixa de diálogo, você pode clicar em **Cancelar** para iniciar o depurador.  
  
 Além disso, consulte o artigo da Base de Dados de Conhecimento Q133174, “Como localizar onde ocorre uma falha geral de proteção (GP)”. Você pode encontrar artigos da Base de dados de Conhecimento no CD da biblioteca MSDN ou pesquisando [ http://support.microsoft.com/ ](http://support.microsoft.com/).  
  
## <a name="see-also"></a>Consulte também  
 [Perguntas frequentes do código nativo de depuração](../debugger/debugging-native-code-faqs.md)   
 [Depurando código nativo](../debugger/debugging-native-code.md)



