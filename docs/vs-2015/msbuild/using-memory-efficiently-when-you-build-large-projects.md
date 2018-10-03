---
title: Uso de memória com eficiência ao compilar projetos grandes | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- memory use (MSBuild)
- msbuild, efficient memory use building large trees
- caching (MSBuild)
ms.assetid: 853a21ed-69f7-4817-af00-57f73e2c74b5
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d2cb204fcfb5a96fe9833571895513dfda4449b8
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47466588"
---
# <a name="using-memory-efficiently-when-you-build-large-projects"></a>Usando memória com eficiência ao compilar projetos grandes
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [usando memória com eficiência quando você compilar projetos grandes](https://docs.microsoft.com/visualstudio/msbuild/using-memory-efficiently-when-you-build-large-projects).  
  
  
Projetos grandes geralmente contêm diversos subprojetos e outras dependências que podem consumir muita memória do sistema no momento da compilação. Quando a memória disponível no sistema é reduzida, o desempenho do sistema também pode diminuir. As versões mais antigas dos projetos [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] que permanecem na memória ou os projetos que foram removidos da versão 3.5, mas que ainda mantêm resultados da compilação em um cache para que possam ser recuperados posteriormente.  
  
 A versão 4.0 manipula esse gerenciamento de memória automaticamente, evitando que projetos usem propriedades como `UnloadProjectsOnCompletion` e `UseResultsCache`.  
  
## <a name="see-also"></a>Consulte também  
 [Compilando Vários Projetos Paralelamente](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md)



