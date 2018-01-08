---
title: "Criando controles reutilizáveis para Web Parts ou páginas de aplicativo | Microsoft Docs"
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
- user controls [SharePoint development in Visual Studio], creating
- SharePoint development in Visual Studio, user controls
ms.assetid: 8fcafd98-c002-47f1-b4a9-cbb500232616
caps.latest.revision: "19"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 02847ae640f969d3c330b5eb573f36c74ef07a2f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="creating-reusable-controls-for-web-parts-or-application-pages"></a>Criando controles reutilizáveis para Web Parts ou páginas de aplicativo
  No Visual Studio, você pode criar controles reutilizáveis e personalizados que podem ser consumidos por páginas de aplicativos e Web Parts que são executados no SharePoint. Esses controles são chamados de controles de usuário. Um controle de usuário é um tipo de controle composto que funciona como uma página da Web do ASP.NET, você pode adicionar controles de servidor Web existentes e marcação para um controle de usuário e definir propriedades e métodos para o controle. Você pode, em seguida, inseri-los em páginas da Web ASP.NET, onde eles atuam como uma unidade.  
  
## <a name="creating-a-user-control"></a>Criando um controle de usuário  
 Para criar um controle de usuário, adicione um **controle de usuário** para um **projeto vazio do SharePoint**. Para obter mais informações, consulte [como: criar um controle de usuário para uma página de aplicativo do SharePoint ou a Web Part](../sharepoint/how-to-create-a-user-control-for-a-sharepoint-application-page-or-web-part.md).  
  
 Quando você adiciona um **controle de usuário** item, o Visual Studio cria uma pasta em seu projeto e, em seguida, adiciona vários arquivos na pasta. A tabela a seguir descreve cada arquivo.  
  
|Arquivo|Descrição|  
|----------|-----------------|  
|Arquivo de controle de usuário|Define o controle de usuário. Crie o controle de usuário, adicionando controles e marcação para esse arquivo.|  
|Arquivo de código|Contém o código de controle de usuário. Adicione código para tratar eventos neste arquivo.|  
|Arquivo de código de Designer|Contém o código gerado pelo designer e não deve ser editada diretamente.|  
  
## <a name="designing-the-user-control"></a>Criando o controle de usuário  
 Crie o controle de usuário usando o designer Visual Web Developer no Visual Studio. Esse designer é exibida quando você abre o arquivo de controle de usuário em seu projeto e escolha o **Design** guia.  

## <a name="consuming-the-user-control"></a>Consumindo o controle de usuário  
 Controles de usuário não aparecem no SharePoint até que você pode incluí-las em uma página de aplicativo ou uma Web Part.  
  
 Para incluir um controle de usuário em uma página de aplicativo, abra a página da Web para o qual você deseja adicionar o controle de usuário do ASP.NET. Alternar para modo de Design, selecione seu arquivo de controle de usuário personalizada no Gerenciador de soluções e arraste-o para a página. O controle de usuário do ASP.NET é adicionado à página, e o designer cria a diretiva @ Register, que é necessária para a página reconhecer o controle de usuário. Agora você pode trabalhar com o controle propriedades e métodos públicos.  
  
 Para incluir um controle de usuário em uma Web Part, adicione o controle de usuário para a Web Part <xref:System.Web.UI.WebControls.WebParts.Part.Controls%2A> coleta no arquivo de código da Web Part. O exemplo a seguir adiciona um controle de usuário para o <xref:System.Web.UI.WebControls.WebParts.Part.Controls%2A> coleção de uma Web Part.  
  
 [!code-vb[SP_VisualWebPart#5](../sharepoint/codesnippet/VisualBasic/sp_visualwebpart.vb/visualwebpart1/visualwebpart1.vb#5)]
 [!code-csharp[SP_VisualWebPart#5](../sharepoint/codesnippet/CSharp/sp_visualwebpart.cs/visualwebpart1/visualwebpart1.cs#5)]  
  
## <a name="debugging-a-user-control"></a>Depuração de um controle de usuário  
 Para depurar um controle de usuário, certifique-se de que o controle de usuário é incluído em uma página de aplicativo ou a Web Part em seu projeto do SharePoint. Em seguida, você pode depurar o código no controle de usuário exatamente como você faria para depurar código em qualquer projeto do Visual Studio.  
  
 Quando você inicia o depurador do Visual Studio, o Visual Studio abrirá o site do SharePoint.  
  
 No SharePoint, abra a página de aplicativo que inclui o controle de usuário. Se o controle de usuário é incluído em uma Web Part, adicione a Web Part a uma página de Web Part no SharePoint.  
  
 Para obter mais informações sobre como depurar projetos do SharePoint, consulte [Solucionando problemas de soluções do SharePoint](../sharepoint/troubleshooting-sharepoint-solutions.md).  
  
## <a name="related-topics"></a>Tópicos relacionados  
  
|Título|Descrição|  
|-----------|-----------------|  
|[Como criar um controle de usuário para uma página de aplicativo do SharePoint ou Web Part](../sharepoint/how-to-create-a-user-control-for-a-sharepoint-application-page-or-web-part.md)|Mostra como criar controles reutilizáveis e personalizados que podem ser consumidos por páginas de aplicativos e Web Parts que são executados no SharePoint.|  
  
  