---
title: "Editor de conjunto de trabalho na regra de análise de código | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.codeanalysis.ruleseteditor
ms.assetid: 370c97bf-bb29-4b2f-b9ae-ba125bce7b2d
caps.latest.revision: "12"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: d5a0fc10230c4c2b7638e1be75770872e0dcf4aa
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="working-in-the-code-analysis-rule-set-editor"></a>Trabalhando no Editor de Conjunto de Regras de Análise do Código
O editor de conjunto de regras de análise de código permite que você especifique as regras que são incluídas em um conjunto de regra personalizada e para especificar a ação. Você também pode especificar a ação a ser tomada quando a análise de código encontra uma violação da regra.  
  
|Ação|Descrição|  
|------------|-----------------|  
|**Aviso**|Gera um aviso de **lista de erros** janela.|  
|**Erro**|Gera um erro no **lista de erros** janela.|  
|**Nenhum**|Desabilita a regra.|  
  
 O editor exibe as regras em uma estrutura de árvore que grupos de regras por uma regra de definir o campo que você especificar. Para adicionar ou remover as regras de um conjunto de regras, execute uma ou mais das seguintes etapas:  
  
-   Marque ou desmarque a caixa de seleção do nó de grupo para adicionar ou remover todas as regras do grupo. Quando você selecionar um grupo, todas as regras são definidas o **aviso** ação.  
  
-   Clique o **ação** campo de um grupo e, em seguida, especifique a ação para aplicar a todas as regras do grupo.  
  
-   Marque ou desmarque a caixa de seleção de uma regra individual. Quando você seleciona a caixa de seleção para uma regra, a regra é definida como a ação de aviso.  
  
## <a name="rule-set-editor-toolbar"></a>Barra de ferramentas do Editor de conjunto de regras  
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
  
## <a name="rule-set-fields"></a>Campos de conjunto de regra  
 Exibe informações sobre uma regra definida e podem ser usadas para classificar e agrupar a lista de regras de campos do conjunto de regras. Para exibir ou ocultar campos, clique em **opções de coluna** na regra de conjunto de ferramentas do editor e, em seguida, marque ou desmarque as caixas de seleção dos campos para mostrar ou ocultar.  
  
 A tabela a seguir descreve os campos de um conjunto de regras.  
  
|Campo|Descrição|  
|-----------|-----------------|  
|**ID**|O identificador da regra.|  
|**Categoria**|Além de sua participação em conjuntos de regras, regras de análise de código também são agrupadas por categoria. Para obter mais informações, consulte [análise de código para avisos de código gerenciado](../code-quality/code-analysis-for-managed-code-warnings.md).|  
|**Nome**|O título da regra.|  
|**Namespace**|O namespace da regra.|  
|**Tipo de destino**|Indica se a regra é para nativo, gerenciados ou código de banco de dados.|  
|**Ação**|A ação tomada quando a regra for violada em uma execução de análise de código.<br /><br /> **Aviso** -gera um aviso.<br /><br /> **Erro** -gera um erro.<br /><br /> **Nenhum** -desabilita a regra.<br /><br /> Você pode editar o campo de ação. Definir o valor como None é igual a desmarcando a caixa de seleção para a regra.|  
|**Conjuntos de regras de origem**|O conjunto de regras que contém a regra.|  
  
## <a name="sorting-and-filtering-rule-sets"></a>Classificação e filtragem de conjuntos de regras  
 De cabeçalhos de coluna da grade de conjunto de regras, você pode classificar e filtrar as regras, os valores do campo.  
  
-   Para classificar a lista de conjunto de regras, clique no cabeçalho da coluna do campo pelo qual você deseja classificar. Se os conjuntos de regras são agrupados, cada grupo é classificado individualmente.  
  
-   Para filtrar os conjuntos de regras por valor de um campo, clique no botão de filtro no cabeçalho da coluna do campo pelo qual você deseja filtrar. Marque as caixas de seleção dos valores que você deseja mostrar e desmarque as caixas de seleção dos valores que você deseja ocultar.