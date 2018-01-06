---
title: "Como: sair do código gerenciado quando quadros nativos não forem encontrados na janela de pilha de chamadas | Microsoft Docs"
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
- JScript
- SQL
helpviewer_keywords:
- Call Stack window, missing native frames
- code, managed code
- native frames
- stepping, out of managed code
- managed code, stepping out of
ms.assetid: 97cdd2a8-02a9-4a06-a5b1-c92b1e431979
caps.latest.revision: "19"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 7599c99c9375cda7b5f24432db8c137c5c4357df
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-step-out-of-managed-code-when-native-frames-are-missing-from-the-call-stack-window"></a>Como sair do código gerenciado quando quadros nativos não forem encontrados na janela Pilha de Chamadas
Se seu código possui quadros nativos que são visíveis no **pilha de chamadas** janela, revisão de código gerenciado pode produzir resultados inesperados. Como alternativa, você pode usar um ponto de interrupção em vez de **sair**.  
  
> [!NOTE]
>  As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas. Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**. Para obter mais informações, confira [Personalizar o IDE do Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
### <a name="to-step-out-of-managed-code-when-native-frames-are-missing-from-the-call-stack-display"></a>Para depurar fora do código gerenciado quando os quadros nativos estiverem ausentes da exibição da pilha de chamadas  
  
1.  No código nativo, defina um ponto de interrupção do local depois da chamada para o código gerenciado.  
  
2.  Sobre o **depurar** menu, escolha **continuar**.  
  
     Quando a chamada gerenciada for concluída, a execução será interrompida no ponto de interrupção no código nativo.  
  
## <a name="see-also"></a>Consulte também  
 [Como usar a janela Pilha de Chamadas](../debugger/how-to-use-the-call-stack-window.md)