---
title: 'Como: criar um receptor de evento para uma instância específica de lista | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, event receivers
- event receivers [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 4e5c68db8d1c9809e487fc8f64159d8b385a96a2
ms.sourcegitcommit: 1466ac0f49ebf7448ea4507ae3f79acb25d51d3e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/22/2018
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
  
    ```xml  
    <Receivers ListTemplateId="104">  
    ```  
  
     Altere esta linha para o seguinte texto:  
  
    ```xml  
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
  
  