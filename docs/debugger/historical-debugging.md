---
title: Depuração histórica | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 7cc5ddf2-2f7c-4f83-b7ca-58e92e9bfdd2
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a75dfc04bd5ce3b1e61cc2c8e8fe293c13560cf9
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2018
---
# <a name="historical-debugging"></a>Depuração histórica
Depuração histórica é um modo de depuração que depende das informações coletadas pelo IntelliTrace. Ele permite que retroceder e Avançar pela execução de seu aplicativo e inspecionar o estado.  
  
 Você pode usar o IntelliTrace na edição Enterprise do Visual Studio (mas não nas edições Professional ou comunidade).  
  
## <a name="why-use-historical-debugging"></a>Por que usar a depuração histórica?  
 Definir pontos de interrupção para localizar erros pode ser uma questão bastante hit-or-miss. Você define um ponto de interrupção perto o lugar no seu código onde você suspeitar que o bug a ser, em seguida, executar o aplicativo no depurador e esperança que seu ponto de interrupção é atingido, e que o local em que a execução é interrompida pode revelar a origem do erro. Caso contrário, você precisará, tente definir um ponto de interrupção em outro lugar no código e execute novamente o depurador, executando as etapas de teste repetidamente até encontrar o problema.  
  
 ![definindo um ponto de interrupção](../debugger/media/breakpointprocesa.png "BreakpointProcesa")  
  
 Você pode usar o IntelliTrace e depuração histórica se movem em torno de seu aplicativo e inspecione o seu estado (pilha de chamadas e variáveis locais) sem a necessidade de definir pontos de interrupção, reinicie a depuração e repita as etapas de teste. Isso pode economizar muito tempo, especialmente quando o erro está localizado profundo em um cenário de teste que leva muito tempo para executar.  
  
## <a name="how-do-i-start-using-historical-debugging"></a>Como iniciar usando a depuração histórica?  
 IntelliTrace está ativado por padrão. Tudo o que você precisa fazer é decidir quais eventos e chamadas de função são do seu interesse e, se você deseja exibir instantâneos sua completa do estado do aplicativo. Para obter mais informações sobre como definir o que você deseja procurar, consulte [funcionalidades do IntelliTrace](../debugger/intellitrace-features.md).  

 - Para exibir instantâneos com depuração histórica, consulte [exibir instantâneos usando IntelliTrace etapa-back](../debugger/how-to-use-intellitrace-step-back.md)
 - Para saber como inspecionar variáveis e navegar pelo código, consulte [inspecionar o seu aplicativo com depuração histórica](../debugger/historical-debugging-inspect-app.md)
 - Para saber mais sobre a depuração com os eventos do IntelliTrace, consulte [passo a passo: usando o IntelliTrace](../debugger/walkthrough-using-intellitrace.md).