---
title: Criar suplementos do VSTO para Office usando o Visual Studio | Microsoft Docs
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
ms.assetid: eabd0377-cb94-4c1e-a99c-f13ff8df1a87
caps.latest.revision: "12"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 16d3e15187d6164bf0b659a94ac81d26a8bf6a5c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="create-vsto-add-ins-for-office-by-using-visual-studio"></a>Criar suplementos do VSTO para o Office usando o Visual Studio
  Você pode usar as ferramentas de desenvolvedor do Microsoft Office no Visual Studio para criar aplicativos do .NET Framework que estendem o Office. Esses aplicativos também são chamados de *soluções do Office*.  
  
 As ferramentas do desenvolvedor do Office fornecem recursos que ajudam a criar soluções do Office para atender a uma variedade de necessidades comerciais. As ferramentas incluem modelos de projeto para ajudá-lo a criar soluções do Office usando Visual Basic ou Visual C#, além de designers visuais que ajudam a criam interfaces de usuário personalizada para as soluções do Office.  
  
> [!NOTE]  
>  Interessado em desenvolvimento de soluções que estendem a experiência do Office em [várias plataformas](https://dev.office.com/add-in-availability)? Confira a nova [modelo de suplementos do Office](https://dev.office.com/docs/add-ins/overview/office-add-ins). Suplementos do Office têm uma superfície pequena em comparação com suplementos do VSTO e soluções, e você pode criá-los usando quase qualquer tecnologia, como JavaScript, HTML5, CSS3 e XML de programação da web.  
  
 Para obter as informações mais recentes sobre o desenvolvimento do Office, consulte os seguintes centros de desenvolvimento no MSDN:  
  
-   O [desenvolvimento do Office com o Portal do desenvolvedor do Visual Studio](http://go.microsoft.com/fwlink/?LinkId=123844) contém links para informações sobre o produto, exemplos de código, vídeos e recursos da comunidade sobre o uso do Visual Studio para personalizar os aplicativos do Office como parte de suas soluções .  
  
-   O [Microsoft Office Developer Center](http://go.microsoft.com/fwlink/?LinkId=83467) contém links para artigos técnicos, exemplos de código, downloads, informações da comunidade, suporte e outras documentações sobre personalizações do Office e aplicativos de negócios do Office (OBAs ).  
  
## <a name="in-this-section"></a>Nesta seção  
 [Guia de Introdução &#40; desenvolvimento do Office no Visual Studio &#41;](../vsto/getting-started-office-development-in-visual-studio.md)  
 Fornece links para informações sobre como configurar um computador de desenvolvimento para criar soluções do Office, como começar a criar soluções do Office e o que há de novo para desenvolvimento do Office no Visual Studio.  
  
 [Atualizando e migrando soluções do Office](../vsto/upgrading-and-migrating-office-solutions.md)  
 Fornece links para informações sobre o processo de atualização de projetos criados usando versões anteriores do Visual Studio.  
  
 [Arquitetura de soluções do Office no Visual Studio](../vsto/architecture-of-office-solutions-in-visual-studio.md)  
 Fornece links para informações sobre como as soluções do Office funcionam, incluindo informações sobre personalizações no nível do documento e suplementos do VSTO.  
  
 [Projetando e criando soluções do Office](../vsto/designing-and-creating-office-solutions.md)  
 Fornece informações sobre como criar um projeto do Office e configurá-lo no Visual Studio.  
  
 [Desenvolvendo soluções do Office](../vsto/developing-office-solutions.md)  
 Fornece informações sobre como usar o código gerenciado com soluções do Office, incluindo como personalizar a interface de usuário do Office, trabalhar com dados e solucionar problemas.  
  
 [Soluções do Excel](../vsto/excel-solutions.md)  
 Fornece informações sobre como automatizar o Excel, criar soluções do Excel e entender os problemas de globalização específicos do Excel.  
  
 [Soluções InfoPath](../vsto/infopath-solutions.md)  
 Fornece informações sobre como criar modelos de formulário e suplementos do VSTO para InfoPath.  
  
 [Soluções do Outlook](../vsto/outlook-solutions.md)  
 Fornece informações sobre como automatizar o Outlook e criar suplementos do VSTO do Outlook e regiões de formulário.  
  
 [Soluções PowerPoint](../vsto/powerpoint-solutions.md)  
 Fornece informações sobre como automatizar o PowerPoint e criar suplementos do VSTO do PowerPoint.  
  
 [Soluções do projeto](../vsto/project-solutions.md)  
 Fornece informações sobre como automatizar o Microsoft Office Project e criar suplementos do VSTO do projeto.  
  
 [Soluções do Visio](../vsto/visio-solutions.md)  
 Fornece informações sobre como automatizar o Visio e criar suplementos do VSTO Visio.  
  
 [Soluções do Word](../vsto/word-solutions.md)  
 Fornece informações sobre como automatizar o Word e criar soluções do Word.  
  
 [Compilando soluções do Office](../vsto/building-office-solutions.md)  
 Fornece informações sobre as diferenças entre a criação de projetos do Office e outros tipos de projetos no [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
 [Depurando projetos do Office](../vsto/debugging-office-projects.md)  
 Fornece informações sobre as diferenças entre a depuração de projetos do Office e outros tipos de projetos no [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
 [Protegendo soluções do Office](../vsto/securing-office-solutions.md)  
 Fornece informações sobre como os recursos de segurança funcionam em soluções do Office.  
  
 [Implantando uma solução do Office](../vsto/deploying-an-office-solution.md)  
 Fornece informações sobre como criar soluções do Office disponíveis para os usuários e os principais problemas a serem considerados ao escolher um método de implantação.  
  
 [Explicações passo a passo e exemplos de desenvolvimento do office](../vsto/office-development-samples-and-walkthroughs.md)  
 Fornece links para tópicos que fornecem instruções passo a passo para executar tarefas comuns e aplicativos de exemplo.  
  
 [Referência geral &#40; desenvolvimento do Office no Visual Studio &#41;](../vsto/general-reference-office-development-in-visual-studio.md)  
 Fornece links para informações detalhadas sobre Assemblies de interoperabilidade primária do Office, manifestos, elementos de interface do usuário e mensagens de erro.  
  
 [Gerenciado referência &#40; desenvolvimento do Office no Visual Studio &#41;](../vsto/managed-reference-office-development-in-visual-studio.md)  
 Fornece links para informações sobre namespaces de API e tipos que são usados em projetos do Office destinados a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]. Para obter a documentação de referência de API sobre os namespaces e tipos que são usados em projetos do Office destinados ao .NET Framework 3.5, consulte a seguinte seção de referência na documentação do Visual Studio 2008: [2007 sistema gerenciado referência](http://go.microsoft.com/fwlink/?LinkId=160658).  
  
 [Referência de API não gerenciada &#40; desenvolvimento do Office no Visual Studio &#41;](../vsto/unmanaged-api-reference-office-development-in-visual-studio.md)  
 Contém links para informações sobre interfaces COM que você pode usar para executar ações como carregar e descarregar gerenciados suplementos do VSTO em aplicativos do Office.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Desenvolvimento do Office com o Portal do desenvolvedor do Visual Studio](http://go.microsoft.com/fwlink/?LinkId=123844)  
 Fornece recursos adicionais, como artigos técnicos, vídeos e blogs.  
  
 [Centro de desenvolvedores do Visual Studio](http://go.microsoft.com/fwlink/?LinkID=99124)  
 Fornece recursos adicionais do Visual Studio, como artigos técnicos, vídeos e blogs.  
  
 [Portal do desenvolvedor de aplicativos do Office Business](http://go.microsoft.com/fwlink/?LinkId=99125)  
 Fornece informações sobre Aplicativos de Negócios do Office (OBAs) e como criá-los usando a plataforma do sistema Office.  
  
 [Seção de desenvolvimento do Microsoft Office da biblioteca MSDN](http://go.microsoft.com/fwlink/?LinkId=149870)  
 A área da biblioteca MSDN onde você pode encontrar artigos e consultar a documentação sobre desenvolvimento de soluções para várias versões do Office (não específica para desenvolvimento do Office usando o Visual Studio).  
  
 [Desenvolvimento de aplicativos no Visual Studio](http://msdn.microsoft.com/en-us/97490c1b-a247-41fb-8f2c-bc4c201eff68)  
 Contém links para tópicos que explicam como usar o Visual Studio para projetar, desenvolver, depurar e implantar aplicativos da web, XML de serviços da web e aplicativos clientes tradicionais.  
  
 [Programação do .NET framework no Visual Studio](http://msdn.microsoft.com/en-us/f3f63195-82c6-48e8-a4a0-612810e7d093)  
 Discute o desenvolvimento de aplicativos com o .NET Framework no Visual Basic e Visual C#.  
  
  