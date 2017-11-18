---
title: "Não é possível alterar a caixa de diálogo valor | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.variables.failededit
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Cannot Change Value dialog box
- variables [debugger], editing
ms.assetid: 19e930c2-5fbf-4c83-aae8-a1dc3f8fcae8
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b05c461d71f1fc1526114e8ae41ecf7f04d63885
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="cannot-change-value-dialog-box"></a>Caixa de diálogo Não é Possível Alterar o Valor
## <a name="error"></a>Erro  
 `The value of this variable cannot be changed`&#124; `The name` *nome* `does not exist in the current context` &#124; *várias outras mensagens*  
  
 Essa caixa de mensagem aparece quando você tenta alterar o conteúdo de uma variável para um valor inválido em uma janela do depurador (janelas Autos, Inspeção ou Locais) ou na caixa de diálogo QuickWatch. Por exemplo, se você tentar definir o valor de uma variável de inteiro como uma cadeia de caracteres, essa caixa de mensagem é exibida.  
  
## <a name="solution"></a>Solução  
 Certifique-se que o valor inserido na janela do depurador ou na caixa de diálogo QuickWatch representa um valor válido para a variável que você está tentando definir.  
  
## <a name="see-also"></a>Consulte também  
 [Expressões no depurador](../debugger/expressions-in-the-debugger.md)