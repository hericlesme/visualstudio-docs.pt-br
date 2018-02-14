---
title: "Como compilar destinos específicos em soluções usando o MSBuild.exe | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: msbuild
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MSBuild, building specific targets in a solution
- msbuild.exe, building specific targets in a solution
- MSBuild, msbuild.exe
ms.assetid: f46feb9b-4c16-4fec-b6e1-36a959692ba3
caps.latest.revision: 
author: Mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 66ec27d619b64353bf0cbac6a8b92c582ef5a590
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/09/2018
---
# <a name="how-to-build-specific-targets-in-solutions-by-using-msbuildexe"></a>Como compilar destinos específicos em soluções usando o MSBuild.exe
Você pode usar MSBuild.exe para compilar destinos específicos de projetos específicos em uma solução.  
  
### <a name="to-build-a-specific-target-of-a-specific-project-in-a-solution"></a>Para criar um destino específico de um projeto específico em uma solução  
  
1.  Na linha de comando, digite `MSBuild.exe <SolutionName>.sln`, em que `<SolutionName>` corresponde ao nome de arquivo da solução que contém o destino que você deseja executar.  
  
2.  Especifique o destino após o comutador **/t** no formato *ProjectName*:*TargetName*.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir executa o destino `Rebuild` do projeto `NotInSlnFolder` e, em seguida, executa o destino `Clean` do projeto `InSolutionFolder`, que está localizado na pasta da solução `NewFolder`.  
  
```  
msbuild SlnFolders.sln /t:NotInSlnfolder:Rebuild;NewFolder\InSolutionFolder:Clean  
```  
  
## <a name="see-also"></a>Consulte também  
 [Referência de linha de comando](../msbuild/msbuild-command-line-reference.md)   
 [Referência do MSBuild](../msbuild/msbuild-reference.md)   
 [ MSBuild](../msbuild/msbuild.md)  
 [Conceitos do MSBuild](../msbuild/msbuild-concepts.md)