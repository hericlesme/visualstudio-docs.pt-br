---
title: Configurar a análise de código no Visual Studio | Microsoft Docs
ms.date: 04/04/2018
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.propertypages.csvb
- vs.codeanalysis.propertypages.solution
helpviewer_keywords:
- code analysis, selecting rule sets
- code analysis, rule sets
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- dotnet
ms.openlocfilehash: daac3af3a6d5d5fba4d6e8dbb652821583769762
ms.sourcegitcommit: 3b692c9bf332b7b9150901e16daf99a64b599fee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/10/2018
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

    - Definir um [conjunto de regras personalizado](../code-quality/how-to-create-a-custom-rule-set.md).

## <a name="specify-rule-sets-for-multiple-projects-in-a-solution"></a>Especificar os conjuntos de regras para vários projetos em uma solução

Por padrão, todos os projetos gerenciados de uma solução são atribuídos a *Microsoft mínimo recomendado regras* conjunto de regras de análise de código. Você pode alterar os conjuntos de regras que são atribuídos aos projetos de uma solução no **propriedades** caixa de diálogo para a solução.

1. Abra a solução no Visual Studio.

2. Sobre o **analisar** menu, selecione **configurar a análise de código para solução**.

3. Se necessário, expanda **propriedades comuns**e, em seguida, selecione **configurações de análise de código**.

4. Você pode especificar uma regra definida para um ou mais projetos:

    - Para especificar uma regra definida para um projeto individual, selecione o nome do projeto.

    - Para especificar uma regra definida para vários projetos, mantenha pressionada **Ctrl** e selecione os nomes de projeto.

    - Para especificar todos os projetos na solução, mantenha pressionada **Shift** e clique na lista de projetos.

5. Selecione o **do conjunto de regras** campo de um projeto e, em seguida, selecione o nome da regra definido que você deseja aplicar.

## <a name="see-also"></a>Consulte também

- [Como configurar a análise de código para um Aplicativo Web ASP .NET](../code-quality/how-to-configure-code-analysis-for-an-aspnet-web-application.md)