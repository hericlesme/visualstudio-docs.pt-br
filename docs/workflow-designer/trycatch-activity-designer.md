---
title: Designer de atividade de TryCatch | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- System.Activities.Statements.TryCatch.UI
- System.Activities.Statements.Catch`1.UI
ms.assetid: 02a326c2-4009-442f-b7cb-e42121fd2992
caps.latest.revision: "8"
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload: multiple
ms.openlocfilehash: 9fe179a0e1aee4ff929974899d26df48f669ccd0
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="trycatch-activity-designer"></a>Designer de atividade de TryCatch
O **TryCatch** designer de atividade é usado para criar e configurar um <xref:System.Activities.Statements.TryCatch> atividade.  
  
## <a name="the-trycatch-activity"></a>A atividade de TryCatch  
 O <xref:System.Activities.Statements.TryCatch> atividade contém uma <xref:System.Activities.Statements.TryCatch.Try%2A> atividade, uma coleção de **Catch\<TException >** e um <xref:System.Activities.Statements.TryCatch.Finally%2A> atividade. Um <xref:System.Activities.Statements.Catch%601> do tipo **TException** contém um <xref:System.Activities.Statements.Catch%601.ExceptionType%2A> e um <xref:System.Activities.Statements.Catch%601.Action%2A>. São usados juntos para implementar um mecanismo exceção baseado típico de manipulação de erro. Uma atividade de <xref:System.Activities.Statements.TryCatch> tentar executar a atividade de <xref:System.Activities.Statements.TryCatch.Try%2A> . Se o <xref:System.Activities.Statements.TryCatch.Try%2A> atividade gera qualquer exceção, o <xref:System.Activities.Statements.TryCatch> atividade usa seu **Catch < TException\>**  coleção para coincidir com a exceção. Se houver uma correspondência, o <xref:System.Activities.Statements.Catch%601.Action%2A> do **Catch\<TException >** é executado, que serve como o lógica para a exceção de tratamento de erros. Se as atividades na seção de <xref:System.Activities.Statements.TryCatch.Try%2A> completa com êxito ou as atividades em <xref:System.Activities.Statements.TryCatch.Catches%2A> completa com êxito, a atividade de <xref:System.Activities.Statements.TryCatch> executa sua atividade de <xref:System.Activities.Statements.TryCatch.Finally%2A> . [! INCLUIR[crdefault](/dotnet/framework/windows-workflow-foundation/exceptions).  
  
### <a name="using-the-trycatch-activity-designer"></a>Usando o designer de atividade de TryCatch  
 O **TryCatch** designer de atividade pode ser encontrado no **tratamento de erros** categoria do **caixa de ferramentas**, que é acessado clicando o **dacaixadeferramentas** guia no lado esquerdo do [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] (como alternativa, selecione **barra de ferramentas** do **exibição** menu ou CTLR + ALT + X.)  
  
 O **TryCatch** designer de atividades pode ser arrastado o **caixa de ferramentas** e removidos no [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] superfície onde quer que as atividades geralmente são colocados, tais como dentro um <xref:System.Activities.Statements.Sequence>. Isso cria uma atividade de <xref:System.Activities.Statements.TryCatch> com <xref:System.Activities.Activity.DisplayName%2A> padrão de TryCatch. O <xref:System.Activities.Activity.DisplayName%2A> valor pode ser editado no cabeçalho do **TryCatch** designer de atividade ou o **DisplayName** caixa da grade de propriedade. As outras propriedades devem ser editadas na superfície do **TryCatch** designer de atividade.  
  
 Clique no botão de expansão no canto superior direito da **TryCatch** designer para ver o **tente**, **captura**, e **finalmente** nas caixas de modo de exibição expandido. Para adicionar uma variável, clique o **adicionar novo catch** botão **TryCatch** designer. O botão muda para uma caixa de combinação de tipo. Selecione um tipo de exceção e pressione ENTER para adicionar a captura. Depois de adicionar um **Catch**, expande a área de catch e uma atividade pode ser solto catch para definir a lógica de execução para o problema. Observe que há uma caixa de texto no lado direito da área expandida catch. Você pode nomear a variável de exceções usando esta caixa de texto. A variável de exceção só pode ser usada para atividades dentro do mesmo **Catch**.  
  
 O **TryCatch** designer não oferece suporte à edição **Catch**. Se você quiser alterar o tipo de exceção, você precisa excluir o **Catch** e adicione um novo. Um **Catch** pode ser excluído, selecionando-o e excluí-lo ou usando o **excluir** no menu de contexto acessado com um clique direito.  
  
### <a name="the-trycatch-properties"></a>As propriedades de TryCatch  
 A tabela a seguir mostra o <xref:System.Activities.Statements.TryCatch>propriedades e descreve como eles são usados no designer.  
  
|Nome da Propriedade|Necessária|Uso|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Especifica o nome amigável opcional de atividade de <xref:System.Activities.Statements.TryCatch> . O padrão é TryCatch.|  
|<xref:System.Activities.Statements.TryCatch.Try%2A>|False|A atividade executada primeiro quando <xref:System.Activities.Statements.TryCatch> executar.|  
|<xref:System.Activities.Statements.TryCatch.Catches%2A>|False|A coleção de **Catch** elementos a serem verificados quando o <xref:System.Activities.Statements.TryCatch.Try%2A> atividade gera uma exceção.<br /><br /> Você precisa pelo menos de adicionar uma atividade em <xref:System.Activities.Statements.TryCatch.Catches%2A> ou uma atividade no bloco de <xref:System.Activities.Statements.TryCatch.Finally%2A> .|  
|<xref:System.Activities.Statements.TryCatch.Finally%2A>|False|A atividade a ser executada quando <xref:System.Activities.Statements.TryCatch.Try%2A> e todas as atividades necessárias na coleção de <xref:System.Activities.Statements.TryCatch.Catches%2A> tiver terminado a execução.<br /><br /> Você precisa pelo menos de adicionar uma atividade em <xref:System.Activities.Statements.TryCatch.Catches%2A> ou uma atividade no bloco de <xref:System.Activities.Statements.TryCatch.Finally%2A> .|  
  
## <a name="see-also"></a>Consulte também  
 [Coleção](../workflow-designer/collection-activity-designers.md)   
 [Relançar](../workflow-designer/rethrow-activity-designer.md)   
 [Throw](../workflow-designer/throw-activity-designer.md)