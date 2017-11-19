---
title: Desenvolvimento do Office e do SharePoint no Visual Studio | Microsoft Docs
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
- Office applications [Office development in Visual Studio], about developing applications
- Office development in Visual Studio
- Office projects
- Visual Studio Tools for Office, see Office development in Visual Studio
- Office applications [Office development in Visual Studio]
- Office Business Applications
- applications [Office development in Visual Studio]
- programming [Office development in Visual Studio]
- VSTO, see Office development in Visual Studio
- Office, development with Visual Studio
ms.assetid: 2ddec047-263a-4901-a54c-a15fc8472329
caps.latest.revision: "88"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 236bd457f478d21ed27d31b0a28871e1102a1547
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="office-and-sharepoint-development-in-visual-studio"></a>Desenvolvimento do Office e do SharePoint no Visual Studio
  Você pode estender o Microsoft Office e SharePoint, criando um aplicativo simples ou suplemento que os usuários baixem do [Office Store](https://store.office.com/) ou uma unidade organizacional do catálogo ou criando uma solução baseada no .NET Framework que os usuários de instalar em um computador.  
  
 Neste tópico:  
  
-   [Criar suplementos para o Office e SharePoint](#Apps)  
  
-   [Criar um suplemento do VSTO](#Add-ins)  
  
-   [Criar uma solução do SharePoint](#Solutions)  
  
##  <a name="Apps"></a>Criar suplementos para o Office e SharePoint  
 Office 2013 e SharePoint 2013 introduz um novo suplemento do modelo que ajuda a criar, distribuir e monetizar suplementos que estendem o Office e SharePoint.  Esses suplementos podem executar no Office ou SharePoint Online e os usuários podem interagir com eles de muitos dispositivos.  
  
 Saiba como usar o novo [modelo de suplemento do Office](https://msdn.microsoft.com/library/office/jj220082.aspx) para estender a experiência para os usuários do Office.  
  
 Esses suplementos têm volumes muito pequenos em comparação com suplementos do VSTO e soluções e você pode criá-los usando quase qualquer tecnologia, como JavaScript, HTML5, CSS3 e XML de programação da web.  Para começar, use as ferramentas de desenvolvedor do Office no Visual Studio ou a ferramenta de baseado na web leve codinome Napa Office 365 ferramentas de desenvolvimento, que lhe permite criar projetos, gravar o código e execute-los em um navegador.  
  
 ![Aplicativos para Office e SharePoint modelo conceitual](../vsto/media/officeandsharepointapps2015.png "aplicativos para Office e SharePoint modelo conceitual")  
  
 **Saiba mais**  
  
|Para|Consulte|  
|--------|---------|  
|Saiba mais sobre as ferramentas de desenvolvimento Napa Office 365.|[Ferramentas de desenvolvimento do Office 365 Napa](https://msdn.microsoft.com/library/dn974046.aspx)|  
  
### <a name="build-an-office-add-in"></a>Criar um suplemento do Office  
 Para estender a funcionalidade do Office, crie um suplemento do Office. Ele é basicamente uma página da Web que é hospedada em um aplicativo do Office como Word, Excel, Outlook e PowerPoint. Seu aplicativo pode adicionar funcionalidade a documentos, planilhas, mensagens de email, compromissos, apresentações e projetos.  
  
 Você pode vender seu aplicativo na Office Store.  O [Office Store](https://store.office.com/) facilita a monetizar seus suplementos, gerenciamento de atualizações e acompanhar a telemetria. Você também pode publicar seu aplicativo para usuários por meio de um aplicativo de aplicativos no SharePoint ou no Exchange Server.  
  
 O seguinte aplicativo do Office mostra os dados da planilha em um mapa do Bing.  
  
 ![Aplicativo de conteúdo para o Office](../vsto/media/appforoffice.png "aplicativo de conteúdo para o Office")  
  
 **Saiba mais**  
  
|Para|Consulte|  
|--------|---------|  
|Saiba mais sobre os suplementos do Office e, em seguida, crie um.|[Suplementos do Office](http://msdn.microsoft.com/office/dn448457)|  
|Compare as diferentes maneiras em que você pode estender o Office e decidir se deve usar um aplicativo ou um suplemento do Office.|[Roteiro para Office suplementos do VSTO e VBA](http://blogs.msdn.com/b/officeapps/archive/2013/06/18/roadmap-for-apps-for-office-vsto-and-vba.aspx)|  
|Saiba mais sobre as ferramentas de desenvolvimento Napa Office 365.|[Ferramentas de desenvolvimento do Office 365 Napa](https://msdn.microsoft.com/library/dn974046.aspx)|  
  
### <a name="build-a-sharepoint-add-in"></a>Criar um suplemento do SharePoint  
 Para estender o SharePoint para os usuários, crie um suplemento do SharePoint. É basicamente um aplicativo autônomo, pequeno, fácil de usar que resolve a necessidade dos usuários ou business.  
  
 Você pode vender seu aplicativo para SharePoint no [Office Store](https://store.office.com/). Você também pode publicar seu suplemento aos usuários por meio de um catálogo de suplemento do SharePoint.  Os proprietários de site podem instalar, atualizar e desinstalar o suplemento em seus sites do SharePoint, sem a Ajuda de um servidor de farm ou administrador do conjunto de sites.  
  
 Aqui está um exemplo de um aplicativo do SharePoint que ajuda os usuários a gerenciar contatos comerciais.  
  
 ![Aplicativo do Gerenciador de contato de negócios para SharePoint](../vsto/media/appforsharepoint.png "aplicativo do Gerenciador de contato de negócios para SharePoint")  
  
 **Saiba mais**  
  
|Para|Consulte|  
|--------|---------|  
|Saiba mais sobre os suplementos do SharePoint e, em seguida, crie um.|[Suplementos do SharePoint](https://msdn.microsoft.com/library/office/fp179930.aspx)|  
|Compare os suplementos para SharePoint com tradicionais soluções de SharePoint.|[Suplementos de SharePoint, em comparação com as soluções do SharePoint](http://msdn.microsoft.com/library/office/jj163114.aspx)|  
|Escolha se deseja criar um suplemento do SharePoint ou uma solução do SharePoint.|[Decidir entre o SharePoint add-ins e soluções do SharePoint](https://msdn.microsoft.com/library/office/jj163114.aspx)|  
|Saiba mais sobre as ferramentas de desenvolvimento Napa Office 365.|[Ferramentas de desenvolvimento do Office 365 Napa](https://msdn.microsoft.com/library/dn974046.aspx)|  
  
##  <a name="Add-ins"></a>Criar um suplemento do VSTO  
 Crie um suplemento de VSTO para Office 2007 ou o Office 2010 de destino, ou estender o Office 2013 e Office 2016 além do que é possível com os suplementos do Office. Suplementos do VSTO executados apenas na área de trabalho. Os usuários precisam instalar suplementos do VSTO, para que eles sejam normalmente mais difícil de implantar e oferecer suporte.  No entanto, o suplemento do VSTO pode ser integrado melhor com o Office. Por exemplo, ele pode adicionar controles à Faixa de Opções do Office e executar tarefas de automação avançadas como mesclar documentos ou modificar gráficos. Você pode aproveitar o .NET Framework e usar o C# e o Visual Basic para interagir com objetos do Office.  
  
 Aqui está um exemplo que um suplemento do VSTO pode fazer. Esse suplemento do VSTO adiciona os controles de faixa de opções, um painel tarefa personalizada e uma caixa de diálogo para o PowerPoint.  
  
 ![Solução de suplemento do PowerPoint](../vsto/media/powerpointaddin.png "solução de suplemento do PowerPoint")  
  
 **Saiba mais**  
  
|Para|Ler|  
|--------|----------|  
|Compare as diferentes maneiras em que você pode estender o Office e decidir se deve usar um suplemento do VSTO ou um suplemento do Office.|[Roteiro para Office suplementos do VSTO e VBA](http://blogs.msdn.com/b/officeapps/archive/2013/06/18/roadmap-for-apps-for-office-vsto-and-vba.aspx)|  
|Crie um suplemento do VSTO.|[Criar suplementos do VSTO com o Visual Studio](https://msdn.microsoft.com/library/jj620922.aspx)|  
  
##  <a name="Solutions"></a>Criar uma solução do SharePoint  
 Crie uma solução do SharePoint para SharePoint Foundation 2010 e SharePoint Server 2010 de destino, ou estender o SharePoint 2013 e SharePoint 2016 maneiras além do que é possível com um suplemento do SharePoint.  
  
 Soluções do SharePoint exigem servidores de farm do SharePoint no local. Os administradores devem instalá-los e, como soluções são executada no SharePoint, podem afetar o desempenho do servidor. No entanto, soluções fornecem maior acesso a objetos do SharePoint. Além disso, quando você cria uma solução do SharePoint, pode utilizar o .NET Framework e usar C# e Visual Basic para interagir com objetos do SharePoint.  
  
 **Saiba mais**  
  
|Para|Consulte|  
|--------|---------|  
|Compare as soluções do SharePoint com os suplementos do SharePoint.|[Suplementos de SharePoint, em comparação com as soluções do SharePoint](http://msdn.microsoft.com/library/office/jj163114.aspx)|  
|Criar uma solução do SharePoint.|[Criar soluções do SharePoint](../sharepoint/create-sharepoint-solutions.md)|  
  
  