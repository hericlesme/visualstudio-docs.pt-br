---
title: Instalar o Visual Studio versões lado a lado | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- side-by-side installations [Visual Studio]
- Help [Visual Studio], installing
- install multiple versions of Visual Studio
ms.assetid: 4d00f240-4910-4699-aaf3-cda6461f0c29
caps.latest.revision: 48
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.openlocfilehash: ae67e83b2f1444c09129ed5242afac2c3939c954
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47474653"
---
# <a name="install-visual-studio-versions-side-by-side"></a>Instalar o Visual Studio versões lado a lado
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

É possível instalar esta versão do Visual Studio em um computador que já tenha uma versão anterior instalada. Se você encontrar uma falha de instalação, você pode usar o [ferramenta de coleta de log](http://go.microsoft.com/fwlink/?LinkId=262077) para coletar informações sobre as falhas para que você possa depurar os problemas.  
  
> [!NOTE]
>  É recomendável que você instale [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] versões na ordem em que elas foram lançadas. Por exemplo, instale o Visual Studio 2013 antes de instalar o Visual Studio 2015.  
  
 Antes de instalar as versões lado a lado, revise as seguintes circunstâncias:  
  
-   Se você usar o Visual Studio 2015 para abrir uma solução que foi criada no [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)], mais tarde, você pode abrir e modificar a solução novamente na versão mais antiga, desde que você não tenha implementado quaisquer recursos que são específicos ao Visual Studio 2015.  
  
-   Se você tentar usar o Visual Studio 2015 para abrir uma solução que foi criada no [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)] ou uma versão anterior, você talvez precise modificar seus projetos e arquivos para serem compatíveis com o Visual Studio 2015. Para obter mais informações, consulte o [portar, migrar e atualizar projetos do Visual Studio](../misc/port-migrate-and-upgrade-visual-studio-projects-in-visual-studio-15-rc.md) página.  
  
-   Se você desinstalar uma versão do [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] em um computador que tem mais de uma versão instalada, as associações de arquivo do [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] são removidas para todas as versões. É possível remapear essas associações de arquivos usando o **restaurar associações de arquivos** botão a **ambiente**, **geral** página do [opções](../ide/reference/general-environment-options-dialog-box.md) caixa de diálogo.  
  
-   O Visual Studio não atualiza automaticamente extensões porque nem todas as extensões são compatíveis. Você deverá reinstalar as extensões do [Galeria do Visual Studio](http://go.microsoft.com/fwlink/?LinkId=178891) ou fornecedor de software.  
  
## <a name="net-framework-versions-and-side-by-side-installations"></a>Versões do .NET Framework e instalações lado a lado  
  
-   Projetos do Visual Basic, Visual c# e Visual F # usam a **estrutura de destino** opção a **Designer de projeto** para especificar qual versão do .NET Framework usa um projeto. Para um projeto do C++, é possível alterar manualmente a estrutura de destino alterando o arquivo .vcxproj. Para obter mais informações, consulte [compatibilidade de versão](http://msdn.microsoft.com/library/2f25e522-456a-48c3-8a53-e5f39275649f).  
  
     Quando você cria um projeto, você pode especificar qual versão do .NET Framework o projeto é direcionado na **do .NET Framework** lista o **novo projeto** caixa de diálogo.  
  
     Para informações específicas do idioma, consulte o tópico apropriado na tabela a seguir.  
  
    |Idioma|Tópico|  
    |--------------|-----------|  
    |[!INCLUDE[vbprvb](../includes/vbprvb-md.md)]|[Página de Aplicativo, Designer de Projeto (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md)|  
    |Visual C#|[Página Aplicativo, Designer de Projeto (C#)](../ide/reference/application-page-project-designer-csharp.md)|  
    |Visual F#|[Configurando Projetos](http://msdn.microsoft.com/library/a1489abb-6294-4f8f-b71f-2cb126393526)|  
    |C++|[Como modificar a estrutura de destino e o conjunto de ferramentas da plataforma](http://msdn.microsoft.com/library/031b1d54-e6e1-4da7-9868-3e75a87d9ffe)|  
    |[!INCLUDE[jsprjscript](../includes/jsprjscript-md.md)]|[Executar um aplicativo JScript em uma versão anterior do Common Language Runtime](http://msdn.microsoft.com/en-us/bbea51b5-ac03-4e6c-b9a6-f487ef63eda5)|  
  
## <a name="see-also"></a>Consulte também  
 [Instalar o Visual Studio](../install/install-visual-studio-2015.md) [portar, migrar e atualizar projetos do Visual Studio](../misc/port-migrate-and-upgrade-visual-studio-projects-in-visual-studio-15-rc.md)   
 [Criação de C/C++ de aplicativos isolados e Assemblies lado a lado](http://msdn.microsoft.com/library/9465904e-76f7-48bd-bb3f-c55d8f1699b6)   
 [Personalizando configurações de desenvolvimento no Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)