---
title: Usando conjuntos de regras para especificar as regras do C++ para executar | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ac3877e6-5349-4c03-9541-3d5be259f1e8
caps.latest.revision: "5"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 5ad51388ae1580ada61442798b46048ad71ece64
ms.sourcegitcommit: fb751e41929f031d1a9247bc7c8727312539ad35
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/15/2017
---
# <a name="using-rule-sets-to-specify-the-c-rules-to-run"></a>Usando conjuntos de regras para especificar as regras do C++ para execução
Em [!INCLUDE[vsPreShort](../code-quality/includes/vspreshort_md.md)] e [!INCLUDE[vsUltShort](../code-quality/includes/vsultshort_md.md)], você pode criar e modificar um personalizado *conjunto de regras* para atender às necessidades específicas do projeto associadas com a análise de código. Para criar uma regra personalizada de C++ definido, um projeto de C/C++ deve ser aberto no IDE do Visual Studio. Você, em seguida, abra um conjunto de regras padrão no editor de conjunto de regras e, em seguida, adicionar ou remove regras específicas e, opcionalmente, altere a ação que ocorre quando a análise de código determina que uma regra que foi violada.  
  
 Para criar uma nova regra personalizada definida, você pode salvá-lo usando um novo nome de arquivo. O conjunto de regras personalizado é automaticamente atribuído ao projeto.  
  
## <a name="opening-the-rule-set-editor"></a>Abrindo a regra de editor de conjunto  
  
#### <a name="to-create-a-custom-rule-from-a-single-existing-rule-set"></a>Para criar uma regra personalizada de um único conjunto de regras existente  
  
1.  No Solution Explorer, abra o menu de atalho para o projeto e, em seguida, escolha **propriedades**.  
  
2.  Sobre o **propriedades** guia, escolha **análise de código**.  
  
3.  No **do conjunto de regras** lista suspensa, siga um destes procedimentos:  
  
    -   Escolha o conjunto de regras que você deseja personalizar.  
  
     \- ou -  
  
    -   Escolha  **\<procurar... >** para especificar uma regra existente de conjunto que não está na lista.  
  
4.  Escolha **abrir** para exibir as regras no editor de conjunto de regras.  
  
#### <a name="to-modify-a-rule-set-in-the-rule-set-editor"></a>Para modificar uma regra definida no editor de conjunto de regras  
  
-   Para alterar o nome de exibição do conjunto de regras no **exibição** menu, escolha **janela propriedades**. Digite o nome de exibição no **nome** caixa. Observe que o nome de exibição pode ser diferente do nome de arquivo.  
  
-   Para adicionar todas as regras do grupo a um conjunto de regras personalizado, selecione a caixa de seleção do grupo. Para remover todas as regras do grupo, desmarque a caixa de seleção.  
  
-   Para adicionar uma regra específica para o conjunto de regras personalizado, selecione a caixa de seleção da regra. Para remover a regra de conjunto de regras, desmarque a caixa de seleção.  
  
-   Para alterar a ação tomada quando uma regra é violada em uma análise de código, escolha o **ação** campo para a regra e, em seguida, escolha um dos seguintes valores:  
  
     **Avisar** -gera um aviso.  
  
     **Erro** -gera um erro.  
  
     **Nenhum** -desabilita a regra. Esta ação é o mesmo que remover regra do conjunto de regras.  
  
#### <a name="to-group-filter-or-change-the-fields-in-the-rule-set-editor-by-using-the-rule-set-editor-toolbar"></a>Para agrupar, filtrar ou alterar os campos no editor de conjunto de regras usando a barra de ferramentas do editor de conjunto de regras  
  
-   Para expandir as regras em todos os grupos, escolha **Expandir tudo**.  
  
-   Para recolher as regras em todos os grupos, escolha **Recolher tudo**.  
  
-   Para alterar o campo de regras são agrupadas por, escolha o campo do **Group By** lista. Para exibir as regras desagrupadas, escolha  **\<nenhum >**.  
  
-   Para adicionar ou remover campos em colunas de regra, escolha **opções de coluna**.  
  
-   Para ocultar as regras que não se aplicam à solução atual, escolha **ocultar regras que não se aplicam à solução atual**.  
  
-   Para alternar entre mostrar e ocultar as regras que são atribuídas a ação de erro, escolha **Mostrar regras que podem gerar erros de análise de código**.  
  
-   Para alternar entre mostrar e ocultar as regras que são atribuídas a ação de aviso, escolha **Mostrar regras que podem gerar avisos de análise de código**.  
  
-   Para alternar entre mostrar e ocultar as regras que são atribuídas a **nenhum** ação, escolha **Mostrar regras que não estão habilitadas**.  
  
-   Para adicionar ou remover conjuntos de regras do padrão para o conjunto de regras atual do Microsoft, escolha **adicionar ou remover conjuntos de regras filhas**.