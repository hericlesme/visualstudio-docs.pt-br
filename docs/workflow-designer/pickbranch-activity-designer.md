---
title: Designer de atividade de PickBranch | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- System.Activities.Statements.PickBranch.UI
ms.assetid: f523ad47-bbc0-4cda-a35c-41e67c4ba081
caps.latest.revision: 
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload:
- multiple
ms.openlocfilehash: d583c662de31b990982b78d876bc0046e89089d7
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="pickbranch-activity-designer"></a>Designer de atividade de PickBranch
<xref:System.Activities.Statements.PickBranch> fornece um caminho de execução baseado em uma atividade de <xref:System.Activities.Statements.Pick> que pode ser acionada por um evento de entrada.  
  
## <a name="pickbranch"></a>PickBranch  
 os objetos de<xref:System.Activities.Statements.PickBranch> estão contidos na coleção de <xref:System.Activities.Statements.Pick.Branches%2A> de uma atividade de <xref:System.Activities.Statements.Pick> . Cada <xref:System.Activities.Statements.PickBranch> está contido em uma ramificação de atividade de <xref:System.Activities.Statements.Pick> e pode ser executado devido a qualquer evento de entrada que serve como um disparador. Dessa forma [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] fornece a modelagem com base em eventos de fluxo de controle. Cada <xref:System.Activities.Statements.PickBranch> contém <xref:System.Activities.Statements.PickBranch.Trigger%2A> e <xref:System.Activities.Statements.PickBranch.Action%2A>.  
  
### <a name="how-to-use-the-pick-activity-designer"></a>Como usar o designer de atividade de picareta  
 O **PickBranch** designer pode ser encontrado no **fluxo de controle** categoria do **caixa de ferramentas**, que é acessado clicando o **caixa de ferramentas** guia [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] (como alternativa, selecione **barra de ferramentas** do **exibição** menu ou CTRL + ALT + X).  
  
 Dois vazio <xref:System.Activities.Statements.PickBranch> objetos com exibem nomes de **Branch1** e **Branch2** são criados por padrão como elementos de um <xref:System.Activities.Statements.Pick> atividade quando o **escolher** designer de atividade inicialmente é descartado para a [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]. Esses respectivos <xref:System.Activities.Statements.PickBranch.DisplayName%2A> valores de propriedade podem ser editados no **PickBranch** cabeçalho designer ou dentro de **propriedades** janela para cada ramificação.  
  
 Há duas maneiras de adicionar <xref:System.Activities.Statements.PickBranch> objetos para a coleção de um <xref:System.Activities.Statements.Pick> objeto: arrastando e soltando o **PickBranch** designer do **caixa de ferramentas** ou usando o menu de contexto dentro de **escolher** superfície de design:  
  
1.  O **PickBranch** designer cria um <xref:System.Activities.Statements.PickBranch> quando ele é arrastado do **caixa de ferramentas** e descartado em uma das ramificações de um **escolher** designer de atividade sobre o [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] superfície. Novos objetos de <xref:System.Activities.Statements.PickBranch> podem ser colocados dentro do designer de <xref:System.Activities.Statements.Pick> para a esquerda ou direita de todos os elementos existentes de <xref:System.Activities.Statements.PickBranch> já contidos na coleção. Ao arrastar um **PickBranch** designer para o **escolher** designer com o mouse, o **escolher** designer usa uma faixa cinza azul vertical para indicar onde o <xref:System.Activities.Statements.PickBranch> é adicionado para o posicionamento de um determinado mouse.  
  
2.  Clique com botão direito **escolher** designer de atividade (mas não dentro **PickBranch** designer) para obter um menu de contexto e selecione **criar ramificação** para adicionar um novo <xref:System.Activities.Statements.PickBranch>. Observe que o novo <xref:System.Activities.Statements.PickBranch> é adicionada à direita do existente <xref:System.Activities.Statements.PickBranch> objetos no **escolher** designer.  
  
 O **PickBranch** designer pode ser expandido para revelar o **gatilho** e **ação** caixas ou recolhido clicando os sinais de interpolação duplas à direita dos cabeçalhos. Editar o <xref:System.Activities.Statements.PickBranch.Trigger%2A> e <xref:System.Activities.Statements.PickBranch.Action%2A> de cada <xref:System.Activities.Statements.PickBranch> soltando atividades no **gatilho** e **ação** caixas de seus designers.  
  
 O <xref:System.Activities.Statements.PickBranch> objetos no <xref:System.Activities.Statements.Pick.Branches%2A> coleção de um <xref:System.Activities.Statements.Pick> de objeto, podem ser reordenadas arrastando e soltando-los para um novo local dentro de **escolher** designer. O **escolher** designer usa uma faixa cinza azul vertical para indicar onde o <xref:System.Activities.Statements.PickBranch> é adicionada para o posicionamento de um determinado mouse.  
  
 Há duas maneiras para excluir <xref:System.Activities.Statements.PickBranch>:  
  
1.  Selecione o **PickBranch** designer e excluí-lo.  
  
2.  Selecione o **PickBranch** designer, clique com botão direito para obter o menu de contexto e selecione **excluir**.  
  
 Certifique-se de selecionar o **PickBranch** designer, como selecionar uma das atividades dentro de seu **gatilho** ou **ação** caixas exclui uma dessas atividades por engano e não o <xref:System.Activities.Statements.PickBranch> objeto.  
  
### <a name="pickbranch-properties-in-the-workflow-designer"></a>Propriedades de PickBranch em Designer de Fluxo de Trabalho  
 A tabela a seguir mostra as propriedades mais úteis de <xref:System.Activities.Statements.PickBranch> e descreve como usá-los em [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)].  
  
|Nome da Propriedade|Necessária|Uso|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Statements.PickBranch.DisplayName%2A>|False|O nome amigável exibido no cabeçalho do **PickBranch** designer. O valor padrão é ramificação.<br /><br /> Embora não seja necessário <xref:System.Activities.Activity.DisplayName%2A> restrita, é uma prática recomendada usar um.|  
|<xref:System.Activities.Statements.PickBranch.Trigger%2A>|verdadeiro|Cada <xref:System.Activities.Statements.PickBranch> contém uma ação de <xref:System.Activities.Statements.PickBranch.Trigger%2A> que pode chamar <xref:System.Activities.Statements.PickBranch.Action%2A>.|  
|<xref:System.Activities.Statements.PickBranch.Action%2A>|False|Cada <xref:System.Activities.Statements.PickBranch> contém <xref:System.Activities.Statements.PickBranch.Action%2A> que é executado se disparado.|  
  
## <a name="see-also"></a>Consulte também  
 [Fluxo de controle](../workflow-designer/control-flow-activity-designers.md)   
 [Escolher atividade](/dotnet/framework/windows-workflow-foundation/pick-activity)   
 [Usando a atividade de Pick](/dotnet/framework/windows-workflow-foundation/samples/using-the-pick-activity)