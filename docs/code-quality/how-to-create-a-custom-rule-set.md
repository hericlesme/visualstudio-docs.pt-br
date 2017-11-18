---
title: 'Como: criar um conjunto de regras personalizado | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.codeanalysis.addremoverulesets
helpviewer_keywords: Development Edition, rule sets
ms.assetid: bcc42508-9592-4802-9f66-a50111641d73
caps.latest.revision: "24"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 7e9cba33565af81a76d043a3fc3f63eef831e1ce
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-create-a-custom-rule-set"></a>Como criar um conjunto de regras personalizado
Em [!INCLUDE[vsUltShort](../code-quality/includes/vsultshort_md.md)], [!INCLUDE[vsPreShort](../code-quality/includes/vspreshort_md.md)], e [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)], você pode criar e modificar um personalizado *conjunto de regras* para atender às necessidades específicas do projeto associadas com a análise de código. Para criar uma regra personalizada definida, abrir um ou mais padrão regra define no editor de conjunto de regras. Você pode adicionar ou remover regras específicas e você pode alterar a ação que ocorre quando a análise de código determina que uma regra que foi violada.  
  
 Para criar uma nova regra personalizada definida, você pode salvá-lo usando um novo nome de arquivo. O conjunto de regras personalizado é automaticamente atribuído ao projeto.  
  
## <a name="opening-the-rule-set-editor"></a>Abrindo a regra de editor de conjunto  
  
#### <a name="to-open-an-empty-rule-set-file-in-the-rule-set-editor"></a>Para abrir um vazio regra definir o arquivo no editor de conjunto de regras  
  
1.  Sobre o **arquivo** menu de [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)], aponte para **novo** e, em seguida, clique em **arquivo**.  
  
2.  No **novo arquivo** caixa de diálogo, clique em **geral** no **modelos instalados** e, em seguida, selecione **conjunto de regras de análise de código**.  
  
3.  Editor de conjunto de regras é exibida. Nenhuma regra estiver selecionada na lista de editor.  
  
#### <a name="to-create-a-custom-rule-from-a-single-existing-rule-set"></a>Para criar uma regra personalizada de um único conjunto de regras existente  
  
1.  No Gerenciador de soluções, clique com o botão direito e, em seguida, selecione **propriedades**.  
  
2.  Sobre o **propriedades** , clique em **análise de código**.  
  
3.  No **do conjunto de regras** lista suspensa, siga um destes procedimentos:  
  
    -   Selecione o conjunto de regras que você deseja personalizar.  
  
     \- ou -  
  
    -   Selecione  **\<procurar... >** para especificar uma regra existente de conjunto que não está na lista.  
  
4.  Clique em **abrir** para exibir as regras no editor de conjunto de regras.  
  
#### <a name="to-create-a-custom-rule-set-from-multiple-existing-rule-sets"></a>Para criar uma regra personalizada definida de vários conjuntos de regra existente  
  
1.  No Gerenciador de soluções, clique com o botão direito e, em seguida, selecione **propriedades**.  
  
2.  Sobre o **propriedades** , clique em **análise de código**.  
  
3.  Selecione  **\<escolher vários regra define... >** de **executar esse conjunto de regras**.  
  
4.  No **adicionar ou remover conjuntos de regras** caixa de diálogo, selecione os conjuntos de regras no qual você deseja basear o novo conjunto de regras e, em seguida, clique em **Okey**.  
  
5.  Salve o novo conjunto de regras.  
  
     O nome do novo conjunto de regras é selecionado no **executar esse conjunto de regras** lista. Você pode alterar o nome para exibição da regra definida na próxima etapa.  
  
6.  (Opcional) Para alterar o nome de exibição do conjunto de regras no **exibição** menu, clique em **janela propriedades**. Digite o nome de exibição no **nome** caixa.  
  
7.  Para adicionar, remover, ou modificar as regras de análise de código específico no novo conjunto de regras, clique em **abrir**.  
  
## <a name="modifying-a-rule-set"></a>Modificando um conjunto de regras  
  
#### <a name="to-modify-a-rule-set-in-the-rule-set-editor"></a>Para modificar uma regra definida no editor de conjunto de regras  
  
-   Para alterar o nome de exibição do conjunto de regras no **exibição** menu, clique em **janela propriedades**. Digite o nome de exibição no **nome** caixa. Observe que o nome de exibição pode ser diferente do nome de arquivo.  
  
-   Para adicionar todas as regras do grupo a um conjunto de regras personalizado, selecione a caixa de seleção do grupo. Para remover todas as regras do grupo, desmarque a caixa de seleção.  
  
-   Para adicionar uma regra específica para o conjunto de regras personalizado, selecione a caixa de seleção da regra. Para remover a regra de conjunto de regras, desmarque a caixa de seleção.  
  
-   Para alterar a ação tomada quando uma regra é violada em uma análise de código, clique no **ação** campo para a regra e, em seguida, selecione um dos seguintes valores:  
  
     **Avisar** -gera um aviso.  
  
     **Erro** -gera um erro.  
  
     **Nenhum** -desabilita a regra. Esta ação é o mesmo que remover regra do conjunto de regras.  
  
## <a name="changing-the-rule-set-editor-display"></a>Alterar a regra de definir a exibição do editor  
  
#### <a name="to-group-filter-or-change-the-fields-in-the-rule-set-editor-by-using-the-rule-set-editor-toolbar"></a>Para agrupar, filtrar ou alterar os campos no editor de conjunto de regras usando a barra de ferramentas do editor de conjunto de regras  
  
-   Para expandir as regras em todos os grupos, clique em **Expandir tudo**.  
  
-   Para recolher as regras em todos os grupos, clique em **Recolher tudo**.  
  
-   Para alterar o campo de regras são agrupadas por, selecione o campo do **Group By** lista. Para exibir as regras desagrupadas, selecione  **\<nenhum >**.  
  
-   Para adicionar ou remover campos em colunas de regra, clique em **opções de coluna**.  
  
-   Para ocultar as regras que não se aplicam à solução atual, **ocultar regras que não se aplicam à solução atual**.  
  
-   Para alternar entre mostrar e ocultar as regras que são atribuídas a ação de erro, clique em **Mostrar regras que podem gerar erros de análise de código**.  
  
-   Para alternar entre mostrar e ocultar as regras que são atribuídas a ação de aviso, clique em **Mostrar regras que podem gerar avisos de análise de código**.  
  
-   Para alternar entre mostrar e ocultar as regras que são atribuídas a **nenhum** ação, clique em **Mostrar regras que não estão habilitadas**.  
  
-   Para adicionar ou remover conjuntos de regras do padrão para o conjunto de regras atual do Microsoft, clique em **adicionar ou remover conjuntos de regras filhas**.  
  
## <a name="see-also"></a>Consulte também  
 [Como: configurar a análise de código para um projeto de código gerenciado](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md)   
 [Referência do conjunto de regras de análise de código](../code-quality/code-analysis-rule-set-reference.md)