---
title: Criar ou atualizar políticas de seleção da análise de código padrão
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.policyeditor
helpviewer_keywords:
- code analysis, migrating check-in policy
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 96fa2dd75c590e0841d7479e4e071154add04857
ms.sourcegitcommit: 33c954fbc8e05f7ba54bfa2c0d1bc1f9bbc68876
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2018
---
# <a name="how-to-create-or-update-standard-code-analysis-check-in-policies"></a>Como criar ou atualizar políticas de check-in de análise do código padrão

Você pode exigir que a análise de código seja executada em todos os projetos de código em um projeto de equipe usando a análise de código check-in de política. Necessidade de análise de código pode melhorar a qualidade do código que é verificada para a base de código.

> [!NOTE]
> Este recurso está disponível apenas se você estiver usando o Team Foundation Server.

Políticas do check-in de análise de código são definidas nas configurações do projeto de equipe e se aplicam a cada projeto de código no projeto de equipe. Análise de código é executado é configurado para projetos de código no arquivo de projeto (.xxproj) para o projeto de código. Análise de código é executado é executado no computador local. Quando você habilitar uma política de check-in do analysis código, arquivos em um projeto de código que fazem check-in devem ser compilados após sua última edição e uma análise de código que contém, no mínimo, as regras nas configurações do projeto de equipe devem ser executadas no computador onde o c alterações foram feitas.

- Para código gerenciado, você deve definir a política de check-in, especificando um *conjunto de regras* que contém um subconjunto das regras de análise de código.

- Para código C/C++, no Visual Studio 2017 versão 15.6 e anteriores, a política de check-in requer que todas as regras de análise de código serão executadas. Você pode adicionar as diretivas de pré-processador para desabilitar regras específicas para os projetos de código individuais em seu projeto de equipe. No 15,7 e posterior, você pode usar **/ANALYZE: ruleset** para especificar quais regras a serem executadas. Para obter mais informações, consulte [usando conjuntos de regras para especificar as regras do C++ para executar](using-rule-sets-to-specify-the-cpp-rules-to-run.md).

Depois de especificar uma política de check-in para código gerenciado, os membros da equipe podem sincronizar suas configurações de análise de código para projetos de código para as configurações de política de projeto de equipe.

## <a name="to-open-the-check-in-policy-editor"></a>Para abrir o editor de política de check-in

1. No Team Explorer, clique com botão direito no nome do projeto de equipe, aponte para **as configurações de projeto de equipe**e, em seguida, clique em **controle de origem**.

1. No **controle de origem** caixa de diálogo, selecione o **política de Check-in** guia.

1. Realize um dos seguintes procedimentos:

    - Clique em **adicionar** para criar uma nova política de check-in.

    - Clique duas vezes em existente **análise de código** item o **tipo de política** lista para alterar a política.

## <a name="to-set-policy-options"></a>Para definir opções de política

Marque ou desmarque as opções a seguir:

|Opção|Descrição|
|------------|-----------------|
|**Impor check-in para conter somente os arquivos que fazem parte da solução atual.**|Análise de código pode executar somente em arquivos especificados em arquivos de configuração de solução e projeto. Essa política garante que todo o código que faz parte de uma solução é analisado.|
|**Impor análise de código C/C++ (/Analyze)**|Requer que todos os projetos C ou C++ ser criado com a / opção analyze do compilador para executar a análise de código antes que eles podem fazer check-in.|
|**Impor análise de código para código gerenciado**|Requer que todos os projetos gerenciados executar análise de código e compilar antes que eles podem fazer check-in.|

## <a name="to-specify-a-managed-rule-set"></a>Para especificar um conjunto de regras gerenciado

Do **executar esse conjunto de regras** lista, use um dos seguintes métodos:

- Selecione um conjunto de regras padrão do Microsoft.

- Selecione uma regra personalizada definida clicando  **\<Selecionar conjunto de regras de controle de origem... >**. Em seguida, digite o caminho de controle de versão da regra definida no navegador de controle do código-fonte. A sintaxe de um caminho de controle de versão é:

   **$/** `TeamProjectName` **/** `VersionControlPath`

Para obter mais informações sobre como criar e implementar uma regra de política de check-in personalizado definido, consulte [políticas de Check-in implementar personalizadas para código gerenciado](../code-quality/implementing-custom-code-analysis-check-in-policies-for-managed-code.md).

## <a name="see-also"></a>Consulte também

- [Criar e usar as políticas do check-in de análise de código](../code-quality/creating-and-using-code-analysis-check-in-policies.md)