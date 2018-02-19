---
title: Conceitos do MSBuild | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: msbuild
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MSBuild, concepts
ms.assetid: 083b8ba3-e4ad-45af-bb5d-3bc81d406131
caps.latest.revision: 
author: Mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: d0b0283899980fdc9748709d0b3fef049e233f45
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/09/2018
---
# <a name="msbuild-concepts"></a>Conceitos do MSBuild
[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] fornece um esquema XML básico que você pode usar para controlar como a plataforma de build compila o software. Para especificar os componentes no build e como eles devem ser compilados, use essas quatro partes do MSBuild: propriedades, itens, tarefas e destinos.  
  
## <a name="related-topics"></a>Tópicos relacionados  
  
|Título|Descrição|  
|-----------|-----------------|  
|[Propriedades MSBuild](../msbuild/msbuild-properties.md)|Introduz propriedades e coleções de propriedades. As propriedades são pares chave-valor que podem ser usados para configurar builds.|  
|[Itens do MSBuild](../msbuild/msbuild-items.md)|Apresenta os itens e as coleções de itens. Os itens são entradas no sistema de build e normalmente representam arquivos.|  
|[Destinos do MSBuild](../msbuild/msbuild-targets.md)|Explica como agrupar tarefas em uma ordem específica e habilitar seções do processo de build a ser chamado na linha de comando.|  
|[Tarefas do MSBuild](../msbuild/msbuild-tasks.md)|Mostra como criar uma unidade do código executável que pode ser usado por [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] para realizar operações de build atômicas.|  
|[Comparando propriedades e itens](../msbuild/comparing-properties-and-items.md)|Compara itens e propriedades do MSBuild. Ambos são usados para passar informações para tarefas, avaliar condições e armazenar os valores que podem ser referenciadas em todo o arquivo de projeto.|  
|[Caracteres especiais do MSBuild](../msbuild/msbuild-special-characters.md)|Explica como escapar alguns caracteres que o [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] reserva para uso especial em contextos específicos.|  
|[Passo a passo: criando um arquivo de projeto MSBuild do zero](../msbuild/walkthrough-creating-an-msbuild-project-file-from-scratch.md)|Mostra como criar um arquivo de projeto básico de forma incremental, usando somente um editor de texto.|  
|[Passo a passo: usando o MSBuild](../msbuild/walkthrough-using-msbuild.md)|Apresenta os blocos de construção do MSBuild e mostra como escrever, manipular e depurar projetos do MSBuild sem fechar o IDE (ambiente de desenvolvimento integrado) do Visual Studio.|  
|[Referência do MSBuild](../msbuild/msbuild-reference.md)|Links para documentos que contêm informações de referência.|  
|[MSBuild](../msbuild/msbuild.md)|Apresenta uma visão geral do esquema XML para um arquivo de projeto e mostra como ele controla os processos que compilam o software.|
