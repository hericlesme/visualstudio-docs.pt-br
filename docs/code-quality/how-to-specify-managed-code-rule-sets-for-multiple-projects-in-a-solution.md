---
title: "Como: especificar conjuntos de regras de código gerenciado para vários projetos em uma solução | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.codeanalysis.propertypages.solution
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- dotnet
ms.openlocfilehash: e0b6a2864340f87702b765f49605ebdb3aaa555c
ms.sourcegitcommit: bfa26fd7426af0d065cb2eef3d6827b5d6f7986c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/20/2018
---
# <a name="how-to-specify-managed-code-rule-sets-for-multiple-projects-in-a-solution"></a>Como especificar conjuntos de regras de código gerenciado para vários projetos em uma solução

Por padrão, todos os projetos gerenciados de uma solução são atribuídos a análise de código Microsoft mínimo recomendado regras *conjunto de regras*. Você pode alterar os conjuntos de regras que são atribuídos aos projetos de uma solução na caixa de diálogo Propriedades da solução.

> [!NOTE]
> Por padrão, a análise de código do projeto não é executada como uma etapa de compilação. Para habilitar a análise de código como uma etapa de compilação, consulte [como: configurar a análise de código para um projeto de código gerenciado](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md).

1. Abra a solução no Visual Studio.

2. Sobre o **analisar** menu, clique em **configurar a análise de código para solução**.

3. Se necessário, expanda **propriedades comuns**e, em seguida, clique em **configurações de análise de código**.

4. Você pode especificar uma regra definida para um ou mais projetos.

    - Para especificar uma regra definida para um projeto individual, clique no nome do projeto.

    - Para especificar uma regra definida para vários projetos, mantenha pressionada a tecla CTRL e clique nos nomes de projeto.

    - Para especificar todos os projetos na solução, mantenha pressionada a tecla SHIFT e clique na lista de projetos.

5. Clique o **do conjunto de regras** campo de um projeto e, em seguida, clique o nome da regra de conjunto que você deseja aplicar.