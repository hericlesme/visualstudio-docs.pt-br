---
title: Designer de fluxo de trabalho - ClearCollection<T> Designer de atividade
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Statements.ClearCollection`1.UI
ms.assetid: db0e5da2-7b5a-4f1a-864c-f3aeeeeb51a7
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b3d9d246fa6bad55e47ddff73c888906f2979695
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31974506"
---
# <a name="clearcollectiont-activity-designer"></a>ClearCollection\<T > Designer de atividade

O **ClearCollection\<T >** designer de atividade é usado para criar e configurar um <xref:System.Activities.Statements.ClearCollection%601> atividade.

## <a name="the-clearcollectiont-activity"></a>O ClearCollection\<T > atividade
 A atividade de <xref:System.Activities.Statements.ClearCollection%601> limpa especificada uma coleção de todos os itens.

### <a name="using-the-clearcollectiont-activity-designer"></a>Usando o ClearCollection\<T > Designer de atividade
 O **ClearCollection\<T >** designer de atividade pode ser encontrado no **coleção** categoria do **caixa de ferramentas**, que é acessado clicando o  **Caixa de ferramentas** guia do Designer de fluxo de trabalho (como alternativa, selecione **barra de ferramentas** do **exibição** menu ou CTRL + ALT + X.)

 O **ClearCollection\<T >** designer de atividades pode ser arrastado do **caixa de ferramentas** e descartado para a superfície do Designer de fluxo de trabalho onde quer que as atividades são colocados, tais como dentro de um <xref:System.Activities.Statements.Sequence>. Descartar o designer de atividade cria um <xref:System.Activities.Statements.ClearCollection%601> atividade com um padrão <xref:System.Activities.Activity.DisplayName%2A> de ClearCollection < Int32\>. (Por padrão, o *TypeArgument* é **Int32**. TypeArgument pode ser alterada na grade de propriedades.) O <xref:System.Activities.Activity.DisplayName%2A> valor pode ser editado no cabeçalho do **ClearCollection < T\>**  designer de atividade ou o **DisplayName** caixa da grade de propriedade. Outras propriedades devem ser editadas na grade de propriedade.

### <a name="the-clearcollectiont-properties"></a>O ClearCollection\<T > Propriedades
 A tabela a seguir mostra as propriedades de <xref:System.Activities.Statements.ClearCollection%601> e descreve como elas são usadas no designer.

|Nome da Propriedade|Necessária|Uso|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Especifica o nome amigável opcional de atividade de <xref:System.Activities.Statements.ClearCollection%601> . O padrão é ClearCollection < Int32\>. Embora o valor de <xref:System.Activities.Activity.DisplayName%2A> não é necessário restrita, é uma prática recomendada usar um.|
|<xref:System.Activities.Statements.ClearCollection%601.Collection%2A>|verdadeiro|Especifica a coleção a ser limpa os itens. Essa coleção é do tipo **ICollection\<TypeArgument >.** Para especificar a coleção, digite uma expressão do Visual Basic na grade de propriedade.|
|*TypeArgument*|verdadeiro|Especifica o tipo T de itens contidos em <xref:System.Collections.Generic.ICollection%601>. Por padrão, isso *TypeArgument* tipo é definido como **Int32**. Para alterar o tipo, altere o valor de *TypeArgument* na caixa de combinação na grade de propriedades.|

## <a name="see-also"></a>Consulte também

- [Coleção](../workflow-designer/collection-activity-designers.md)
- [AddToCollection\<T >](../workflow-designer/addtocollection-t-activity-designer.md)
- [ExistsInCollection\<T >](../workflow-designer/existsincollection-t-activity-designer.md)
- [RemoveFromCollection\<T >](../workflow-designer/removefromcollection-t-activity-designer.md)