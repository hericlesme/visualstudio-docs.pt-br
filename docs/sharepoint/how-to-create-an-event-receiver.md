---
title: 'Como: criar um receptor de evento | Microsoft Docs'
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VS.SharePointTools.SPE.EventReceiver
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, event receivers
- event receivers [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 1b00d82679388c50d6d111209a9a206bd9587a3a
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-create-an-event-receiver"></a>Como criar um receptor de evento
  Criando *receptores de evento*, você pode responder quando um usuário interage com itens do SharePoint, como listas ou itens de lista. Por exemplo, o código em um receptor de evento pode ser acionado quando um usuário altera o calendário ou exclui um nome de uma lista de contatos. Ao seguir neste tópico, você pode aprender a adicionar um receptor de evento para uma instância de lista.  
  
 Para concluir essas etapas, você deve ter instalado [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] e edições com suporte do Windows e do SharePoint. Para obter mais informações, consulte [requisitos para desenvolver soluções do SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md). Como este exemplo exige um projeto do SharePoint, você também deve ter concluído o procedimento no tópico [passo a passo: criar uma coluna de Site, o tipo de conteúdo e a lista do SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md).  
  
## <a name="adding-an-event-receiver"></a>Adicionando um receptor de evento  
 O projeto que você criou na [passo a passo: criar uma coluna de Site, o tipo de conteúdo e a lista do SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md) inclui colunas de site personalizado, uma lista personalizada e um tipo de conteúdo. No procedimento a seguir, você vai expandir este projeto adicionando um manipulador de eventos simples (um receptor de evento) a uma instância de lista para mostrar como manipular eventos que ocorrem em itens do SharePoint, como listas.  
  
#### <a name="to-add-an-event-receiver-to-the-list-instance"></a>Para adicionar um receptor de evento para a instância de lista  
  
1.  Abra o projeto que você criou na [passo a passo: criar uma coluna de Site, o tipo de conteúdo e a lista do SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md).  
  
2.  Em **Solution Explorer**, escolha o nó do projeto do SharePoint, que é chamado de **clínica**.  
  
3.  Na barra de menus, escolha **projeto**, **Adicionar Novo Item**.  
  
4.  Em um **Visual C#** ou **Visual Basic**, expanda o **SharePoint** nó e, em seguida, escolha o **2010** item.  
  
5.  No **modelos** painel, escolha **receptor de evento**, nomeie-o **TestEventReceiver1**e, em seguida, escolha o **Okey** botão.  
  
     O **Assistente de personalização do SharePoint** é exibida.  
  
6.  No **o tipo de receptor de eventos você deseja fazer?** , escolha **eventos de Item de lista**.  
  
7.  No **o item deve ser a origem do evento?** , escolha **pacientes (Clinic\Patients)**.  
  
8.  No **lidar com os seguintes eventos** , selecione a caixa de seleção ao lado de **um item foi adicionado**e, em seguida, escolha o **concluir** botão.  
  
     O arquivo de código para o novo receptor de evento contém um único método chamado `ItemAdded`. Na próxima etapa, você adicionará código para esse método para que cada contato será nomeado Scott Brown por padrão.  
  
9. Substituir o `ItemAdded` método com o seguinte código e, em seguida, pressione a tecla F5:  
  
     [!code-csharp[SP_EventReceiver#1](../sharepoint/codesnippet/CSharp/CustomField1/TestEventReceiver1/TestEventReceiver1.cs#1)]
     [!code-vb[SP_EventReceiver#1](../sharepoint/codesnippet/VisualBasic/CustomField1_VB/EventReceiver1/EventReceiver1.vb#1)]  
  
     O código é executado e o SharePoint site aparece no navegador da web.  
  
10. Na barra de início rápido, escolha o **pacientes** link e, em seguida, escolha o **Adicionar Novo Item** link.  
  
     Abre o formulário de entrada para novos itens.  
  
11. Inserir dados nos campos e, em seguida, escolha o **salvar** botão.  
  
     Depois que você escolher o **salvar** botão, o **paciente nome** coluna é atualizada automaticamente para o nome de Scott Brown.  
  
## <a name="see-also"></a>Consulte também  
 [Desenvolvendo soluções do SharePoint](../sharepoint/developing-sharepoint-solutions.md)  
  
  