---
title: Use o Editor de conjunto de regra de análise de código no Visual Studio
ms.date: 04/-4/2018
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.ruleseteditor
ms.assetid: 370c97bf-bb29-4b2f-b9ae-ba125bce7b2d
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3bd9f02142b803cc9a09fce79cb687ea521dea9e
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/19/2018
---
# <a name="use-the-code-analysis-rule-set-editor"></a>Editor de conjunto de regras de análise de código de uso

O editor de conjunto de regra de análise código permite que você especifique as regras que são incluídas em um conjunto de regras personalizado e a gravidade de violações de regras.

|Ação (gravidade)|Descrição|
|-|-|
|Aviso|Gera um aviso de **lista de erros** e também em tempo de compilação.|
|Erro|Gera um erro no **lista de erros** e também em tempo de compilação.|
|Info|Gera uma mensagem no **lista de erros**.|
|Hidden|A violação não é visível para o usuário. O IDE é notificado da violação, no entanto.|
|Nenhum|A regra será suprimida. O comportamento é o mesmo como se a regra foi removida do conjunto de regras.|

O editor exibe as regras em uma estrutura de árvore que grupos de regras por uma regra de definir o campo que você especificar. Para adicionar ou remover as regras de um conjunto de regras, execute uma ou mais das seguintes etapas:

- Marque ou desmarque a caixa de seleção do nó de grupo para adicionar ou remover todas as regras do grupo. Quando você selecionar um grupo, todas as regras são definidas o **aviso** ação.

   > [!TIP]
   > Você pode alterar como as regras são agrupadas no **Agrupar por** lista suspensa.

- Clique o **ação** campo de um grupo e, em seguida, especifique a ação para aplicar a todas as regras do grupo.

- Marque ou desmarque a caixa de seleção de uma regra individual. Quando você seleciona a caixa de seleção para uma regra, a regra é definida como a ação de aviso.

## <a name="toolbar"></a>Barra de ferramentas

Você pode usar a barra de ferramentas do editor de conjunto de regras para agrupar, filtrar e pesquisar os dados que aparecem na grade de conjunto de regras.

A tabela a seguir descreve os controles na barra de ferramentas do editor de conjunto de regras.

|Controle de barra de ferramentas|Descrição|
|---------------------|-----------------|
|**Expandir tudo**|Mostra as regras em todos os grupos.|
|**Recolher tudo**|Oculta as regras em todos os grupos.|
|**Group By**|Especifica o campo pelo qual as regras são agrupadas. Clique em  **\<nenhum >** para mostrar as regras sem grupos.|
|**Opções de coluna**|Especifica os campos de regra para exibir.|
|**Ocultar as regras que não se aplicam à solução atual**|Mostra ou oculta as regras que não são do mesmo tipo de destino como a solução.|
|**Mostrar regras que podem gerar erros de análise de código**|Mostra ou oculta as regras que são atribuídas a ação de erro.|
|**Mostrar regras que podem gerar avisos de análise de código**|Mostra ou oculta as regras que são atribuídas a ação de aviso.|
|**Mostrar regras que não estão habilitadas**|Mostra ou oculta as regras que são atribuídas a nenhuma ação.|
|**Adicionar ou remover conjuntos de regras filhas**|Adiciona ou remove as regras nos conjuntos de regra selecionada.|
|**Regras de pesquisa**|Pesquisa todos os valores de campo para a cadeia de caracteres que você especificar.|

## <a name="rule-set-fields"></a>Campos de conjunto de regras

Campos de conjunto de regra exibem informações sobre um conjunto de regras e podem ser usados para classificar e agrupar a lista de regras. Para exibir ou ocultar campos, selecione **opções de coluna** na regra de conjunto de ferramentas do editor e, em seguida, marque ou desmarque as caixas de seleção dos campos para mostrar ou ocultar.

A tabela a seguir descreve os campos de um conjunto de regras:

|Campo|Descrição|
|-----------|-----------------|
|**ID**|O identificador da regra.|
|**Categoria**|Além de sua participação em conjuntos de regras, regras de análise de código também são agrupadas por categoria. Para obter mais informações, consulte [avisos de análise de código](../code-quality/code-analysis-for-managed-code-warnings.md).|
|**Nome**|O título da regra.|
|**Namespace**|O namespace da regra.|
|**Tipo de destino**|Indica se a regra é para nativo, gerenciados ou código de banco de dados.|
|**Ação**|A ação tomada quando a regra for violada em uma execução de análise de código. Você pode editar o **ação** campo.|
|**Conjuntos de regras de origem**|O conjunto de regras que contém a regra.|

## <a name="sort-and-filter-rule-sets"></a>Classificar e filtrar conjuntos de regras

De cabeçalhos de coluna da grade de conjunto de regras, você pode classificar e filtrar as regras, os valores do campo.

- Para classificar a lista de conjunto de regras, clique no cabeçalho da coluna do campo pelo qual você deseja classificar. Se os conjuntos de regras são agrupados, cada grupo é classificado individualmente.

- Para filtrar os conjuntos de regras por valor de um campo, clique no botão de filtro no cabeçalho da coluna do campo pelo qual você deseja filtrar. Marque as caixas de seleção dos valores que você deseja mostrar e desmarque as caixas de seleção dos valores que você deseja ocultar.

## <a name="see-also"></a>Consulte também

- [Criar um conjunto de regras personalizado](../code-quality/how-to-create-a-custom-rule-set.md)