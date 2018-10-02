---
title: Comando Avaliar Instrução | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- debug.evaluatestatement
helpviewer_keywords:
- Debug.EvaluateStatement command
- Evaluate Statement command
ms.assetid: 032039bc-9477-4f93-9b9d-66d4be0e90f4
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: d569033193997135d9d0bc990ab7b9a9ef815f8d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47464257"
---
# <a name="evaluate-statement-command"></a>Comando Avaliar Instrução
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [avaliar instrução comando](https://docs.microsoft.com/visualstudio/ide/reference/evaluate-statement-command).  
  
  
Avalia e exibe a instrução fornecida.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
Debug.EvaluateStatement text   
```  
  
## <a name="arguments"></a>Arguments  
 `text`  
 Necessário. A instrução a ser avaliada.  
  
## <a name="remarks"></a>Comentários  
 A janela usada para inserir o comando **EvaluateStatement** determina se um sinal de igual (=) é interpretado como um operador de comparação ou um operador de atribuição.  
  
 Na janela **Comando**, um sinal de igual (=) é interpretado como um operador de comparação. Dessa forma, por exemplo, se os valores das variáveis `a` e `b` forem diferentes, o comando  
  
```  
>Debug.EvaluateStatement(a=b)  
```  
  
 retornará um valor de `false`.  
  
 Na janela **Imediato**, por outro lado, um sinal de igual (=) é interpretado como um operador de atribuição. Assim, por exemplo, o comando  
  
```  
>Debug.EvaluateStatement(a=b)  
```  
  
 atribuirá à variável `a` o valor da variável `b`.  
  
## <a name="example"></a>Exemplo  
  
```  
>Debug.EvaluateStatement(a+b)  
```  
  
## <a name="see-also"></a>Consulte também  
 [Comando Imprimir](../../ide/reference/print-command.md)   
 [Comandos do Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Janela Comando](../../ide/reference/command-window.md)   
 [Caixa Localizar/Comando](../../ide/find-command-box.md)   
 [Aliases de comando do Visual Studio](../../ide/reference/visual-studio-command-aliases.md)



