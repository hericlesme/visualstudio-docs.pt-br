---
title: "Melhorando a qualidade do código com políticas de Check-in do projeto de equipe | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- code quality, using check-in policies
- team-based development, enhancing code quality
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: c82bc929fa7633719c06569cb3dded5df651a349
ms.sourcegitcommit: d6327b978661c0a745bf4b59f32d8171607803a3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/01/2018
---
# <a name="enhancing-code-quality-with-team-project-check-in-policies"></a>Melhorando a qualidade do código com políticas de check-in do projeto de equipe

Quando você usa o controle de versão de base da equipe (TFVC), você pode criar políticas de check-in para seus projetos de equipe. para impor práticas que levam ao código melhor e mais eficiente do desenvolvimento de grupo. Políticas de check-in são regras que são definidas no nível de projeto de equipe e aplicadas em computadores de desenvolvedor antes que o código tem permissão para fazer check-in.

Você pode especificar essas políticas de check-in do projeto equipe:

- **Cria**: requer que quebras de compilação que foram criadas durante uma compilação devem ser corrigidas antes de um novo check-in.

- **Comentários de conjunto de alterações**: requer que os usuários forneçam comentários ao fazer check-in de alterações.

- **Análise de código**: requer que a análise de código é executada antes do check-in.

- **Itens de trabalho**: requer que um ou mais itens de trabalho pode ser associado a seleção-no.

> [!IMPORTANT]
> Para usar políticas de check-in, você deve estar conectado ao [!INCLUDE[vststfsLong](../code-quality/includes/vststfslong_md.md)].

## <a name="common-tasks"></a>Tarefas comuns

|Tarefa|Conteúdo de suporte|
|----------|------------------------|
|**Criar e usar as políticas do check-in de análise de código:** você pode escolher um conjunto padrão de regras de análise de código, ou você pode criar um conjunto personalizado.|[Criando e usando políticas de check-in de análise de código](../code-quality/creating-and-using-code-analysis-check-in-policies.md)|

## <a name="related-tasks"></a>Tarefas relacionadas

|Tarefa|Conteúdo de suporte|
|----------|------------------------|
|**Use a análise de código no processo de desenvolvimento:** membros da equipe executam análise de código em seus computadores de desenvolvimento. No Visual Studio, os desenvolvedores de configurar e executar análise de código é executado para projetos de código individuais, exibir em analisar problemas encontrados pelo é executado e criar itens de trabalho para avisos.|[Analisando a qualidade do aplicativo](../code-quality/analyzing-application-quality-by-using-code-analysis-tools.md)|
|**Criar e executar testes de unidade:** testes de unidade dão aos desenvolvedores e testadores uma forma rápida de procurar erros lógicos nos métodos de classes em projetos c#, Visual Basic e C++. Um teste de unidade pode ser criado uma vez e pode ser executado toda vez que o código fonte é alterado para certificar-se de que nenhum bugs foram introduzidos.|[Efetuar teste de unidade em seu código](../test/unit-test-your-code.md)|
|**Acompanhar itens de trabalho e defeitos:** você pode usar itens de trabalho para controlar e gerenciar seu trabalho e informações sobre seu projeto de equipe. Um item de trabalho é um banco de dados de registro [!INCLUDE[esprfound](../code-quality/includes/esprfound_md.md)] usa para controlar a atribuição e o andamento do trabalho. Você pode usar tipos diferentes de itens de trabalho para acompanhar diferentes tipos de trabalho, como requisitos de cliente, bugs de produto e tarefas de desenvolvimento.|[Itens de trabalho (VSTS)](/vsts/work/work-items/index)|

## <a name="external-resources"></a>Recursos externos

[Testing for Continuous Delivery with Visual Studio 2012 - Chapter 2: Unit Testing: Testing the Inside](http://go.microsoft.com/fwlink/?LinkID=255188) (Testando para entrega contínua com o Visual Studio 2012 – Capítulo 2: Teste de unidade: testando o interior)