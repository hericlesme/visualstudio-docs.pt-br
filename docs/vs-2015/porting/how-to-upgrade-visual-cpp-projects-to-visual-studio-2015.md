---
title: 'Como: atualizar projetos do Visual C++ para Visual Studio 2015 | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- projects [C++], upgrading
ms.assetid: 9a283ebb-f6d8-49c0-a73e-323979ff56a2
caps.latest.revision: 26
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: f8fcc3e835e2a8cb6613dc78e67383f534f97f7c
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47474256"
---
# <a name="how-to-upgrade-visual-c-projects-to-visual-studio-2015"></a>Como: atualizar projetos do Visual C++ para o Visual Studio 2015
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Para obter a documentação mais recente do Visual Studio 2017, consulte [guia de atualização e portabilidade do Visual C++](https://docs.microsoft.com/en-us/cpp/porting/visual-cpp-porting-and-upgrading-guide).

Quando você abre primeiro um projeto do Visual C++ que foi criado em uma versão anterior do Visual Studio, poderá ser solicitado que você atualize o projeto. A mensagem pergunta se você deseja atualizar para a versão mais recente do compilador e das bibliotecas do Visual C++. As opções de atualização dependem da versão do [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] que foi usada para criar o projeto.  
  
 Você pode usar o [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)] para abrir, editar, e compilar os projetos do [!INCLUDE[win8](../includes/win8-md.md)] que foram criados no [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)], mas para criar um novo projeto do [!INCLUDE[win8](../includes/win8-md.md)], você deve usar o [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)]. (Para criar um projeto [!INCLUDE[win81](../includes/win81-md.md)], você deve usar [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)].)  
  
 Para criar um projeto do Windows 10, você deve usar [!INCLUDE[vs_dev14](../includes/vs-dev14-md.md)].  
  
 Se a atualização do projeto não for solicitada, talvez não seja necessário que você faça algo para atualizá-lo.  
  
-   Se o projeto (.vcproj) foi criado em uma versão de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] mais antiga do que [!INCLUDE[vs2010](../includes/vs2010-md.md)], você deve atualizar o projeto.  
  
-   Se o projeto (. vcxproj) foi criado no [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)], [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)], ou [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)] tem duas opções:  
  
    -   Você pode pular a atualização. [!INCLUDE[vs_dev14](../includes/vs-dev14-md.md)] carregará o projeto sem fazer quaisquer alterações se ele tem acesso a ferramentas do Visual C++ no [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] com SP1, [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)], ou [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)]. Você pode fornecer esse acesso instalando a versão do Visual Studio que o projeto foi criado com o no mesmo computador que tenha [!INCLUDE[vs_dev14](../includes/vs-dev14-md.md)]. Para obter mais informações, consulte [instalando versões do Visual Studio lado a lado](../install/install-visual-studio-versions-side-by-side.md).  
  
    -   Você pode atualizar o projeto permitindo que o [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] faça as alterações que são descritas posteriormente neste tópico. Se você tiver mais de um projeto do Visual C++ em sua solução, deverá atualizar todos eles.  
  
        > [!NOTE]
        >  Se você recusar a atualização quando solicitado pela primeira vez, você pode atualizar o projeto mais tarde, escolhendo **Atualizar projeto VC + +** sobre o **projeto** menu. Se o comando não aparecer, a atualização não será necessária.  
  
## <a name="upgrading-a-visual-c-project"></a>Atualizando um projeto do Visual C++  
 Se você permitir que [!INCLUDE[vs_dev14](../includes/vs-dev14-md.md)] atualize automaticamente o projeto, estas alterações serão feitas:  
  
-   Altera o projeto para que ele usa o [!INCLUDE[vs_dev14](../includes/vs-dev14-md.md)] compilador e bibliotecas (PlatformToolset = VisualStudio v140).  
  
-   Para [!INCLUDE[cppcli](../includes/cppcli-md.md)] projetos, muda a TargetFrameworkVersion para .NET Framework 4.5.2.  
  
## <a name="continuing-to-work-with-a-custom-platformtoolset"></a>Continuação do trabalho com um PlatformToolset personalizado  
 Se você desejar continuar a trabalhar com um Conjunto de Ferramentas de Plataforma no [!INCLUDE[vs_dev14](../includes/vs-dev14-md.md)], o conjunto de ferramentas deverá ser colocado em %ProgramFiles%\MSBuild\Microsoft.Cpp\v4.0\Platforms\Win32\PlatformToolsets\ em uma máquina x86, ou em %ProgramFiles (x86)%\MSBuild\Microsoft.Cpp\v4.0\Platforms\Win32\PlatformToolsets\ em uma máquina x64. Para obter informações sobre como criar um PlatformToolset personalizado, consulte [C++ multiplataforma nativa](http://go.microsoft.com/fwlink/?LinkId=248587) no blog da equipe do Visual C++.  
  
## <a name="see-also"></a>Consulte também  
 [Guia de atualização e portabilidade do Visual C++](http://msdn.microsoft.com/library/f5fbcc3d-aa72-41a6-ad9a-a706af2166fb)   
 [Portabilidade, migração e atualização de projetos do Visual Studio](../porting/porting-migrating-and-upgrading-visual-studio-projects.md)

