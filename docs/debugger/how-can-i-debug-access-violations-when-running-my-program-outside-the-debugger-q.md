---
title: "Como posso depurar violações de acesso ao executar meu programa fora do depurador? | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.access
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- access violation debugging
- debugging [Visual Studio], access violations
ms.assetid: 780a298a-132e-4245-8370-8c82ca27c6c1
caps.latest.revision: "19"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 0af98932a940126c8f7288d7b5c830bb40f270fe
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-can-i-debug-access-violations-when-running-my-program-outside-the-debugger"></a>Como posso depurar violações de acesso ao executar meu programa fora do depurador?
## <a name="problem-description"></a>Descrição do problema  
 Meu programa é executado corretamente no ambiente do Visual Studio, mas quando eu o executo em modo autônomo no sistema operacional Windows, ele gera uma violação de acesso. Como posso depurar esse problema?  
  
## <a name="solution"></a>Solução  
 Definir o [Just-in-time depuração](../debugger/just-in-time-debugging-in-visual-studio.md) opção e execute o programa autônomo, até que a violação de acesso. Em seguida, no **violação de acesso** caixa de diálogo, você pode clicar em **Cancelar** para iniciar o depurador.  
  
 Além disso, consulte o artigo da Base de Dados de Conhecimento Q133174, “Como localizar onde ocorre uma falha geral de proteção (GP)”. Você pode encontrar artigos da Base de dados de Conhecimento no CD de biblioteca do MSDN ou pesquisando [http://support.microsoft.com/](http://support.microsoft.com/).  
  
## <a name="see-also"></a>Consulte também  
 [Perguntas frequentes de código nativo de depuração](../debugger/debugging-native-code-faqs.md)   
 [Depurando código nativo](../debugger/debugging-native-code.md)