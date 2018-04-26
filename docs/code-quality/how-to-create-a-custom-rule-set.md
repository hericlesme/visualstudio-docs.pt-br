---
title: Criar uma regra de análise de código personalizado definida no Visual Studio
ms.date: 04/04/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.addremoverulesets
helpviewer_keywords:
- Development Edition, rule sets
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a3b1d9b436c3e3be4f241d18791744085be4ece9
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="custom-rule-sets"></a>Conjuntos de regras personalizados

Você pode criar um personalizado *conjunto de regras* para atender às necessidades de análise de código.

## <a name="create-a-custom-rule-set"></a>Criar um conjunto de regras personalizado

Para criar uma regra personalizada definida, você pode abrir uma conjunto de regras internas do **editor de conjunto de regras**. A partir daí, você pode adicionar ou remover regras específicas, e você pode alterar a ação que ocorre quando uma regra é violada&mdash;Mostrar, por exemplo, um aviso ou erro.

1. Em **Solution Explorer**, clique com o botão direito e, em seguida, selecione **propriedades**.

2. Sobre o **propriedades** páginas, selecionadas o **análise de código** guia.

3. No **executar esse conjunto de regras** lista suspensa, siga um destes procedimentos:

    - Selecione o conjunto de regras que você deseja personalizar.

     \- ou -

    - Selecione  **\<procurar... >** para especificar uma regra existente de conjunto que não está na lista.

4. Selecione **abrir** para exibir as regras no editor de conjunto de regras.

Você também pode criar um novo arquivo de conjunto de regras do **novo arquivo** caixa de diálogo:

1. Selecione **arquivo** > **novo** > **arquivo**, ou pressione **Ctrl**+**N**.

2. No **novo arquivo** caixa de diálogo, selecione o **geral** categoria à esquerda e, em seguida, selecione **conjunto de regras de análise de código**.

3. Selecione **Abrir**.

   O novo *. RuleSet* arquivo é aberto no editor de conjunto de regras.

### <a name="create-a-custom-rule-set-from-multiple-rule-sets"></a>Criar uma regra personalizada definida de vários conjuntos de regra

1. No Gerenciador de soluções, clique com o botão direito e, em seguida, selecione **propriedades**.

2. Sobre o **propriedades** páginas, selecionadas o **análise de código** guia.

3. Selecione  **\<escolher vários regra define... >** de **executar esse conjunto de regras**.

4. No **adicionar ou remover conjuntos de regras de** caixa de diálogo, selecione os conjuntos de regras deseja incluir em seu novo conjunto de regras.

   ![Adicionar ou remover a caixa de diálogo de conjuntos de regra](media/add-remove-rule-sets.png)

5. Selecione **Salvar como**, insira um nome para o *. RuleSet* de arquivo e, em seguida, selecione **salvar**.

   O novo conjunto de regras está selecionado no **executar esse conjunto de regras** lista.

6. Selecione **abrir** para abrir a nova regra definida no editor de conjunto de regras.

## <a name="name-and-description"></a>Nome e descrição

Para alterar o nome de exibição de um conjunto de regras que é aberto no editor, abra o **propriedades** selecionando **exibição** > **janela propriedades** na barra de menus. Digite o nome de exibição no **nome** caixa. Você também pode inserir uma descrição para o conjunto de regras.

## <a name="next-steps"></a>Próximas etapas

Agora que você tiver uma regra definida, a próxima etapa é personalizar as regras, adicionando ou removendo regras ou modificando a gravidade de violações de regras.

> [!div class="nextstepaction"]
> [Modificar as regras no editor de conjunto de regras](../code-quality/working-in-the-code-analysis-rule-set-editor.md)

## <a name="see-also"></a>Consulte também

- [Como configurar a análise de código para um projeto de código gerenciado](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md)
- [Referência do conjunto de regras de análise de código](../code-quality/rule-set-reference.md)