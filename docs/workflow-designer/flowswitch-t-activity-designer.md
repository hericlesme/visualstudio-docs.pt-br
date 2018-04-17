---
title: /Flowswitch&lt;T&gt; Designer de atividade | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Core.Presentation.FlowSwitchLink.UI
- System.Activities.Statements.FlowSwitch`1.UI
- System.Activities.Core.Presentation.FlowSwitchLink`1.UI
- System.Activities.Core.Presentation.FlowSwitchLinkIdentifier.UI
ms.assetid: 5b9c5afe-7499-4ee8-8c33-28aff14bde07
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: fb8c28f835fad4e70b213d13aaeb654780b72297
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="flowswitchlttgt-activity-designer"></a>/Flowswitch&lt;T&gt; Designer de atividade
A atividade de <xref:System.Activities.Statements.FlowSwitch%601> é um nó condicional que fornece a ramificação para o fluxo de controle baseado no critério de correspondência quando mais de duas ramificações alternativas são necessários. Se a ramificação de fluxo requer apenas dois caminhos, use a atividade de <xref:System.Activities.Statements.FlowDecision> em vez disso.

## <a name="the-flowswitcht-activity"></a>FlowSwitch < T\> atividade
 O <xref:System.Activities.Statements.FlowSwitch%601> atividade contém uma <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> que retorna um valor do tipo *T* (especificado pelo parâmetro genérico) quando avaliada. A atividade também contém um conjunto de <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A>, que especifica um mapeamento exclusivo de resultados possíveis da avaliação a um conjunto de objetos de <xref:System.Activities.Statements.FlowNode> . O <xref:System.Activities.Statements.FlowNode> executado é aquele cujo objeto do tipo *T* corresponde ao valor do avaliado <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A>. Os exemplos de <xref:System.Activities.Statements.FlowSwitch%601.Default%2A> podem opcionalmente () são fornecidos para casos em que nenhuma correspondência for obtida.

### <a name="using-the-flowswitcht-activity-designer"></a>Usando FlowSwitch\<T > Designer de atividade
 O **/flowswitch\<T >** designer de atividade pode ser encontrado no **fluxograma** categoria do **caixa de ferramentas**, que é acessado clicando-se a **Ferramentas** guia no lado esquerdo do [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] (como alternativa, selecione **barra de ferramentas** do **exibição** menu ou CTRL + ALT + X.)

 O **/flowswitch\<T >** designer de atividades pode ser arrastado o **caixa de ferramentas** e removidos no [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] superfície dentro de um **fluxograma** designer de atividade. Use o **selecionar tipos de** janela que exibe para especificar o tipo (associado no código com o <xref:System.Activities.Statements.FlowSwitch%601> pelo seu parâmetro genérico) obtido avaliando a <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A>. Este procedimento cria um <xref:System.Activities.Statements.FlowSwitch%601> atividade rotulada **Switch** dentro de <xref:System.Activities.Statements.Flowchart> atividade. O <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> podem ser digitados no **expressão** caixa do **propriedades** janela clicando em que o texto de dica dizendo "Insira uma expressão VB".

 Passe o mouse sobre o **/flowswitch\<T >** designer de atividade para fazer com que os identificadores de quadrados que são usados para o link <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> apareça em torno de suas extremidades. Depois de arrastar o **/flowswitch < T\>**  designer de atividade e outros designers de atividade para o **fluxograma**, o <xref:System.Activities.Activity> objetos que representam estão prontos para ser vinculados para especificar a ordem de execução. Para criar um do <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> associado a <xref:System.Activities.Statements.FlowSwitch%601>, clique em uma das alças quadradas casos no perímetro da **/flowswitch < T\>**  e arraste-o (segurando o botão do mouse) para uma das alças que é exibida de maneira semelhante ao redor da atividade de destino quando o mouse passa sobre o designer. Solte o botão do mouse e uma seta do **/flowswitch < T\>**  aparece para o designer de destino que representa este caso. O valor padrão para esse caso exibe na seta e ele pode ser editado no **caso** caixa do **propriedades** janela.

### <a name="the-flowswitcht-properties"></a>FlowSwitch < T\> propriedades
 A tabela a seguir mostra as propriedades de <xref:System.Activities.Statements.FlowSwitch%601> e descreve como elas são usadas no designer. Essas propriedades podem ser editadas na grade de propriedade ou na superfície de designer.

|Nome da Propriedade|Necessária|Uso|
|-------------------|--------------|-----------|
|<xref:System.Activities.Statements.FlowSwitch%601.Expression%2A>|verdadeiro|Especifica a expressão que é avaliada para determinar qual de <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> para alternar o caminho execução.|
|<xref:System.Activities.Statements.FlowSwitch%601.Cases%2A>|False|Especifica um mapeamento exclusivo de resultados possíveis obtidos de avaliar <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> a um conjunto de objetos de <xref:System.Activities.Statements.FlowNode> .|
|<xref:System.Activities.Statements.FlowSwitch%601.Default%2A>|verdadeiro|Especificar o mapeamento quando a avaliação de <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> não coincide com um dos valores contidos no objeto de <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> .|

## <a name="see-also"></a>Consulte também

- [Fluxograma](../workflow-designer/flowchart-activity-designers.md)
- [Fluxograma](../workflow-designer/flowchart-activity-designer.md)
- [FlowDecision](../workflow-designer/flowdecision-activity-designer.md)