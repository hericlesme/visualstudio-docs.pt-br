---
title: Visão geral de modelo de objeto do Outlook | Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VST.ProjectItem.OutlookAddin
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Outlook [Office development in Visual Studio], object model overview
- object models [Office development in Visual Studio], Office
- objects [Office development in Visual Studio], Office object models
- object models [Office development in Visual Studio], Outlook
- Office object models
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 7e2d0141611a13e7b1ee9b20b8988466c92f3ce2
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34693040"
---
# <a name="outlook-object-model-overview"></a>Visão geral de modelo de objeto do Outlook
  Para desenvolver suplementos do VSTO para Outlook do Microsoft Office, você pode interagir com os objetos que são fornecidos pelo modelo de objeto do Outlook. O modelo de objeto do Outlook fornece interfaces e classes que representam os itens na interface do usuário. Por exemplo, o <xref:Microsoft.Office.Interop.Outlook.Application> objeto representa o aplicativo inteiro, o <xref:Microsoft.Office.Interop.Outlook.MAPIFolder> objeto representa uma pasta que contém as mensagens de email ou outros itens, e o <xref:Microsoft.Office.Interop.Outlook.MailItem> objeto representa uma mensagem de email.  
  
 Este tópico fornece uma visão geral de alguns dos principais objetos no modelo de objeto do Outlook. Para obter recursos onde você pode aprender mais sobre todo o modelo de objeto do Outlook, consulte [usar a documentação de modelo de objeto do Outlook](#refdoc).  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
 ![link para vídeo](../vsto/media/playvideo.gif "link para vídeo") para uma demonstração de vídeo relacionada, consulte [How do i: Use o Outlook para criar um relatório de tarefa personalizada?](http://go.microsoft.com/fwlink/?LinkID=130315).  
  
## <a name="access-objects-in-an-outlook-project"></a>Acessar objetos em um projeto do Outlook  
 O Outlook fornece muitos objetos com os quais você pode interagir. Para usar o modelo de objeto com eficiência, você deve estar familiarizado com os seguintes objetos de nível superior:  
  
-   <xref:Microsoft.Office.Interop.Outlook.Application>  
  
-   <xref:Microsoft.Office.Interop.Outlook.Explorer>  
  
-   <xref:Microsoft.Office.Interop.Outlook.Inspector>  
  
-   <xref:Microsoft.Office.Interop.Outlook.MAPIFolder>  
  
-   <xref:Microsoft.Office.Interop.Outlook.MailItem>  
  
-   <xref:Microsoft.Office.Interop.Outlook.AppointmentItem>  
  
-   <xref:Microsoft.Office.Interop.Outlook.TaskItem>  
  
-   <xref:Microsoft.Office.Interop.Outlook.ContactItem>  
  
### <a name="application-object"></a>Objeto de aplicativo  
 O <xref:Microsoft.Office.Interop.Outlook.Application> objeto representa o aplicativo do Outlook, e é o objeto de nível mais alto no modelo de objeto do Outlook. Alguns dos membros do objeto mais importantes incluem:  
  
-   O [CreateItem](http://msdn.microsoft.com/en-us/771707fb-5f34-473d-9fdf-09a6a7f55ece) método que você pode usar para criar um novo item como uma mensagem de email, uma tarefa ou um compromisso.  
  
-   O <xref:Microsoft.Office.Interop.Outlook._Application.Explorers%2A> propriedade, que você pode usar para acessar as janelas que exibem o conteúdo de uma pasta na interface de usuário (UI) do Outlook.  
  
-   O <xref:Microsoft.Office.Interop.Outlook._Application.Inspectors%2A> propriedade, que você pode usar para acessar as janelas que exibem o conteúdo de um único item, como uma solicitação de reunião ou de mensagem de email.  
  
 Para obter uma instância do <xref:Microsoft.Office.Interop.Outlook.Application> de objeto, use o campo de aplicativo do `ThisAddIn` classe em seu projeto. Para obter mais informações, consulte [suplementos do VSTO do programa](../vsto/programming-vsto-add-ins.md).  
  
> [!NOTE]  
>  Para evitar avisos de segurança quando você usar propriedades e métodos que estão bloqueados pelo protetor de modelo de objeto do Outlook, obter objetos do Outlook do campo de aplicativo de `ThisAddIn` classe. Para obter mais informações, consulte [considerações de segurança específicas para soluções do Office](../vsto/specific-security-considerations-for-office-solutions.md).  
  
### <a name="explorer-object"></a>Objeto Explorer  
 O <xref:Microsoft.Office.Interop.Outlook.Explorer> objeto representa uma janela que exibe o conteúdo de uma pasta que contém itens como mensagens de email, tarefas ou compromissos. O <xref:Microsoft.Office.Interop.Outlook.Explorer> objeto inclui métodos e propriedades que você pode usar para modificar a janela e eventos que são gerados quando a janela é alterado.  
  
 Para obter um <xref:Microsoft.Office.Interop.Outlook.Explorer> de objeto, faça o seguinte:  
  
-   Use o <xref:Microsoft.Office.Interop.Outlook._Application.Explorers%2A> propriedade do <xref:Microsoft.Office.Interop.Outlook.Application> objeto para acessar todo o <xref:Microsoft.Office.Interop.Outlook.Explorer> objetos no Outlook.  
  
-   Use o <xref:Microsoft.Office.Interop.Outlook._Application.ActiveExplorer%2A> método o <xref:Microsoft.Office.Interop.Outlook.Application> objeto para obter o <xref:Microsoft.Office.Interop.Outlook.Explorer> que atualmente tem o foco.  
  
-   Use o `GetExplorer` método o <xref:Microsoft.Office.Interop.Outlook.MAPIFolder> objeto para obter o <xref:Microsoft.Office.Interop.Outlook.Explorer> para a pasta atual.  
  
### <a name="inspector-object"></a>Objeto do Inspetor  
 O <xref:Microsoft.Office.Interop.Outlook.Inspector> objeto representa uma janela que exibe um único item, como uma mensagem de email, uma tarefa ou um compromisso. O <xref:Microsoft.Office.Interop.Outlook.Inspector> objeto inclui métodos e propriedades que você pode usar para modificar a janela e eventos que são gerados quando a janela é alterado.  
  
 Para obter um <xref:Microsoft.Office.Interop.Outlook.Inspector> de objeto, faça o seguinte:  
  
-   Use o <xref:Microsoft.Office.Interop.Outlook._Application.Inspectors%2A> propriedade do <xref:Microsoft.Office.Interop.Outlook.Application> objeto para acessar todo o <xref:Microsoft.Office.Interop.Outlook.Inspector> objetos no Outlook.  
  
-   Use o <xref:Microsoft.Office.Interop.Outlook._Application.ActiveInspector%2A> método o <xref:Microsoft.Office.Interop.Outlook.Application> objeto para obter o <xref:Microsoft.Office.Interop.Outlook.Inspector> que atualmente tem o foco.  
  
-   Use o `GetInspector` método de um determinado item, como um <xref:Microsoft.Office.Interop.Outlook.MailItem> ou <xref:Microsoft.Office.Interop.Outlook.AppointmentItem>para recuperar o Inspetor que está associado ele.  
  
### <a name="mapifolder-object"></a>Objeto MAPIFolder  
 O <xref:Microsoft.Office.Interop.Outlook.MAPIFolder> objeto representa uma pasta que contém as mensagens de email, contatos, tarefas e outros itens. O Outlook fornece o padrão de 16 <xref:Microsoft.Office.Interop.Outlook.MAPIFolder> objetos.  
  
 O padrão <xref:Microsoft.Office.Interop.Outlook.MAPIFolder> objetos são definidos pelo <xref:Microsoft.Office.Interop.Outlook.OlDefaultFolders> valores de enumeração. Por exemplo,  
  
 Microsoft.Office.Interop.Outlook.OlDefaultFolders.olFolderInbox corresponde do **caixa de entrada** pasta no Outlook.  
  
 Para obter um exemplo que mostra como acessar um padrão <xref:Microsoft.Office.Interop.Outlook.MAPIFolder> e criar um novo <xref:Microsoft.Office.Interop.Outlook.MAPIFolder>, consulte [como: criar programaticamente os itens de pasta personalizados](../vsto/how-to-programmatically-create-custom-folder-items.md).  
  
### <a name="mailitem-object"></a>Objeto MailItem  
 O <xref:Microsoft.Office.Interop.Outlook.MailItem> objeto representa uma mensagem de email. <xref:Microsoft.Office.Interop.Outlook.MailItem> objetos geralmente estão em pastas, tais como **caixa de entrada**, **itens enviados**, e **caixa de saída**. <xref:Microsoft.Office.Interop.Outlook.MailItem> expõe as propriedades e métodos que podem ser usados para criar e enviar mensagens de email.  
  
 Para obter um exemplo que mostra como criar uma mensagem de email, consulte [como: criar programaticamente um item de email](../vsto/how-to-programmatically-create-an-e-mail-item.md).  
  
### <a name="appointmentitem-object"></a>Objeto AppointmentItem  
 O <xref:Microsoft.Office.Interop.Outlook.AppointmentItem> objeto representa uma reunião, um compromisso único ou um compromisso recorrente ou reunião no **calendário** pasta. O <xref:Microsoft.Office.Interop.Outlook.AppointmentItem> objeto inclui métodos que executam ações como responder a ou encaminhar solicitações de reunião e propriedades que especificam os detalhes de reuniões, como o local e a hora.  
  
 Para obter um exemplo que mostra como criar um compromisso, consulte [como: criar programaticamente uma solicitação de reunião](../vsto/how-to-programmatically-create-a-meeting-request.md).  
  
### <a name="taskitem-object"></a>Objeto TaskItem  
 O <xref:Microsoft.Office.Interop.Outlook.TaskItem> objeto representa uma tarefa a ser executada em um intervalo de tempo especificado. <xref:Microsoft.Office.Interop.Outlook.TaskItem> objetos estão localizados no **tarefas** pasta.  
  
 Para criar uma tarefa, use o [CreateItem](http://msdn.microsoft.com/en-us/771707fb-5f34-473d-9fdf-09a6a7f55ece) método o <xref:Microsoft.Office.Interop.Outlook.Application> de objeto e passar o valor <xref:Microsoft.Office.Interop.Outlook.OlItemType.olTaskItem> para o parâmetro.  
  
### <a name="contactitem-object"></a>Objeto ContactItem  
 O <xref:Microsoft.Office.Interop.Outlook.ContactItem>objeto representa um contato de **contatos** pasta. <xref:Microsoft.Office.Interop.Outlook.ContactItem> os objetos contêm uma variedade de informações de contato para as pessoas que eles representam, como endereços, endereços de email e números de telefone.  
  
 Para obter um exemplo que mostra como criar um novo contato, consulte [como: adicionar uma entrada a contatos do Outlook programaticamente](../vsto/how-to-programmatically-add-an-entry-to-outlook-contacts.md). Para obter um exemplo que mostra como pesquisar um contato existente, consulte [como: procurar um contato específico programaticamente](../vsto/how-to-programmatically-search-for-a-specific-contact.md).  
  
##  <a name="refdoc"></a> Use a documentação do modelo de objeto do Outlook  
 Para obter informações completas sobre o modelo de objeto do Outlook, você pode consultar para a referência de assembly de interoperabilidade primária (PIA) do Outlook e a referência de modelo de objeto VBA.  
  
### <a name="primary-interop-assembly-reference"></a>Referência de assembly de interoperabilidade primária  
 A referência do Outlook PIA documenta os tipos em assemblies de interoperabilidade primários para Outlook 2010. Para obter mais informações, consulte [referência de assembly de interoperabilidade primária do Outlook 2010](http://go.microsoft.com/fwlink/?LinkId=189580).  
  
 Além de fornecer informações para todos os tipos nos PIAs, esta documentação também fornece informações adicionais sobre a estrutura de PIAs e exemplos de código para tarefas comuns de automação do Outlook.  
  
### <a name="vba-object-model-reference"></a>Referência de modelo de objeto do VBA  
 A referência de modelo de objeto VBA documenta o modelo de objeto do Outlook, como ele é exposto para o Visual Basic para código Applications (VBA). Para obter mais informações, consulte [referência de modelo de objeto do Outlook 2010](http://go.microsoft.com/fwlink/?LinkId=199769).  
  
 Todos os objetos e membros na referência de modelo de objeto do VBA correspondem aos tipos e membros no PIA do Outlook. Por exemplo, o objeto do Inspetor na referência de modelo de objeto do VBA corresponde do <xref:Microsoft.Office.Interop.Outlook.Inspector> objeto o PIA do Outlook. Embora a referência de modelo de objeto VBA fornece exemplos de código para a maioria das propriedades, métodos e eventos, você deve converter o código VBA essa referência ao Visual Basic ou Visual c#, se você quiser usá-los em um projeto de suplemento do Outlook do VSTO que você cria usando O Visual Studio.  
  
### <a name="related-topics"></a>Tópicos relacionados  
  
|Título|Descrição|  
|-----------|-----------------|  
|[Trabalhar com itens de contato](../vsto/working-with-contact-items.md)|Fornece tópicos que mostram como executar tarefas com contatos.|  
|[Trabalhar com itens de email](../vsto/working-with-mail-items.md)|Fornece tópicos que mostram como executar tarefas com itens de email.|  
|[Trabalhar com pastas](../vsto/working-with-folders.md)|Fornece tópicos que mostram como executar tarefas de pastas.|  
|[Trabalhar com itens de calendário](../vsto/working-with-calendar-items.md)|Fornece tópicos que mostram como executar tarefas com itens de calendário.|  
|[Como: determinar programaticamente o item atual do Outlook](../vsto/how-to-programmatically-determine-the-current-outlook-item.md)|Mostra como exibir o nome da pasta atual e algumas informações sobre o item selecionado.|  
  