---
title: "Como: configurar a análise de código para um projeto de código gerenciado | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.codeanalysis.propertypages.csvb
helpviewer_keywords:
- code analysis, selecting rule sets
- code analysis, rule sets
ms.assetid: 618f6ff3-db0e-46cb-b08d-dfa35e62c9e7
caps.latest.revision: "33"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: dotnet
ms.openlocfilehash: 134645ced3352d820165b23a73308894fed0897a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-configure-code-analysis-for-a-managed-code-project"></a>Como configurar a análise de código para um projeto de código gerenciado
Em [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)] e [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)], você pode escolher de uma lista de análise de código *conjuntos de regras* para aplicar a um projeto de código gerenciado. O conjunto de regras padrão é o Microsoft mínimo recomendado regras. Você pode aplicar outra regra definida para um projeto ou para todos os projetos em uma solução.  
  
> [!NOTE]
>  Para obter informações sobre como configurar uma conjunto de regras para aplicativos Web ASP.NET, consulte [como: configurar a análise de código para um aplicativo Web ASP.NET](../code-quality/how-to-configure-code-analysis-for-an-aspnet-web-application.md).  
  
### <a name="to-configure-a-rule-set-for-a-net-framework-project"></a>Para configurar uma regra definida para um projeto do .NET Framework  
  
1.  Em **Solution Explorer**, clique no projeto.  
  
2.  Sobre o **analisar** menu, clique em **configurar a análise de código para** *ProjectName*.  
  
3.  No **configuração** e **plataforma** listas, clique a plataforma de destino e a configuração de compilação.  
  
4.  Para executar a análise de código toda vez que o projeto é compilado usando a configuração selecionada, selecione o **habilitar análise de código no Build (define a constante CODE_ANALYSIS)** caixa de seleção. Você também pode executar a análise de código manualmente abrindo o **analisar** menu e clicando em **executar análise de código em** *ProjectName*.  
  
5.  Por padrão, a análise de código não relata avisos de código que é gerado automaticamente por ferramentas externas. Para exibir avisos do código gerado, desmarque o **Suprimir resultados do código gerado** caixa de seleção.  
  
    > [!NOTE]
    >  Essa opção suprime erros de análise de código e avisos do código gerado quando os erros e avisos aparecem em formulários e modelos. Você pode exibir e manter o código-fonte para um formulário ou um modelo.  
  
6.  No **executar esse conjunto de regras** lista, siga um destes procedimentos:  
  
    -   Clique o conjunto de regras que você deseja usar.  
  
    -   Clique em  **\<procurar... >** para especificar uma regra personalizada existente de conjunto que não está na lista.  
  
    -   Defina um conjunto de regra personalizada.  
  
         Para obter mais informações, consulte [criando conjuntos de regras personalizado](../code-quality/creating-custom-code-analysis-rule-sets.md).  
  
## <a name="see-also"></a>Consulte também  
 [Passo a passo: configurando e usando um conjunto de regras personalizado](../code-quality/walkthrough-configuring-and-using-a-custom-rule-set.md)