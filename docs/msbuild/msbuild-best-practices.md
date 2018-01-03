---
title: "Práticas recomendadas do MSBuild | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- best practices, MSBuild
- MSBuild, best practices
ms.assetid: 90ef8693-e921-410a-a377-fe4d13f58c48
caps.latest.revision: "5"
author: kempb
ms.author: kempb
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 9634fe1a0fa26d5180edc9312b925e6740bac216
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="msbuild-best-practices"></a>Práticas recomendadas do MSBuild
Recomendamos as seguintes práticas recomendadas para escrever scripts MSBuild:  
  
-   Os valores de propriedade padrão são mais facilmente tratados usando o atributo `Condition` e não declarando uma propriedade cujo valor padrão pode ser substituído na linha de comando. Por exemplo, use  
  
     `<MyProperty Condition="'$(MyProperty)' == ''">`  
  
     `MyDefaultValue`  
  
     `</MyProperty>`  
  
-   Evite curingas ao selecionar itens. Em vez disso, especifique os arquivos explicitamente. Isso torna mais fácil controlar os erros que podem ocorrer quando você adiciona ou exclui arquivos.  
  
## <a name="see-also"></a>Consulte também  
 [Conceitos avançados](../msbuild/msbuild-advanced-concepts.md)
