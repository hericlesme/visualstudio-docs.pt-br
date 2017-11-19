---
title: "Depuração e o processo de hospedagem | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], hosting process
- hosting process
ms.assetid: d0f0b9a6-2a6e-463d-b6ea-9518ee727933
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 02cdf8b50415a238c2af2735a20fea4ed8c23668
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="debugging-and-the-hosting-process"></a>Depuração e o processo de hospedagem
O processo de hospedagem do Visual Studio melhora o desempenho do depurador e habilita novos recursos do depurador, como a depuração de confiança parcial e a avaliação de expressão de tempo de design. Você pode desabilitar o processo de hospedagem se isso for necessário. Para obter mais informações, consulte [como: desabilitar o processo de hospedagem](../ide/how-to-disable-the-hosting-process.md). As seções a seguir descrevem algumas diferenças entre a depuração com e sem o processo de hospedagem.  
  
## <a name="partial-trust-debugging-and-click-once-security"></a>Depuração de confiança parcial e segurança de Click-Once  
 A depuração de confiança parcial requer o processo de hospedagem. Se você desabilitar o processo de hospedagem, confiança parcial depuração não irá funcionar mesmo se segurança de confiança parcial é habilitada no **segurança** página de **propriedades do projeto**. Para obter mais informações, consulte [como: desabilitar o processo de hospedagem](../ide/how-to-disable-the-hosting-process.md) e [como: depurar um aplicativo de confiança parcial](../debugger/how-to-debug-a-partial-trust-application.md).  
  
## <a name="design-time-expression-evaluation"></a>Avaliação de expressão de tempo de design  
 A expressão de tempo de design sempre usa o processo de hospedagem. Desabilitando a hospedagem processar o **propriedades do projeto** desabilita a avaliação de expressão em tempo de design para projetos de biblioteca de classe. Para outros tipos de projeto, a avaliação de expressão de tempo de design não é desabilitada. Em vez disso, o Visual Studio inicia o executável real e usa-o para a avaliação de tempo de design sem o processo de hospedagem. Essa diferença pode produzir resultados diferentes.  
  
## <a name="appdomaincurrentdomainfriendlyname-differences"></a>Diferenças de AppDomain.CurrentDomain.FriendlyName  
 O `AppDomain.CurrentDomain.FriendlyName` retorna resultados diferentes dependendo se o processo de hospedagem está habilitado. Se você chamar `AppDomain.CurrentDomain.FriendlyName` com o processo de hospedagem habilitado, ele retorna *app_name*`.vhost.exe`. Se você chamá-lo o processo de hospedagem desabilitado, ele retorna *app_name*`.exe`.  
  
## <a name="assemblygetcallingassemblyfullname-differences"></a>Diferenças de Assembly.GetCallingAssembly().FullName  
 O `Assembly.GetCallingAssembly().FullName` retorna resultados diferentes dependendo se o processo de hospedagem está habilitado. Se você chamar `Assembly.GetCallingAssembly().FullName` com o processo de hospedagem habilitado, ele retorna `mscorlib`. Se você chamar `Assembly.GetCallingAssembly().FullName` com o processo de hospedagem desabilitado, ele retornará o nome do aplicativo.  
  
## <a name="see-also"></a>Consulte também  
 [Processo de hospedagem (vshost.exe)](../ide/hosting-process-vshost-exe.md)   
 [Como: depurar um aplicativo de confiança parcial](../debugger/how-to-debug-a-partial-trust-application.md)   
 [Como desabilitar o processo de hospedagem](../ide/how-to-disable-the-hosting-process.md)