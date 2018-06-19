---
title: Designer de fluxo de trabalho - AddToCollection<T> Designer de atividade
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Statements.AddToCollection`1.UI
ms.assetid: f7fc0702-164e-4370-8946-bb2f9f9384b7
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2b32df48f79d60500cb23a40c5273ceeedfc9c56
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31976696"
---
# <a name="addtocollectiont-activity-designer"></a>AddToCollection\<T > Designer de atividade

O **AddToCollection\<T >** designer de atividade é usado para criar e configurar um <xref:System.Activities.Statements.AddToCollection%601> atividade.

## <a name="the-addtocollectiont-activity"></a>O AddToCollection\<T > atividade

A atividade de <xref:System.Activities.Statements.AddToCollection%601> adiciona um item a uma coleção.

### <a name="using-the-addtocollectiont-activity-designer"></a>Usando o AddToCollection\<T > Designer de atividade

O **AddToCollection\<T >** designer de atividade pode ser encontrado no **coleção** categoria do **caixa de ferramentas**, que é acessado clicando o  **Caixa de ferramentas** guia do Designer de fluxo de trabalho (como alternativa, selecione **barra de ferramentas** do **exibição** menu ou CTRL + ALT + X.)

O **AddToCollection\<T >** designer de atividades pode ser arrastado do **caixa de ferramentas** e descartado para a superfície do Designer de fluxo de trabalho onde quer que as atividades são colocados, tais como dentro de um <xref:System.Activities.Statements.Sequence>. Descartando o **AddToCollection\<T >** designer de atividade cria um <xref:System.Activities.Statements.AddToCollection%601> atividade com um padrão <xref:System.Activities.Activity.DisplayName%2A> de AddToCollection < Int32\>. (Por padrão, o *TypeArgument* é **Int32**. TypeArgument pode ser alterada na grade de propriedades.) O <xref:System.Activities.Activity.DisplayName%2A> valor pode ser editado no cabeçalho do **AddToCollection < T\>**  designer de atividade ou o **DisplayName** caixa da grade de propriedade. Outras propriedades devem ser editadas na grade de propriedade.

### <a name="the-addtocollectiont-properties"></a>O AddToCollection\<T > Propriedades

A tabela a seguir mostra as propriedades de <xref:System.Activities.Statements.AddToCollection%601> e descreve como elas são usadas no designer.

|Nome da Propriedade|Necessária|Uso|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|O nome amigável de atividade de <xref:System.Activities.Statements.AddToCollection%601> . O padrão é AddToCollection < Int32\>. Embora o valor de <xref:System.Activities.Activity.DisplayName%2A> não é necessário restrita, é uma prática recomendada usar um.|
|<xref:System.Activities.Statements.AddToCollection%601.Item%2A>|verdadeiro|O item a ser adicionado à coleção\<T >. Este item é do tipo *T*, que é do tipo *TypeArgument*. Para especificar o item, digite uma expressão do Visual Basic na grade de propriedade.|
|<xref:System.Activities.Statements.AddToCollection%601.Collection%2A>|verdadeiro|A coleção para que o item deve ser adicionado. Essa coleção é do tipo **ICollection < TypeArgument\>**. Para especificar a coleção, digite uma expressão do Visual Basic na grade de propriedade.|
|*TypeArgument*|verdadeiro|O tipo T de itens contidos em <xref:System.Collections.Generic.ICollection%601>. Por padrão, isso *TypeArgument* tipo é definido como **Int32**. Para alterar o tipo, altere o valor de *TypeArgument* na caixa de combinação na grade de propriedades.|

## <a name="see-also"></a>Consulte também

- [Coleção](../workflow-designer/collection-activity-designers.md)
- [AddToCollection\<T > Designer de atividade](../workflow-designer/addtocollection-t-activity-designer.md)
- [ClearCollection\<T >](../workflow-designer/clearcollection-t-activity-designer.md)
- [ExistsInCollection\<T >](../workflow-designer/existsincollection-t-activity-designer.md)
- [RemoveFromCollection\<T >](../workflow-designer/removefromcollection-t-activity-designer.md)