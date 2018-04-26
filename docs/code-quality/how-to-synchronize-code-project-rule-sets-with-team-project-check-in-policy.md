---
title: Como sincronizar conjuntos de regras do projeto de código com política de check-in do projeto de equipe
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.selecttfsruleset
ms.assetid: 9b02f934-2db6-41ec-aaff-9c31ceec2f04
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bcc6fe17d9f5e7666531086549eae6ad26741a22
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-synchronize-code-project-rule-sets-with-team-project-check-in-policy"></a>Como sincronizar conjuntos de regras do projeto de código com política de check-in do projeto de equipe

Você pode sincronizar as configurações de análise de código para projetos de código para a política de check-in para o projeto de equipe, especificando um conjunto de regras que contenha pelo menos as regras que são especificadas na regra definida para a política de check-in. Seu responsável desenvolvedor pode informar o nome e o local da regra definida para a política de check-in. Você pode usar uma das opções a seguir para garantir que a análise de código para o projeto usa o conjunto correto de regras:

-   Se a política de check-in usa um dos conjuntos de regra interna do Microsoft, abra a caixa de diálogo Propriedades do projeto de código, exibir a página de análise de código e selecione a regra definida na página de configurações do projeto de código da análise de código. O Microsoft conjuntos de regras padrão são instalados automaticamente com o Visual Studio são definidos como somente leitura e não deve ser editada. Se os conjuntos de regras não são editados, as regras na política e conjuntos de regra local são garantidas para corresponder.

-   Se a política de check-in usa um conjunto de regras personalizadas, execute uma operação get no arquivo de conjunto de regras no controle de versão para criar uma cópia local. Em seguida, especifica esse local local nas configurações de análise de código para o projeto de código. As regras são garantidas para correspondência se o conjunto de regras para a política de check-in é atualizado.

     Se você mapear o local do controle de versão para uma pasta local que esteja na mesma relação para a raiz do projeto de equipe do seu projeto de código, o local da regra é definido usando um caminho relativo. O caminho relativo garante que a configuração de projeto de código para análise de código pode ser movida para outros computadores.

-   Personalize uma cópia da regra definida para a política de check-in para um projeto de código. Certifique-se de que o novo conjunto de regras contém todas as regras na política de check-in e outras regras que você deseja incluir. Você deve certificar-se de que o conjunto de regras inclui todas as regras na regra definida para a política de check-in.

## <a name="to-specify-a-microsoft-standard-rule-set"></a>Para especificar uma regra padrão Microsoft definido

1.  Em **Solution Explorer**, clique com botão direito do código e, em seguida, clique em **propriedades**.

2.  Clique em **de análise de código**.

3.  No **executar esse conjunto de regras** lista, clique no conjunto de regra de política de check-in.

## <a name="to-specify-a-custom-check-in-policy-rule-set"></a>Para especificar um conjunto de regras de política de check-in personalizado

1.  Se necessário, execute uma operação get no arquivo de conjunto de regras que especifica a política de check-in.

2.  Em **Solution Explorer**, clique com botão direito do código e, em seguida, clique em **propriedades**.

3.  Clique em **de análise de código**.

4.  No **executar esse conjunto de regras** lista, clique em  **\<procurar... >**.

5.  No **abrir** caixa de diálogo, especifique o arquivo de conjunto de regra de política de check-in.

## <a name="to-create-a-custom-rule-set-for-a-code-project"></a>Para criar uma regra personalizada definida para um projeto de código

1.  Siga um dos procedimentos neste tópico para selecionar a política de check-in do projeto de equipe na página de análise de código da caixa de diálogo de configurações do projeto.

2.  Clique em **abrir**.

3.  Adicionar ou remover regras usando o [editor de conjunto de regras](../code-quality/working-in-the-code-analysis-rule-set-editor.md).

4.  Salve a regra de modificação definido como um arquivo. RuleSet no computador local ou em um caminho UNC.

5.  Abrir a caixa de diálogo Propriedades do projeto de código e exibir o **análise de código** página.

6.  No **executar esse conjunto de regras** lista, clique em  **\<procurar... >**.

7.  No **abrir** caixa de diálogo, especifique o arquivo de conjunto de regra.