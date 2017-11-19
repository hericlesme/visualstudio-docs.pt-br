---
title: 'Como: fornecer contexto para editores | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], legacy - provide context
ms.assetid: 12df4d06-df6b-4eaf-a7bf-c83655a0c683
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6687ce3ed73a96778b84cec6e77d5c0b3145702d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-provide-context-for-editors"></a>Como: fornecer contexto para editores
Para um editor, o contexto está ativo somente quando o editor tem foco ou tinha o foco imediatamente antes do foco foi movido para uma janela de ferramenta. Você pode fornecer o contexto para um editor, fazendo o seguinte:  
  
1.  Crie um recipiente de contexto.  
  
2.  Publica o recipiente de contexto para o identificador de elemento de seleção (SEID).  
  
3.  Manter o contexto no recipiente.  
  
 Essas tarefas são cobertas pelos procedimentos a seguir. Para obter mais informações sobre como fornecer contexto, consulte **programação robusta** mais adiante neste tópico.  
  
### <a name="to-create-a-context-bag-for-an-editor-or-a-designer"></a>Para criar um recipiente de contexto para um editor ou designer  
  
1.  Chamar `QueryService` em seu <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> a interface para o <xref:Microsoft.VisualStudio.Shell.Interop.SVsMonitorUserContext> service.  
  
     Um ponteiro para o <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorUserContext> interface é retornada.  
  
2.  Chamar o <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorUserContext.CreateEmptyContext%2A> método para criar um novo conjunto de contexto ou subcontexto.  
  
     Um ponteiro para o <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext> interface é retornada.  
  
3.  Chamar o <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AddAttribute%2A> método para adicionar atributos, palavras-chave de pesquisa ou palavras-chave de F1 para o recipiente de contexto ou subcontexto.  
  
4.  Se você estiver criando um recipiente subcontexto, chame o <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AddSubcontext%2A> método para vincular o recipiente subcontexto para o recipiente de contexto do pai.  
  
5.  Chamar <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AdviseUpdate%2A> para receber uma notificação quando o **ajuda dinâmica** janela está prestes a atualizar.  
  
     Tendo o **ajuda dinâmica** janela chamar seu editor quando ele estiver pronto para atualizar a oportunidade para atrasar a alterar o contexto até que a atualização ocorra. Isso pode melhorar o desempenho, pois ela permite que você atrasar a execução demorados algoritmos até que o tempo ocioso do sistema está disponível.  
  
### <a name="to-publish-the-context-bag-to-the-seid"></a>Para publicar o recipiente de contexto para o SEID  
  
1.  Chamar `QueryService` no <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackSelectionEx> serviço para retornar um ponteiro para o <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx> interface.  
  
2.  Chamar <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx.OnElementValueChange%2A>, especificando um identificador de elemento (`elementid` parâmetro) valor de SEID_UserContext para indicar que você está passando o contexto no nível global.  
  
3.  Quando o editor ou designer se torna ativo, os valores no seu <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx> objeto são propagadas para a seleção global. Você só precisa concluir esse processo, uma vez por sessão e, em seguida, armazene o ponteiro para o contexto global criado quando você chamou <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx.OnElementValueChange%2A>.  
  
### <a name="to-maintain-the-context-bag"></a>Para manter o recipiente de contexto  
  
1.  Implementar <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext> para garantir que o **ajuda dinâmica** janela chama editor ou designer antes de atualizar.  
  
     Para cada recipiente de contexto que chamou <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AdviseUpdate%2A> depois que o recipiente de contexto é criado e implementou <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate>, as chamadas IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate.UpdateUserContext%2A> para notificar o provedor de contexto que o recipiente de contexto será atualizado. Você pode usar essa chamada para alterar os atributos e as palavras-chave no recipiente de contexto e em quaisquer pacotes subcontexto, antes de **ajuda dinâmica** janela atualização ocorre.  
  
2.  Chamar <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.SetDirty%2A> no conjunto de contexto para indicar que o editor ou designer tem o novo contexto.  
  
     Quando o **ajuda dinâmica** janela chamadas <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate.UpdateUserContext%2A> para indicar que está atualizando, editor ou designer pode atualizar o contexto adequadamente para o recipiente de contexto do pai e de quaisquer pacotes subcontexto nesse momento.  
  
    > [!NOTE]
    >  O `SetDirty` sinalizador é definido automaticamente como `true` sempre que o contexto é adicionado ou removido do conjunto de contexto. O **ajuda dinâmica** janela só chama <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate.UpdateUserContext%2A> no conjunto de contexto se o `SetDirty` sinalizador é definido como `true`. Ele é redefinido para `false` após a atualização.  
  
3.  Chamar <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AddAttribute%2A> para adicionar o contexto para a coleção de contexto ativo ou <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.RemoveAttribute%2A> para remover o contexto.  
  
## <a name="robust-programming"></a>Programação robusta  
 Se você estiver escrevendo seu próprio editor, você deve concluir os procedimentos neste tópico para fornecer contexto para o editor de todos os três.  
  
> [!NOTE]
>  Para ativar corretamente uma janela do editor ou designer e certifique-se de que o roteamento de comando estejam corretamente atualizado, você deve chamar <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> no componente para torná-lo a janela de foco.  
  
 O SEID é uma coleção de propriedades que são alteradas com base na seleção. Informações de SEID estão disponíveis por meio da seleção global. A seleção global está conectada em eventos disparados pelo <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx> interface, e possui uma lista de todos os itens selecionados (editor atual, janela da ferramenta atual, hierarquia atual e assim por diante).  
  
 Para editores e designers, no qual o contexto pode alterar sempre que o cursor se move dentro de uma palavra, é ineficiente para atualizar constantemente o recipiente de contexto. Para facilitar a atualização mais eficiente sempre detectar o cursor movendo dentro do editor ou a janela do designer, você pode chamar <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.SetDirty%2A>. Isso permite que você mantenha suas alterações de contexto até que haja tempo ocioso e o serviço de contexto do IDE envia notificação para o editor ou designer de **ajuda dinâmica** janela está atualizando. Essa abordagem é usada no procedimento "para manter o recipiente de contexto" neste tópico.  
  
 Depois de fornecer contexto para atividades em seu editor ou designer, você deve fornecer uma palavra-chave do F1 específica para permitir que os usuários obter ajuda para o editor ou designer em si.  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx.OnElementValueChange%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AddAttribute%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AdviseUpdate%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.RemoveAttribute%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.SetDirty%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate.UpdateUserContext%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackSelectionEx>