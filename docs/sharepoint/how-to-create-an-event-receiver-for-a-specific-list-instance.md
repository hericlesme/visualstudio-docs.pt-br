---
title: "Como: criar um receptor de evento para uma instância específica de lista | Microsoft Docs"
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
helpviewer_keywords:
- SharePoint development in Visual Studio, event receivers
- event receivers [SharePoint development in Visual Studio]
ms.assetid: 4b4b3564-161a-4327-8963-50896c084ac2
caps.latest.revision: "13"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 3db5af044b1e3eb25e68c96a42335082fd3523f1
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-create-an-event-receiver-for-a-specific-list-instance"></a>Como criar um receptor de evento para uma instância da lista específica
  Um receptor de evento de instância de lista responde a eventos que ocorrem em qualquer instância de uma definição de lista. Embora o modelo de receptor de evento não habilitar o direcionamento de uma instância de lista específica, você pode modificar um receptor de evento com escopo em uma definição de lista para responder a eventos em uma instância de lista específica.  
  
 Para direcionar uma instância de lista específica, em Elements para o receptor de evento, substitua `ListTemplateId` com `ListUrl` e adicione a URL da instância de lista.  
  
## <a name="creating-a-list-instance-event-receiver"></a>Criar um receptor de evento de instância de lista  
 As etapas a seguir mostram como modificar um receptor de eventos de item de lista para responder apenas aos eventos que ocorrem em uma instância de lista de anúncios personalizados.  
  
#### <a name="to-modify-an-event-receiver-to-respond-to-a-specific-list-instance"></a>Para modificar um receptor de eventos para responder a uma instância de lista específica  
  
1.  Em um navegador, abra o site do SharePoint.  
  
2.  No painel de navegação, **lista** link.  
  
3.  No **todo o conteúdo do Site** página, escolha o **criar** link.  
  
4.  No **criar** caixa de diálogo caixa, escolha o **anúncios** tipo, nome do anúncio **TestAnnouncements**e, em seguida, escolha o **criar**botão.  
  
5.  Em [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], criar um projeto de receptor de evento.  
  
6.  No **o tipo de receptor de eventos você deseja fazer?** , escolha **eventos de Item de lista**.  
  
    > [!NOTE]  
    >  Você também pode selecionar qualquer outro tipo de receptor de evento que tem como escopo uma definição de lista, por exemplo, **eventos de Email da lista** ou **eventos de fluxo de trabalho de lista**.  
  
7.  No **o item deve ser a origem do evento?** , escolha **anúncios**.  
  
8.  No **lidar com os seguintes eventos** lista, selecione o **está sendo adicionado a um item** caixa de seleção e, em seguida, escolha o **concluir** botão.  
  
9. Em **Solution Explorer**, em EventReceiver1, abra Elements.  
  
     O receptor de evento atualmente faz referência a definição da lista de anúncios usando a seguinte linha:  
  
    ```  
    <Receivers ListTemplateId="104">  
    ```  
  
     Altere esta linha para o seguinte texto:  
  
    ```  
    <Receivers ListUrl="Lists/TestAnnouncements">  
    ```  
  
     Isso instrui o receptor de evento responda apenas às eventos que ocorrem no novo **TestAnnouncements** lista de anúncios que você acabou de criar. Você pode alterar o `ListURL` atributo para fazer referência a qualquer instância de lista no servidor do SharePoint.  
  
10. Abra o arquivo de código para o receptor de evento e colocar um ponto de interrupção no método ItemAdding.  
  
11. Escolha a tecla F5 para compilar e executar a solução.  
  
12. No SharePoint, escolha o **TestAnnouncements** link no painel de navegação.  
  
13. Escolha o **adicionar novo aviso** link.  
  
14. Insira um título para o anúncio e, em seguida, escolha o **salvar** botão.  
  
     Observe que o ponto de interrupção é atingido quando o novo item é adicionado à lista de anúncios personalizados.  
  
15. Escolha a tecla F5 para continuar.  
  
16. No painel de navegação, escolha o **lista** link e, em seguida, escolha o **anúncios** link.  
  
17. Adicione um novo comunicado.  
  
     Observe que o receptor de evento não disparam no novo anúncio porque o receptor está configurado para responder apenas aos eventos na instância de lista personalizada de lançamento, **TestAnnouncements**.  
  
## <a name="see-also"></a>Consulte também  
 [Como: criar um receptor de evento](../sharepoint/how-to-create-an-event-receiver.md)   
 [Desenvolvendo soluções do SharePoint](../sharepoint/developing-sharepoint-solutions.md)  
  
  