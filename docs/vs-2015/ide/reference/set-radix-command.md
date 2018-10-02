---
title: Comando Set Radix | Microsoft Docs
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
- debug.setradix
helpviewer_keywords:
- Set Radix command
- Debug.SetRadix command
ms.assetid: 6ffd1554-7530-4da4-b5f5-e276a5034f3b
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 99b5623fff4e2919bb34bc7dd4ba60d14ba93077
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47461954"
---
# <a name="set-radix-command"></a>Comando Definir Base
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [comando Set de base](https://docs.microsoft.com/visualstudio/ide/reference/set-radix-command).  
  
  
Define ou retorna a base numérica usada para exibir valores inteiros.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
Debug.SetRadix [10 | 16 | hex | dec]  
```  
  
## <a name="arguments"></a>Arguments  
 `10` ou `16` ou `hex` ou `dec`  
 Opcional. Indica o decimal (10 ou dez) ou hexadecimal (16 ou hexa). Se um argumento for omitido, o valor base atual será retornado.  
  
## <a name="example"></a>Exemplo  
 Este exemplo define o ambiente para exibir valores inteiros em formato hexadecimal.  
  
```  
>Debug.SetRadix hex  
```  
  
## <a name="see-also"></a>Consulte também  
 [Comandos do Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Janela Comando](../../ide/reference/command-window.md)   
 [Caixa Localizar/Comando](../../ide/find-command-box.md)   
 [Aliases de comando do Visual Studio](../../ide/reference/visual-studio-command-aliases.md)



