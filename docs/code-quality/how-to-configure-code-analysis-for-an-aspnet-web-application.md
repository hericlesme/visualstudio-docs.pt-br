---
title: 'Como: configurar a análise de código para um aplicativo Web ASP.NET no Visual Studio'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.propertypages.asp
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- aspnet
ms.openlocfilehash: bb1adaf9e97a950c6e9c53b3734debf5588fe0b9
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31919943"
---
# <a name="how-to-configure-code-analysis-for-an-aspnet-web-application"></a>Como configurar a análise de código para um aplicativo Web do ASP.NET

No Visual Studio, você pode selecionar em uma lista de análise de código *conjuntos de regras* para aplicar a [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplicativo Web. O conjunto de regras padrão é o Microsoft mínimo recomendado regras. Você pode selecionar outra conjunto de regras para aplicar ao site da Web.

1. Selecione o site da Web **Gerenciador de soluções**.

2. Sobre o **analisar** menu, clique em **configurar a análise de código para o Site da Web**.

3. Se você selecionou a solução e a solução tem mais de um projeto, selecione a compilação destino e configuração do sistema operacional no **configuração** e **plataforma** lista.

4. Para cada projeto na solução, clique o **do conjunto de regras** coluna e, em seguida, clique em definir o nome da regra para executar.

5. Por padrão, a análise de código é executada em todos os projetos na solução. Para desabilitar ou habilitar análise de código para um projeto específico, siga estas etapas:

    1. Clique no nome do projeto e, em seguida, clique em Propriedades.

    2. Marque ou desmarque o **habilitar análise de código** caixa de seleção. Você também pode executar a análise de código manualmente selecionando **executar análise de código no Site** do **analisar** menu.

6. No **executar esse conjunto de regras** suspensa lista, siga estas etapas:

    - Selecione o conjunto de regras que você deseja usar.

    - Selecione  **\<procurar >** para especificar uma regra personalizada existente de conjunto que não está na lista.

    - Definir um [conjunto de regras personalizado](../code-quality/how-to-create-a-custom-rule-set.md).