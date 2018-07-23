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
ms.openlocfilehash: c924a866f1bb34f41664fbf62e372b77f4d2620e
ms.sourcegitcommit: 5b767247b3d819a99deb0dbce729a0562b9654ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/20/2018
ms.locfileid: "39178231"
---
# <a name="how-to-configure-code-analysis-for-an-aspnet-web-application"></a>Como configurar a análise de código para um aplicativo Web do ASP.NET

No Visual Studio, você pode selecionar em uma lista de análise de código *conjuntos de regras* para aplicar a [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplicativo web. O conjunto de regras padrão é a regras mínimo recomendado da Microsoft. Você pode selecionar outro conjunto de regras para aplicar ao site da web.

1. Selecione o site da web **Gerenciador de soluções**.

2. Sobre o **Analyze** menu, clique em **configurar a análise de código para o Site da Web**.

3. Se você tiver selecionado a solução e a solução tem mais de um projeto, selecione a configuração e destino operacional sistema de compilação do **Configuration** e **plataforma** lista.

4. Para cada projeto na solução, clique o **do conjunto de regras** coluna e, em seguida, clique o nome da regra é definida para ser executada.

5. Por padrão, a análise de código é executada em todos os projetos na solução. Para desabilitar ou habilitar a análise de código para um projeto específico, siga estas etapas:

    1. Clique com botão direito no nome do projeto e, em seguida, clique em Propriedades.

    2. Marque ou desmarque a **Enable Code Analysis** caixa de seleção. Você também pode executar a análise de código manualmente selecionando **executar a análise de código no Site da Web** da **analisar** menu.

6. No **executar este conjunto de regras** suspensa lista, siga estas etapas:

    - Selecione o conjunto de regras que você deseja usar.

    - Selecione  **\<procurar >** especificar uma regra personalizada existente definida que não está na lista.

    - Definir um [conjunto de regras personalizado](../code-quality/how-to-create-a-custom-rule-set.md).