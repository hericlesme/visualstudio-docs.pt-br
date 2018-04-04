---
title: 'Como: configurar a análise de código para um projeto de código gerenciado | Microsoft Docs'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: article
f1_keywords:
- vs.codeanalysis.propertypages.csvb
helpviewer_keywords:
- code analysis, selecting rule sets
- code analysis, rule sets
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- dotnet
ms.openlocfilehash: 46d41b09f0f6639195613c8a4d9a08f952c79525
ms.sourcegitcommit: efd8c8e0a9ba515d47efcc7bd370eaaf4771b5bb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/03/2018
---
# <a name="how-to-configure-code-analysis-for-a-managed-code-project"></a>Como configurar a análise de código para um projeto de código gerenciado

No Visual Studio, você pode escolher de uma lista de análise de código *conjuntos de regras* para aplicar a um projeto de código gerenciado. O conjunto de regras padrão é *Microsoft mínimo recomendado regras*. Você pode aplicar outra regra definida para um projeto ou para todos os projetos em uma solução.

> [!TIP]
> Para obter informações sobre como configurar uma conjunto de regras para aplicativos Web ASP.NET, consulte [como: configurar a análise de código para um aplicativo Web ASP.NET](../code-quality/how-to-configure-code-analysis-for-an-aspnet-web-application.md).

## <a name="to-configure-a-rule-set-for-a-net-framework-project"></a>Para configurar uma regra definida para um projeto do .NET Framework

1. Abra o **análise de código** guia nas páginas de propriedades do projeto. Você pode fazer isso em qualquer uma das seguintes maneiras:

   - Em **Solution Explorer**, selecione o projeto. Na barra de menus, selecione **analisar** > **configurar a análise de código** > **para \<projectname >**.

   - Clique com botão direito no projeto no **Solution Explorer** e selecione **propriedades**e, em seguida, selecione o **análise de código** guia.

1. No **configuração** e **plataforma** listas, selecione a plataforma de destino e a configuração de compilação.

1. Para executar a análise de código toda vez que o projeto é compilado usando a configuração selecionada, selecione o **habilitar análise de código no Build** caixa de seleção. Você também pode executar a análise de código manualmente selecionando **analisar** > **executar análise de código** > **executar análise de código em \<projectname >**.

1. Por padrão, a análise de código não relata avisos de código que é gerado automaticamente por ferramentas externas. Para exibir avisos do código gerado, desmarque o **Suprimir resultados do código gerado** caixa de seleção.

    > [!NOTE]
    > Essa opção suprime erros de análise de código e avisos do código gerado quando os erros e avisos aparecem em formulários e modelos. Você pode exibir e manter o código-fonte para um formulário ou um modelo, sem ter substituído.

1. No **executar esse conjunto de regras** lista, siga um destes procedimentos:

    - Selecione o conjunto de regras que você deseja usar.

    - Selecione  **\<procurar... >** para localizar uma regra personalizada existente definida que não está na lista.

    - Defina um conjunto de regra personalizada. Para obter mais informações, consulte [criando conjuntos de regras personalizado](../code-quality/creating-custom-code-analysis-rule-sets.md).

## <a name="see-also"></a>Consulte também

- [Passo a passo: configurando e usando um conjunto de regras personalizado](../code-quality/walkthrough-configuring-and-using-a-custom-rule-set.md)
- [Como configurar a análise de código para um Aplicativo Web ASP .NET](../code-quality/how-to-configure-code-analysis-for-an-aspnet-web-application.md)