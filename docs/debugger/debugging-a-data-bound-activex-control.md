---
title: "Depuração de um controle ActiveX com ligação de dados | Microsoft Docs"
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
- data-bound controls, ActiveX
- ActiveX controls, debugging
- controls [Visual Studio], ActiveX
ms.assetid: 9f6e1f00-e25b-48a9-8484-7e67a1232461
caps.latest.revision: "15"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 32cbb7bee21b54c932e0c369c46c3b2c3dacd898
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="debugging-a-data-bound-activex-control"></a>Depurando um controle ActiveX com ligação de dados
Se você estiver desenvolvendo um controle ActiveX que será associado a um controle da fonte de dados, poderá criar seu próprio aplicativo de contêiner e usar esse contêiner para depurar o controle ActiveX.  
  
 Por exemplo, você pode criar um aplicativo MFC baseado em diálogo e colocar o controle associado a dados e um controle da fonte de dados na caixa de diálogo. Você pode usar esse aplicativo MFC para teste de tempo de execução e como o executável do contêiner para depurar seu controle ActiveX associado a dados.  
  
## <a name="using-the-test-container"></a>Usando o contêiner de teste  
 Se você quiser um contêiner que possa modificar facilmente para dar suporte a várias interfaces no controle ou no contêiner, use o contêiner de teste ActiveX como o executável para a sessão de depuração. No contêiner de teste do ActiveX, clique em **opções** do **contêiner** menu para permitir várias interfaces. Para obter mais informações, consulte [testando propriedades e eventos com contêiner de teste](/cpp/mfc/testing-properties-and-events-with-test-container).  
  
 Se você precisar entrar no código do contêiner enquanto está depurando, use a versão de depuração do contêiner ou use a versão de depuração do contêiner de teste ActiveX. Para obter mais informações, consulte [TSTCON exemplo: contêiner de teste do controle ActiveX](http://msdn.microsoft.com/en-us/72fa40ef-27d3-400c-813f-10b03236e600).  
  
## <a name="see-also"></a>Consulte também  
 [COM e ActiveX depuração](../debugger/com-and-activex-debugging.md)   
 [Controles ActiveX](/cpp/mfc/activex-controls)