---
title: 'Passo a passo: Adicionar receptores de evento do recurso | Microsoft Docs'
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, advanced packaging tools
- SharePoint development in Visual Studio, event receivers
- SharePoint development in Visual Studio, feature event receivers
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: e028eb4d95495e92718769979f43012319596960
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/10/2018
---
# <a name="walkthrough-add-feature-event-receivers"></a>Instruções passo a passo: adicionar receptores de evento de funcionalidade
  Receptores de evento de recurso são métodos que executar quando ocorrer por um dos seguintes eventos relacionados a recursos no SharePoint:  
  
-   Um recurso é instalado.  
  
-   Um recurso está ativado.  
  
-   Um recurso está desativado.  
  
-   Um recurso será removido.  
  
 Este passo a passo demonstra como adicionar um receptor de eventos a um recurso em um projeto do SharePoint. Ele demonstra as seguintes tarefas:  
  
-   Criando um projeto vazio com um receptor de evento de recurso.  
  
-   Tratamento de **FeatureDeactivating** método.  
  
-   Usando o modelo de objeto do projeto do SharePoint para adicionar um anúncio para a lista de avisos.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Pré-requisitos  
 Você precisa dos seguintes componentes para concluir esta instrução passo a passo:  
  
-   Edições com suporte do Microsoft Windows e do SharePoint. Para obter mais informações, consulte [requisitos para desenvolver soluções do SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   Visual Studio.  
  
## <a name="creating-a-feature-event-receiver-project"></a>Criando um projeto de receptor de evento de recurso  
 Primeiro, crie um projeto para conter o receptor de evento de recurso.  
  
#### <a name="to-create-a-project-with-a-feature-event-receiver"></a>Para criar um projeto com um receptor de evento de recurso  
  
1.  Na barra de menus, escolha **arquivo**, **novo**, **projeto** para exibir o **novo projeto** caixa de diálogo.  
  
2.  Expanda o **SharePoint** nó sob o **Visual C#** ou **Visual Basic**e, em seguida, escolha o **2010** nó.  
  
3.  No **modelos** painel, escolha o **projeto do SharePoint 2010** modelo.  
  
     Você pode usar esse tipo de projeto para receptores de evento de recurso porque eles têm nenhum modelo de projeto.  
  
4.  No **nome** , digite **FeatureEvtTest**e, em seguida, escolha o **Okey** botão para exibir o **Assistente de personalização do SharePoint**.  
  
5.  Sobre o **especificar o nível de site e segurança de depuração** página, insira a URL do servidor do site do SharePoint ao qual você deseja adicionar o novo item de campo personalizado ou usar o local padrão (http://\<*sistema nome*> /).  
  
6.  No **o que é o nível de confiança para essa solução do SharePoint?** , escolha o **implantar como uma solução de farm** botão de opção.  
  
     Para obter mais informações sobre soluções de área restrita em comparação com soluções de farm, consulte [considerações sobre a solução em área restrita](../sharepoint/sandboxed-solution-considerations.md).  
  
7.  Escolha o **concluir** botão e, em seguida, observe que um recurso chamado Feature1 aparece sob o **recursos** nó.  
  
## <a name="adding-an-event-receiver-to-the-feature"></a>Adicionando um receptor de eventos para o recurso  
 Em seguida, adicionar um receptor de eventos para o recurso e adicione o código que é executado quando o recurso está desativado.  
  
#### <a name="to-add-an-event-receiver-to-the-feature"></a>Para adicionar um receptor de eventos para o recurso  
  
1.  Abra o menu de atalho para o nó de recursos e, em seguida, escolha **adicionar recurso** para criar um recurso.  
  
2.  Sob o **recursos** nó, abra o menu de atalho para **Feature1**e, em seguida, escolha **adicionar receptor de evento** para adicionar um receptor de eventos para o recurso.  
  
     Isso adiciona um arquivo de código em Feature1. Nesse caso, ele é chamado Feature1.EventReceiver.cs ou Feature1.EventReceiver.vb, dependendo da linguagem de desenvolvimento do seu projeto.  
  
3.  Se seu projeto é escrito em [!INCLUDE[csprcs](../sharepoint/includes/csprcs-md.md)], adicione o seguinte código na parte superior do receptor do evento, se ainda não estiver lá:  
  
     [!code-csharp[SP_FeatureEvt#1](../sharepoint/codesnippet/CSharp/featureevttest2/features/feature1/feature1.eventreceiver.cs#1)]  
  
4.  Classe receptora do evento contém vários métodos comentada que agem como eventos. Substitua o **FeatureDeactivating** método com o seguinte:  
  
     [!code-vb[SP_FeatureEvt#2](../sharepoint/codesnippet/VisualBasic/featureevt2vb/features/feature1/feature1.eventreceiver.vb#2)]
     [!code-csharp[SP_FeatureEvt#2](../sharepoint/codesnippet/CSharp/featureevttest2/features/feature1/feature1.eventreceiver.cs#2)]  
  
## <a name="testing-the-feature-event-receiver"></a>Teste o receptor de evento de recurso  
 Em seguida, desativar o recurso para testar se o **FeatureDeactivating** método gera um anúncio para a lista de anúncios do SharePoint.  
  
#### <a name="to-test-the-feature-event-receiver"></a>Para testar o receptor de evento de recurso  
  
1.  Defina o valor do projeto do **configuração de implantação ativa** propriedade **ativação não**.  
  
     Definir essa propriedade impede que o recurso de ativação no SharePoint e permite que você depure receptores de evento de recurso. Para obter mais informações, consulte [soluções do SharePoint de depuração](../sharepoint/debugging-sharepoint-solutions.md).  
  
2.  Escolha o **F5** para executar o projeto e implantá-lo no SharePoint.  
  
3.  Na parte superior da página da Web do SharePoint, abra o **ações do Site** menu e, em seguida, escolha **configurações do Site**.  
  
4.  Sob o **ações do Site** seção o **configurações de Site** página, escolha o **gerenciar recursos do site** link.  
  
5.  No **recursos** página, escolha o **ativar** lado a **FeatureEvtTest Feature1** recurso.  
  
6.  No **recursos** página, escolha o **desativar** próximo ao **FeatureEvtTest Feature1** recurso e, em seguida, escolha o **desativar esse recurso**  link de confirmação para desativar o recurso.  
  
7.  Escolha o **início** botão.  
  
     Observe que um anúncio aparece no **anúncios** lista depois que o recurso está desativado.  
  
## <a name="see-also"></a>Consulte também  
 [Como: criar um receptor de evento](../sharepoint/how-to-create-an-event-receiver.md)   
 [Desenvolvendo soluções do SharePoint](../sharepoint/developing-sharepoint-solutions.md)  
  
  