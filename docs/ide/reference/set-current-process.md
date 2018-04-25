---
title: Set Current Process | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- Debug.SetCurrentProcess command
- Set Current Process command
ms.assetid: 1e016ebd-aadd-411f-a606-03bf69d3f8aa
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5ea3028be32fdccffd70f7b3d0aa9d3b4eba172c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="set-current-process"></a>Definir processo atual
Define o processo especificado como o processo ativo no depurador.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
Debug.SetCurrentProcess index  
```  
  
## <a name="arguments"></a>Arguments  
 `index`  
 Necessário. O índice do processo.  
  
## <a name="remarks"></a>Comentários  
 Você pode se conectar a vários processos quando está depurando, mas somente um processo está ativo no depurador em um determinado momento. Você pode usar o comando `SetCurrentProcess` para definir o processo ativo.  
  
## <a name="example"></a>Exemplo  
  
```  
>Debug.SetCurrentProcess 1  
```  
  
## <a name="see-also"></a>Consulte também  
 [Comandos do Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Janela Comando](../../ide/reference/command-window.md)   
 [Aliases de comando do Visual Studio](../../ide/reference/visual-studio-command-aliases.md)