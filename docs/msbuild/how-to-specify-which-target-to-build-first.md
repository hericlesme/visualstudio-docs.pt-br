---
title: Como especificar o destino a ser compilado primeiro | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- DefaultTargets attribute [MSBuild]
- MSBuild, specifying the defalut target
- MSBuild, DefaultTargets attribute
ms.assetid: a580ba5b-2919-42d2-ae38-1af991e0205a
caps.latest.revision: "17"
author: kempb
ms.author: kempb
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: a1d5b2bbf218d35cf20638d865c6c78379c5f02b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-specify-which-target-to-build-first"></a>Como especificar o destino a ser compilado primeiro
Um arquivo de projeto pode conter um ou mais elementos `Target` que definem como o projeto é compilado. O mecanismo [!INCLUDE[vstecmsbuildengine](../msbuild/includes/vstecmsbuildengine_md.md)] ([!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]) compila o primeiro projeto e as dependências que localizar, a menos que o arquivo de projeto contenha um atributo `DefaultTargets`, um atributo `InitialTargets` ou que um destino seja especificado na linha de comando usando a opção **/target**.  
  
## <a name="using-the-initialtargets-attribute"></a>Usar o atributo InitialTargets  
 O atributo `InitialTargets` do elemento `Project` especifica um destino que será executado primeiro, mesmo se os destinos forem especificados na linha de comando ou no atributo `DefaultTargets`.  
  
#### <a name="to-specify-one-initial-target"></a>Para especificar um destino inicial  
  
-   Especifique o destino padrão no atributo `InitialTargets` do elemento `Project`. Por exemplo:  
  
     `<Project InitialTargets="Clean">`  
  
 Você pode especificar mais de um destino inicial no atributo `InitialTargets` ao listar os destinos em ordem e usar um ponto e vírgula para separar cada destino. Os destinos na lista serão executados sequencialmente.  
  
#### <a name="to-specify-more-than-one-initial-target"></a>Para especificar mais de um destino inicial  
  
-   Liste os destinos iniciais, separados por ponto e vírgula, no atributo `InitialTargets` do elemento `Project`. Por exemplo, para executar o destino `Clean` e, em seguida, o destino `Compile`, digite:  
  
     `<Project InitialTargets="Clean;Compile">`  
  
## <a name="using-the-defaulttargets-attribute"></a>Usar o atributo DefaultTargets  
 O atributo `DefaultTargets` do elemento `Project` especifica qual destino ou quais destinos serão compilados se um destino não for especificado explicitamente na linha de comando. Se os destinos estiverem especificados nos atributos `InitialTargets` e `DefaultTargets` e nenhum destino for especificado na linha de comando, o [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] executa os destinos especificados no atributo `InitialTargets` seguido pelos destinos especificados no atributo `DefaultTargets`.  
  
#### <a name="to-specify-one-default-target"></a>Para especificar um destino padrão  
  
-   Especifique o destino padrão no atributo `DefaultTargets` do elemento `Project`. Por exemplo:  
  
     `<Project DefaultTargets="Compile">`  
  
 Você pode especificar mais de um destino padrão no atributo `DefaultTargets` ao listar os destinos em ordem e usar um ponto e vírgula para separar cada destino. Os destinos na lista serão executados sequencialmente.  
  
#### <a name="to-specify-more-than-one-default-target"></a>Para especificar mais de um destino padrão  
  
-   Liste os destinos padrão, separados por ponto e vírgula, no atributo `DefaultTargets` do elemento `Project`. Por exemplo, para executar o destino `Clean` e, em seguida, o destino `Compile`, digite:  
  
     `<Project DefaultTargets="Clean;Compile">`  
  
## <a name="using-the-target-switch"></a>Usar a opção /target  
 Se um destino padrão não estiver definido no arquivo de projeto ou se você não desejar usar aquele destino padrão, você poderá usar a opção de linha de comando **/target** para especificar um destino diferente. O destino ou os destinos especificados com a opção **/target** são executados no lugar dos destinos especificados pelo atributo `DefaultTargets`. Os destinos especificados no atributo `InitialTargets` são sempre executados primeiro.  
  
#### <a name="to-use-a-target-other-than-the-default-target-first"></a>Para usar primeiro um destino diferente do destino padrão  
  
-   Especifique o destino como o primeiro destino usando a opção de linha de comando **/target**. Por exemplo:  
  
     `msbuild file.proj /target:Clean`  
  
#### <a name="to-use-several-targets-other-than-the-default-targets-first"></a>Para usar primeiro vários destinos que sejam diferentes dos destinos padrão  
  
-   Liste os destinos, separados por ponto e vírgula ou por vírgulas, usando a opção de linha de comando **/target**. Por exemplo:  
  
     `msbuild <file name>.proj /t:Clean;Compile`  
  
## <a name="see-also"></a>Consulte também
  [MSBuild](../msbuild/msbuild.md)  
 [Destinos](../msbuild/msbuild-targets.md)   
 [Como limpar um build](../msbuild/how-to-clean-a-build.md)