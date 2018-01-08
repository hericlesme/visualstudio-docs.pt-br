---
title: "Implantar uma extensão de modelo de camada | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- dependency diagrams, deploying extensions
- layer models, deploying extensions
ms.assetid: 00a4675b-d20e-487e-8fd5-be2b1e0ba238
caps.latest.revision: "27"
author: alexhomer1
ms.author: ahomer
manager: douge
ms.workload: multiple
ms.openlocfilehash: 0569b5cced2100e1ed3b746464b001d929a209be
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="deploy-a-layer-model-extension"></a>Implantar uma extensão de modelo de camada
Outros usuários do Visual Studio podem instalar camada modelagem extensões que você cria usando o Visual Studio.  
  
## <a name="installing-your-extension"></a>Instalar a extensão  
 A extensão é compilada em um arquivo VSIX, que pode ser instalado em outros computadores. Você também pode instalá-lo no computador de desenvolvimento, para disponibilizar a extensão na instância principal do Visual Studio.  
  
#### <a name="to-install-the-extension"></a>Para instalar a extensão  
  
1.  No projeto que contém **source.vsix.manifest**, abra **bin\\ \***  no Explorador de arquivos.  
  
2.  Copie o  **\*.vsix** arquivo para o computador no qual você deseja instalar a extensão.  
  
3.  No computador de destino, clique duas vezes o arquivo *.vsix no Windows Explorer.  
  
     O instalador do VSIX é aberto.  
  
#### <a name="to-uninstall-the-extension"></a>Para desinstalar a extensão  
  
1.  No Visual Studio, no **ferramentas** menu, clique em **extensões e atualizações**.  
  
2.  Clique no nome da extensão e, em seguida, clique em **desinstalação**.  
  
## <a name="installing-an-extension-on-a-team-foundation-build-server"></a>Instalando uma extensão em um servidor de compilação do Team Foundation  
 [!INCLUDE[esprbuild](../misc/includes/esprbuild_md.md)]servidores normalmente não tenha instalado o Visual Studio, e portanto não é possível instalar o VSIX clicando duas vezes nele. A instalação do [!INCLUDE[esprbuild](../misc/includes/esprbuild_md.md)] inclui alguns componentes que permitem que uma extensão do VSIX ser executado, mas você deve instalar a extensão manualmente.  
  
#### <a name="to-install-your-layer-extension-on-a-includeesprbuildmiscincludesesprbuildmdmd-server"></a>Para instalar a extensão de camada em um [!INCLUDE[esprbuild](../misc/includes/esprbuild_md.md)] Server  
  
1.  Copie o **.vsix** arquivos do seu computador de desenvolvimento para o [!INCLUDE[esprbuild](../misc/includes/esprbuild_md.md)] computador.  
  
     Coloque o arquivo VSIX em um dos seguintes locais:  
  
    -   Para instalar todos os usuários e serviços:  
  
         %ProgramFiles%\Microsoft visual Studio [version] \Common7\IDE\Extensions\Microsoft  
  
    -   Para instalar somente para o serviço de rede que executa [!INCLUDE[esprbuild](../misc/includes/esprbuild_md.md)]:  
  
         %WinDir%\ServiceProfiles\NetworkService\AppData\Local\Microsoft\VisualStudio\\\Extensions\Microsoft [versão]  
  
    -   Se você tiver configurado [!INCLUDE[esprbuild](../misc/includes/esprbuild_md.md)] para executar no modo interativo, como um usuário específico, você pode instalar apenas para o usuário:  
  
         %LocalAppData%\Microsoft\VisualStudio\\\Extensions\Microsoft [versão]  
  
        > [!NOTE]
        >  % LocalAppData % normalmente é *DriveName*: usuários*UserName*AppDataLocal.  
  
2.  Expanda cada arquivo VSIX para uma pasta no mesmo local:  
  
    1.  Alterar a extensão de nome de arquivo de **.vsix** para **. zip**.  
  
    2.  Extraia o conteúdo do arquivo. zip para uma pasta.  
  
    3.  Exclua o arquivo. zip  
  
3.  Reinicie o [!INCLUDE[esprbuild](../misc/includes/esprbuild_md.md)].
