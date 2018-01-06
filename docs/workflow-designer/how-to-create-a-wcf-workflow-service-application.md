---
title: "Como: criar um aplicativo de serviço de fluxo de trabalho WCF | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 12d675ac-27d8-4d86-ba16-6f7688f8c841
caps.latest.revision: "14"
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload: multiple
ms.openlocfilehash: 8730b8f1611694ec7927b52fa4118cf3ca3801b7
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-wcf-workflow-service-application"></a>Como: Crie um aplicativo de Serviço WCF de Fluxo de Trabalho
aplicativos de serviço do fluxo de trabalho[!INCLUDE[indigo1](../workflow-designer/includes/indigo1_md.md)] são serviços de comunicação distribuídos que transmitem as mensagens entre clientes e eles próprios através dos limites de processo. A implementação do contrato de serviço no lado de serviço é feita declarativamente com as atividades de fluxo de trabalho em [!INCLUDE[netfx40_short](../workflow-designer/includes/netfx40_short_md.md)] de um modo semelhante aos serviços herdados de fluxo de trabalho no .NET Framework 3.5.  
  
### <a name="to-create-a-wcf-workflow-service-application"></a>Para criar um aplicativo de serviço do fluxo de trabalho WCF  
  
1.  Inicie o [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)].  
  
2.  Sobre o **arquivo** , aponte para **novo**e, em seguida, selecione **projeto...** .  
  
     A caixa de diálogo **Novo Projeto** é aberta.  
  
3.  No **modelos instalados** painel, selecione **WCF** ou **fluxo de trabalho** do **Visual C#** ou **doVisualBasic** agrupamentos dependendo de você idioma de preferência.  
  
4.  No painel central, selecione **aplicativo de serviço de fluxo de trabalho WCF**.  
  
5.  No **nome** , digite um nome descritivo para o seu projeto tornar mais fácil de identificar.  
  
6.  No **local** , digite o diretório no qual você deseja salvar o projeto ou clique em **procurar** para navegar até ele.  
  
7.  No **solução** , selecione para criar uma nova solução e, em seguida, clique em **Okey**.  
  
    > [!NOTE]
    >  Se você quiser adicionar um aplicativo de console do fluxo de trabalho a uma solução existente, abra essa solução no [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)], clique com botão direito da solução de **Solution Explorer**e selecione **adicionar**, em seguida,  **Novo projeto...**  para abrir o **novo projeto** caixa de diálogo. Continuar conforme descrito acima neste procedimento.  
  
8.  O modelo de projeto cria uma definição de serviço como XAML. [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] abre para o modo design com uma atividade de <xref:System.Activities.Statements.Sequence> que contém um conjunto de <xref:System.ServiceModel.Activities.Receive> e de atividades de <xref:System.ServiceModel.Activities.SendReply> .  
  
## <a name="see-also"></a>Consulte também  
 [Como: criar uma atividade](/dotnet/framework/windows-workflow-foundation/how-to-create-an-activity)   
 [Criando um projeto de fluxo de trabalho](../workflow-designer/creating-a-workflow-project.md)