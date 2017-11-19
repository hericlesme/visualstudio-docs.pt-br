---
title: "Opção&lt;T&gt; Designer de atividade | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- System.Activities.Presentation.ModelItemKeyValuePair.UI
- System.Activities.Statements.Switch`1.UI
ms.assetid: 18a6c96e-49a9-4356-ab61-fbd7e3ab44bb
caps.latest.revision: "3"
author: ErikRe
ms.author: erikre
manager: erikre
ms.openlocfilehash: 73d9838b5908b059aa229b5e979d635088d31de0
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="switchlttgt-activity-designer"></a>Opção&lt;T&gt; Designer de atividade
A atividade de <xref:System.Activities.Statements.Switch%601> avalia uma expressão especificada e executa a atividade de uma coleção de atividades cuja chave associado corresponde ao valor obtido de avaliação.  
  
 O **Switch < T\>**  designer de atividade é usado para criar e configurar um <xref:System.Activities.Statements.Switch%601> atividade no [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)].  
  
## <a name="the-switchtactivity"></a>A opção\<T > atividade  
 Uma atividade de <xref:System.Activities.Statements.Switch%601> contém <xref:System.Activities.Statements.Switch%601.Expression%2A> e um dicionário de <xref:System.Activities.Statements.Switch%601.Cases%2A>. Cada caso no dicionário consiste em um par que contém um *chave* e uma atividade que serve como correspondente *valor*. A atividade de <xref:System.Activities.Statements.Switch%601> avalia <xref:System.Activities.Statements.Switch%601.Expression%2A> e o compara com cada uma das chaves. Se uma correspondência for encontrada, a atividade correspondente é executada. Somente uma correspondência é possível porque as chaves de dicionário devem ser exclusivos de acordo com o tipo de igualdade definido pelo comparer de igualdade de dicionário. Se nenhuma correspondência for encontrada, a atividade de <xref:System.Activities.Statements.Switch%601.Default%2A> é executada.  
  
## <a name="how-to-use-the-switcht-activity-designer"></a>Como usar a opção\<T > Designer de atividade  
 O **Switch\<T >** designer de atividade pode ser encontrado no **fluxo de controle** categoria do **caixa de ferramentas**, que é acessado clicando-se a **Ferramentas** guia o [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] (como alternativa, selecione **barra de ferramentas** do **exibição** menu ou CTRL + ALT + X.) Após removê-la para o [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)], exibe o **selecionar tipos de** caixa de diálogo para permitir que o usuário especifique o tipo genérico *T* usados em <xref:System.Activities.Statements.Switch%601> atividade. O valor padrão é **Int32**. Uma vez para o tipo genérico *T* tiver sido selecionado, uma **Switch < T\>**  designer é adicionado para o designer de fluxo de trabalho.  
  
 Estas são as propriedades de **Switch < T\>**  designer. Todas essas propriedades podem ser editadas na grade de propriedade. Alguns deless também podem ser editados na superfície de designer.  
  
 A tabela a seguir mostra as propriedades mais úteis de <xref:System.Activities.Statements.Switch%601> e descreve como elas são usadas no designer.  
  
|Nome da Propriedade|Necessária|Uso|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Especifica o nome amigável do designer de atividade de <xref:System.Activities.Statements.Switch%601> . O valor padrão é a opção < Int32\>. O valor pode ser editado no **propriedades** janela ou diretamente no cabeçalho do designer.<br /><br /> Embora não seja necessário <xref:System.Activities.Activity.DisplayName%2A> restrita, é uma prática recomendada usar um.|  
|<xref:System.Activities.Statements.Switch%601.Expression%2A>|verdadeiro|Especifica a expressão usada para comparar as chaves na coleção dos casos para determinar que casos a executar.|  
|<xref:System.Activities.Statements.Switch%601.Default%2A>||Especifica a atividade executada se nenhuma correspondência for encontrada. Clique o **adicionar uma atividade** botão no designer para abrir o **padrão** caixa em que a atividade pode ser descartada.|  
|<xref:System.Activities.Statements.Switch%601.Cases%2A>||Especifica os casos a ser avaliado. Para adicionar um caso, clique o **adicionar novo caso** botão na parte inferior da **Switch\<T >** designer. O botão muda para uma caixa de texto (caixa de combinação, se o tipo genérico selecionado ao adicionar o comutador\<T > é a cadeia de caracteres ou Enum). Depois de adicionar uma chave no **caso o valor** , expande a área de casos e uma atividade pode ser descartada em que o texto da dica "Descartar atividade aqui" para definir a lógica de execução para o caso.|  
  
 Vários casos podem ser adicionados como as chaves dos casos não são duplicadas. Se não, uma caixa de diálogo de erro exibe relatar a chave especificada dos casos já existe e que você deve escolher uma chave diferente. No **Switch\<T >** designer, apenas uma área de casos pode ser no modo de exibição expandido por vez. Se uma área dos casos está na visualização recolhida, clique na área dos casos para expandi-la. Observe que para casos, recolhidos de designer mostra o nome para exibição de atividade dentro dos casos no lado direito se houver. Caso contrário, ele mostra o **adicionar uma atividade** botão que expande o caso se você clicar nele e permite que você adicione uma atividade.  
  
 Clique na chave de casos existentes altera a chave de um rótulo em uma caixa de texto para que você possa editar a chave dos casos.  
  
 Existem 2 maneiras de excluir casos:  
  
1.  Selecione os casos e excluir-los.  
  
2.  Selecione o caso, com o botão direito para exibir o menu de contexto e selecione **excluir**.  
  
 Observe que você deve selecionar os casos os próprios para excluir. Selecionando e excluindo a atividade dentro de um caso exclui somente a atividade não os casos.  
  
## <a name="see-also"></a>Consulte também  
 [Fluxo de Controle](../workflow-designer/control-flow-activity-designers.md)