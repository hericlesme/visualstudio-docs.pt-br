---
title: A chamada para os modelos de objeto do SharePoint | Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, client object model
- SharePoint development in Visual Studio, server object model
- SharePoint commands [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, extensibility features
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 24d8c7824e9bf90538a7d4dd1ae230d37cfbdb2f
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/05/2018
ms.locfileid: "34765551"
---
# <a name="call-into-the-sharepoint-object-models"></a>Chamar os modelos de objeto do SharePoint
  Quando você criar extensões para ferramentas do SharePoint no Visual Studio, você terá que chamar as APIs do SharePoint para realizar certas tarefas. Por exemplo, se você criar uma etapa de implantação para projetos do SharePoint, você talvez precise chamar as APIs para executar algumas tarefas para implantar soluções do SharePoint.  
  
 [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] e [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] fornecem dois modelos de objeto diferentes que você pode usar extensões de ferramentas do SharePoint: um modelo de objeto de servidor e um modelo de objeto do cliente. Cada modelo de objeto tem vantagens e desvantagens no contexto de extensões de ferramentas do SharePoint.  
  
 Para obter uma visão geral dos modelos de objeto do SharePoint, consulte [visão geral sobre as extensões de ferramentas de programação modelo do SharePoint](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md).  
  
## <a name="use-the-client-object-model-in-extension-projects"></a>Use o modelo de objeto do cliente em projetos de extensão
 Quando você desenvolve uma extensão para as ferramentas do SharePoint, você pode usar o modelo de objeto do cliente em seu projeto como qualquer outro conjunto de APIs gerenciadas. Você pode adicionar referências a assemblies no modelo de objeto de cliente ao seu projeto e você pode chamar APIs no modelo de objeto de cliente diretamente do seu código.  
  
 No entanto, o modelo de objeto do cliente tem duas desvantagens no contexto de extensões de ferramentas do SharePoint:  
  
-   O modelo de objeto do cliente fornece apenas um subconjunto do modelo de objeto de servidor. Se você tiver que usar a funcionalidade do SharePoint que não é exposta no modelo de objeto de cliente, você deve usar o modelo de objeto do servidor.  
  
-   Embora usando o modelo de objeto de cliente em extensões de ferramentas do SharePoint deve funcionar na maioria dos casos, você pode encontrar alguns cenários onde chamadas para o modelo de objeto do cliente não funcionam conforme o esperado. O modelo de objeto do cliente foi projetado para ser usado em aplicativos cliente para chamar em sites do SharePoint em um farm ou servidor remoto. Ferramentas do SharePoint no Visual Studio funcionam somente com uma instalação local do SharePoint no computador de desenvolvimento. Portanto, quando você usa o modelo de objeto do cliente em uma extensão de ferramentas do SharePoint, você chamar em um site do SharePoint no computador local, que não é como o modelo de objeto do cliente foi projetado para ser usado.  
  
 Para uma explicação passo a passo que demonstra como usar o modelo de objeto do cliente em uma extensão de ferramentas do SharePoint no Visual Studio, consulte [passo a passo: chamando o modelo de objeto de cliente do SharePoint em uma extensão do Gerenciador de servidores](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md).  
  
## <a name="use-the-server-object-model-in-extension-projects"></a>Use o modelo de objeto de servidor em projetos de extensão
 O modelo de objeto de servidor é um superconjunto do modelo de objeto de cliente. Quando você usa o modelo de objeto de servidor, você pode usar todos os recursos que [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] e [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] expor por meio de programação.  

 Extensões de ferramentas do SharePoint podem usar as APIs no modelo de objeto do servidor, mas eles não é possível chamar as APIs diretamente. O modelo de objeto de servidor pode ser chamado apenas de um processo de 64 bits que tem como destino o .NET Framework 3.5. No entanto, extensões de ferramentas do SharePoint exigem o [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] e que são executados no processo do Visual Studio de 32 bits. Isso impede que as extensões de ferramentas do SharePoint referenciar os assemblies no modelo de objeto do SharePoint server diretamente.  
  
 Se você quiser usar o modelo de objeto de servidor em uma extensão de ferramentas do SharePoint, você deve criar um personalizado *comando SharePoint* para chamar a API. Você pode definir o comando do SharePoint em um assembly secundário que pode chamar diretamente o modelo de objeto do servidor. No seu projeto de extensão, você chamar o comando do SharePoint indiretamente por meio do método ExecuteCommand de um <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection> objeto.  
  
 Para obter mais informações sobre como criar e usar comandos do SharePoint, consulte [como: criar um comando SharePoint](../sharepoint/how-to-create-a-sharepoint-command.md) e [como: executar um comando SharePoint](../sharepoint/how-to-execute-a-sharepoint-command.md). Para obter informações sobre como implantar comandos do SharePoint, consulte [implantação de extensões para ferramentas do SharePoint no Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
 Para instruções passo a passo que demonstre como criar e usar comandos do SharePoint, consulte [passo a passo: Criando uma etapa de implantação personalizada para projetos SharePoint](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md) e [passo a passo: estendendo o Gerenciador de servidores Web de exibição Partes](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md).  
  
### <a name="understand-how-sharepoint-commands-are-executed"></a>Entender como os comandos do SharePoint são executados
 Assemblies que definem os comandos do SharePoint são carregados em um processo de host de 64 bits chamado *vssphost4.exe*. Depois de chamar um comando do SharePoint em uma extensão de ferramentas do SharePoint, o comando é executado por *vssphost4.exe* em vez de processo do Visual Studio de 32 bits (*devenv.exe*). Você pode controlar alguns aspectos de como os comandos do SharePoint são executados, definindo valores no registro. Para obter mais informações, consulte [depuração extensões para ferramentas do SharePoint no Visual Studio](../sharepoint/debugging-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## <a name="see-also"></a>Consulte também
 [Como: criar um comando do SharePoint](../sharepoint/how-to-create-a-sharepoint-command.md)   
 [Como: executar um comando do SharePoint](../sharepoint/how-to-execute-a-sharepoint-command.md)   
 [Visão geral do modelo de programação das extensões das Ferramentas do SharePoint](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)  
  
