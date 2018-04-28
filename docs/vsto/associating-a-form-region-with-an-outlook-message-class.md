---
title: Associando uma região de formulário uma classe de mensagem do Outlook | Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology: office-development
ms.prod: visual-studio-dev15
ms.topic: conceptual
f1_keywords:
- VSTO.NewFormRegionWizard.InvalidMessageClassName
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- FormRegionMessageClassAttribute
- form regions [Office development in Visual Studio], message classes
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: e3e3deeb55fb93b1a393d0489213f1d0e7acd85b
ms.sourcegitcommit: 04a717340b4ab4efc82945fbb25dfe58add2ee4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2018
---
# <a name="associating-a-form-region-with-an-outlook-message-class"></a>Associando uma região de formulário a uma classe de mensagem do Outlook
  Você pode especificar quais itens do Microsoft Office Outlook exibem uma região de formulário, associando a região de formulário com a classe de mensagem de cada item. Por exemplo, se você deseja acrescentar uma região de formulário para a parte inferior de um item de email, você pode associar uma região de formulário com o IPM. Observe a classe de mensagem.  
  
 Para associar uma região de formulário uma classe de mensagem, especifique o nome de classe de mensagem no **nova região de formulário do Outlook** assistente ou aplicar um atributo para a classe de fábrica de região de formulário.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## <a name="understanding-outlook-message-classes"></a>Noções básicas sobre Classes de mensagem do Outlook  
 Uma classe de mensagem do Outlook identifica um tipo de item do Outlook. A tabela a seguir lista esses oito tipos padrão de itens e seus nomes de classe de mensagem.  
  
|Tipo de Item do Outlook|Nome da classe de mensagem|  
|-----------------------|------------------------|  
|AppointmentItem|IPM. Compromisso|  
|ContactItem|IPM. Entre em contato com|  
|DistListItem|IPM. DistList|  
|JournalItem|IPM. Atividade|  
|MailItem|IPM. Observação|  
|PostItem|IPM. POST ou IPM. Post.RSS|  
|TaskItem|IPM. Tarefa|  
  
 Você também pode especificar os nomes das classes de mensagem personalizada. Classes de mensagem personalizado identificam formulários personalizados que você define no Outlook.  
  
> [!NOTE]  
>  Para a substituição e regiões de formulário de substituir tudo, você pode especificar um novo nome de classe de mensagem personalizada. Você não precisa usar o nome de classe de mensagem de um formulário personalizado existente. O nome da classe de mensagem personalizada deve ser exclusivo. Uma maneira de garantir que o nome é exclusivo é usar uma convenção de nomenclatura semelhante à seguinte: \< *StandardMessageClassName*>.\< *Empresa*>.\< *MessageClassName*> (por exemplo: IPM. Note.Contoso.MyMessageClass).  
  
## <a name="associating-a-form-region-with-an-outlook-message-class"></a>Associando uma região de formulário a uma classe de mensagem do Outlook  
 Há duas maneiras para associar uma região de formulário uma classe de mensagem:  
  
-   Use o **nova região de formulário do Outlook** assistente.  
  
-   Aplica atributos de classe.  
  
### <a name="using-the-new-outlook-form-region-wizard"></a>Usando o novo Assistente de região de formulário do Outlook  
 Na página final do **nova região de formulário do Outlook** assistente, você pode selecionar as classes de mensagem padrão e digite os nomes das classes de mensagem personalizada que você deseja associar com a região do formulário.  
  
 As classes de mensagem padrão não estarão disponíveis se a região de formulário é projetada para substituir todo o formulário ou a página padrão de um formulário. Você pode especificar nomes de classe de mensagem padrão somente para formulários que adicionar uma nova página a um formulário ou que são acrescentados à parte inferior de um formulário. Para obter mais informações, consulte [como: adicionar uma região de formulário a um projeto de suplemento do Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md).  
  
 Para incluir uma ou mais classes de mensagem personalizada, digite seus nomes no **quais classes de mensagem personalizada exibirá essa região de formulário?** caixa.  
  
 Os nomes que você digitar devem estar em conformidade com as diretrizes a seguir:  
  
