---
title: "Comando Inspeção Rápida | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: debug.quickwatch
helpviewer_keywords:
- Quick Watch command
- Debug.Quickwatch command
ms.assetid: 9670ac3a-8f2f-4874-974d-cb87d3b0cde1
caps.latest.revision: "11"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: bad8605a2a7b9f9606c448680d583c55a2762a75
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="quick-watch-command"></a>Comando Inspeção Rápida
Exibe o texto selecionado ou especificado no campo Expressão da janela [QuickWatch](../../debugger/watch-and-quickwatch-windows.md). Você pode usar essa caixa de diálogo para calcular o valor atual de uma variável ou expressão reconhecida pelo depurador ou o conteúdo de um registro. Além disso, você pode alterar o valor de qualquer variável não const ou o conteúdo de qualquer registro.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
Debug.QuickWatchq [text]  
```  
  
## <a name="arguments"></a>Arguments  
 `text`  
 Opcional. O texto a ser adicionado à caixa de diálogo **Inspeção Rápida**.  
  
## <a name="remarks"></a>Comentários  
 Se `text` for omitido, o texto selecionado atualmente ou a palavra no cursor é adicionada à janela Inspeção.  
  
## <a name="example"></a>Exemplo  
  
```  
>Debug.QuickWatch  
```  
  
## <a name="see-also"></a>Consulte também  
 [Definir uma inspeção nas variáveis usando as janelas Inspeção e QuickWatch no Visual Studio](../../debugger/watch-and-quickwatch-windows.md)   
 [Comandos do Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Janela Comando](../../ide/reference/command-window.md)   
 [Caixa Localizar/Comando](../../ide/find-command-box.md)   
 [Aliases de comando do Visual Studio](../../ide/reference/visual-studio-command-aliases.md)