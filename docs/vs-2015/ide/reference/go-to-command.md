---
title: Comando Ir para | Microsoft Docs
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
- edit.goto
helpviewer_keywords:
- Debug.Goto command
- Go To command
ms.assetid: 201e1dd2-6701-467d-8cc1-faec2ef20511
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 123398be5bf8b4aece11e2624390507cec2252d0
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47464374"
---
# <a name="go-to-command"></a>Comando Ir para
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [ir para o comando](https://docs.microsoft.com/visualstudio/ide/reference/go-to-command).  
  
  
Move o cursor para a linha especificada.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
Edit.GoTo [linenumber]  
```  
  
## <a name="arguments"></a>Arguments  
 `linenumber`  
 Opcional. Um inteiro que representa o número da linha para a qual ir.  
  
## <a name="remarks"></a>Comentários  
 A numeração de linha começa em um. Se o valor de `linenumber` for menor que um, a primeira linha será exibida. Se o valor de `linenumber` for maior que o número da última linha, a última linha será exibida.  
  
 Se um valor para `linenumber` não for especificado, a caixa de diálogo **Ir para a Linha** será exibida.  
  
 O alias para esse comando é GoToLn.  
  
## <a name="example"></a>Exemplo  
  
```  
>Edit.GoTo 125  
```  
  
## <a name="see-also"></a>Consulte também  
 [Comandos do Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Janela Comando](../../ide/reference/command-window.md)   
 [Caixa Localizar/Comando](../../ide/find-command-box.md)   
 [Aliases de comando do Visual Studio](../../ide/reference/visual-studio-command-aliases.md)