-   Use o nome de classe de mensagem totalmente qualificado (por exemplo: "IPM. Note.Contoso").  
  
-   Use ponto e vírgula para separar vários nomes de classe de mensagem.  
  
-   Não inclua padrão classes de mensagem do Outlook, como "IPM. Observação"ou"IPM. Contato". Incluir apenas as classes de mensagem personalizada, como "IPM. Note.Contoso".  
  
-   Não especifique a classe base de mensagem por si só (por exemplo: "IPM").  
  
-   Não exceda 256 caracteres para cada nome de classe de mensagem.  
  
 O **nova região de formulário do Outlook** assistente valida o formato de sua entrada quando você clica em **concluir**.  
  
> [!NOTE]  
>  O **nova região de formulário do Outlook** assistente não verifique se os nomes de classe de mensagem que você fornece estão corretas ou válido.  
  
 Quando você concluir o assistente, o **nova região de formulário do Outlook** assistente aplica atributos para a classe de região de formulário que contém os nomes de classe de mensagem especificada. Você também pode aplicar manualmente esses atributos.  
  
### <a name="applying-class-attributes"></a>Aplicando atributos de classe  
 Você pode associar uma região de formulário com uma classe de mensagem do Outlook depois de concluir o **nova região de formulário do Outlook** assistente. Para fazer isso, aplica atributos para a classe de fábrica de região de formulário.  
  
 O exemplo a seguir mostra duas <xref:Microsoft.Office.Tools.Outlook.FormRegionMessageClassAttribute> atributos que foram aplicados a uma classe de fábrica de região de formulário chamada `myFormRegion`. O primeiro atributo associa a região de formulário de uma classe de mensagem padrão para um formulário de mensagem de email. O segundo atributo associa a região de formulário uma classe de mensagem personalizada denominada `IPM.Task.Contoso`.  
  
 [!code-vb[Trin_Outlook_FR_Attributes#1](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Attributes/FormRegion1.vb#1)]
 [!code-csharp[Trin_Outlook_FR_Attributes#1](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Attributes/FormRegion1.cs#1)]  
  
 Atributos devem estar de acordo com as diretrizes a seguir:  
  
-   Para classes de mensagem personalizada, use o nome da classe de mensagem totalmente qualificado (por exemplo: "IPM. Note.Contoso").  
  
-   Não especifique a classe base de mensagem por si só (por exemplo: "IPM").  
  
-   Não exceda 256 caracteres para cada nome de classe de mensagem.  
  
-   Não inclua os nomes das classes de mensagem padrão se a região de formulário substitui todo o formulário ou a página padrão de um formulário. Você pode especificar nomes de classe de mensagem padrão somente para formulários que adicionar uma nova página a um formulário ou que são acrescentados à parte inferior de um formulário. Para obter mais informações, consulte [como: adicionar uma região de formulário a um projeto de suplemento do Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md).  
  
 Quando você compilar o projeto, o Visual Studio valida o formato dos nomes de classe de mensagem.  
  
> [!NOTE]  
>  O Visual Studio não verifique se os nomes de classe de mensagem que você fornecer correto ou válido.  
  
## <a name="see-also"></a>Consulte também  
 [Acessando uma região de formulário em tempo de execução](../vsto/accessing-a-form-region-at-run-time.md)   
 [Criando regiões de formulário do Outlook](../vsto/creating-outlook-form-regions.md)   
 [Passo a passo: Criando uma região de formulário do Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md)   
 [Diretrizes para criação de regiões de formulário do Outlook](../vsto/guidelines-for-creating-outlook-form-regions.md)   
 [Nome do formulário e visão geral de classe de mensagem](http://msdn.microsoft.com/library/office/ff867629.aspx)   
 [Como os formulários do Outlook e itens funcionam em conjunto](http://msdn.microsoft.com/library/office/ff869706.aspx)  
  
  