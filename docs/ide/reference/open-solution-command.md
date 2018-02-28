---
title: "Comando Abrir Solução | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- file.opensolution
helpviewer_keywords:
- Open Solution command
- File.OpenSolution command
ms.assetid: 61de76c8-69d7-4cdb-b605-e132f45d05d9
caps.latest.revision: 
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: a67e3884fbb5e0c4bbb3a5aefe2cdcc8ac7d683e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="open-solution-command"></a>Comando Abrir Solução
Abre uma solução existente, fechando outras soluções abertas.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
File.OpenSolution filename  
```  
  
## <a name="arguments"></a>Arguments  
 `Filename`  
 Necessário. O caminho completo e o nome de arquivo da solução a ser aberta.  
  
 A sintaxe para o argumento `filename` requer que os caminhos que contêm espaços usem aspas.  
  
## <a name="remarks"></a>Comentários  
 O preenchimento automático tenta localizar o caminho e o nome do arquivo corretos enquanto você digita.  
  
## <a name="example"></a>Exemplo  
 Este exemplo abre a solução, Test1.sln.  
  
```  
>File.OpenSolution "c:\MySolutions\Test1\Test1.sln"  
```  
  
## <a name="see-also"></a>Consulte também  
 [Comandos do Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Janela Comando](../../ide/reference/command-window.md)   
 [Caixa Localizar/Comando](../../ide/find-command-box.md)   
 [Aliases de comando do Visual Studio](../../ide/reference/visual-studio-command-aliases.md)