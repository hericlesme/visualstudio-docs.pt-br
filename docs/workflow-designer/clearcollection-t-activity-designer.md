---
title: ClearCollection&lt;T&gt; Designer de atividade | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.ClearCollection`1.UI
ms.assetid: db0e5da2-7b5a-4f1a-864c-f3aeeeeb51a7
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 6f4a89d062fe8adeb06c05ba25929bce6d466511
ms.sourcegitcommit: 37c87118f6f41e832da96f21f6b4cc0cf8fee046
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2018
---
# <a name="clearcollectionlttgt-activity-designer"></a>ClearCollection&lt;T&gt; Designer de atividade
O **ClearCollection\<T >** designer de atividade é usado para criar e configurar um <xref:System.Activities.Statements.ClearCollection%601> atividade.

## <a name="the-clearcollectiont-activity"></a>O ClearCollection < T\> atividade
 A atividade de <xref:System.Activities.Statements.ClearCollection%601> limpa especificada uma coleção de todos os itens.

### <a name="using-the-clearcollectiont-activity-designer"></a>Usando o ClearCollection\<T > Designer de atividade
 O **ClearCollection\<T >** designer de atividade pode ser encontrado no **coleção** categoria do **caixa de ferramentas**, que é acessado clicando o  **Caixa de ferramentas** guia do [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] (como alternativa, selecione **barra de ferramentas** do **exibição** menu ou CTRL + ALT + X.)

 O **ClearCollection\<T >** designer de atividades pode ser arrastado o **caixa de ferramentas** e removidos no [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] superfície onde quer que as atividades geralmente são colocados, tais como dentro um <xref:System.Activities.Statements.Sequence>. Isso cria uma <xref:System.Activities.Statements.ClearCollection%601> atividade com um padrão <xref:System.Activities.Activity.DisplayName%2A> de ClearCollection < Int32\>. (Por padrão, o *TypeArgument* é **Int32**. Isso pode ser alterado na grade de propriedade.) O <xref:System.Activities.Activity.DisplayName%2A> valor pode ser editado no cabeçalho do **ClearCollection < T\>**  designer de atividade ou o **DisplayName** caixa da grade de propriedade. Outras propriedades devem ser editadas na grade de propriedade.

### <a name="the-clearcollectiont-properties"></a>O ClearCollection < T\> propriedades
 A tabela a seguir mostra as propriedades de <xref:System.Activities.Statements.ClearCollection%601> e descreve como elas são usadas no designer.

|Nome da Propriedade|Necessária|Uso|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Especifica o nome amigável opcional de atividade de <xref:System.Activities.Statements.ClearCollection%601> . O padrão é ClearCollection < Int32\>. Embora o valor de <xref:System.Activities.Activity.DisplayName%2A> não é necessário restrita, é uma prática recomendada usar um.|
|<xref:System.Activities.Statements.ClearCollection%601.Collection%2A>|verdadeiro|Especifica a coleção a ser limpa os itens. Essa coleção é do tipo **ICollection\<TypeArgument >.** Para especificar a coleção, digite uma expressão do Visual Basic na grade de propriedade.|
|*TypeArgument*|verdadeiro|Especifica o tipo T de itens contidos em <xref:System.Collections.Generic.ICollection%601>. Por padrão, isso *TypeArgument* tipo é definido como **Int32**. Para alterar o tipo, altere o valor de *TypeArgument* na caixa de combinação na grade de propriedades.|

## <a name="see-also"></a>Consulte também

- [Coleção](../workflow-designer/collection-activity-designers.md)
- [AddToCollection\<T>](../workflow-designer/addtocollection-t-activity-designer.md)
- [ExistsInCollection\<T>](../workflow-designer/existsincollection-t-activity-designer.md)
- [RemoveFromCollection\<T>](../workflow-designer/removefromcollection-t-activity-designer.md)