---
title: -Diff | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5377fedb-632a-4e86-a947-7c11c86451e7
caps.latest.revision: "2"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 14deeec64d4645135f19587997844bfdd0b18cd5
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="diff"></a>/Diff
Compara dois arquivos. As diferenças são exibidas em uma janela especial do Visual Studio.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
devenv /Diff SourceFile, TargetFile, [SourceDisplayName],[TargetDisplayName]  
```  
  
## <a name="arguments"></a>Arguments  
 `SourceFile`  
 Necessário. O caminho completo e o nome do primeiro arquivo a ser comparado.  
  
 `TargetFile`  
 Necessário. O caminho completo e o nome do segundo arquivo a ser comparado  
  
 `SourceDisplayName`  
 Opcional. O nome de exibição do primeiro arquivo.  
  
 `TargetDisplayName`  
 Opcional. O nome de exibição do segundo arquivo.