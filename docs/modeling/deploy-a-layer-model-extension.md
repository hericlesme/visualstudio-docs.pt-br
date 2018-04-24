---
title: Implantar uma extensão de modelo de camada
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- dependency diagrams, deploying extensions
- layer models, deploying extensions
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: d44e5deaa9e631255d0a4f36d7b5f175b7d14611
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/20/2018
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
 [!INCLUDE[esprbuild](../misc/includes/esprbuild_md.md)] servidores normalmente não tenha instalado o Visual Studio, e portanto não é possível instalar o VSIX clicando duas vezes nele. A instalação do [!INCLUDE[esprbuild](../misc/includes/esprbuild_md.md)] inclui alguns componentes que permitem que uma extensão do VSIX ser executado, mas você deve instalar a extensão manualmente.

#### <a name="to-install-your-layer-extension-on-a-includeesprbuildmiscincludesesprbuildmdmd-server"></a>Para instalar a extensão de camada em um [!INCLUDE[esprbuild](../misc/includes/esprbuild_md.md)] Server

1.  Copie o **.vsix** arquivos do seu computador de desenvolvimento para o [!INCLUDE[esprbuild](../misc/includes/esprbuild_md.md)] computador.

     Coloque o arquivo VSIX em um dos seguintes locais:

    -   Para instalar todos os usuários e serviços:

         %ProgramFiles%\Microsoft visual Studio [version] \Common7\IDE\Extensions\Microsoft

    -   Para instalar somente para o serviço de rede que executa [!INCLUDE[esprbuild](../misc/includes/esprbuild_md.md)]:

         %WinDir%\ServiceProfiles\NetworkService\AppData\Local\Microsoft\VisualStudio\\[version]\Extensions\Microsoft

    -   Se você tiver configurado [!INCLUDE[esprbuild](../misc/includes/esprbuild_md.md)] para executar no modo interativo, como um usuário específico, você pode instalar apenas para o usuário:

         %LocalAppData%\Microsoft\VisualStudio\\\Extensions\Microsoft [versão]

        > [!NOTE]
        >  % LocalAppData % normalmente é *DriveName*: usuários*UserName*AppDataLocal.

2.  Expanda cada arquivo VSIX para uma pasta no mesmo local:

    1.  Alterar a extensão de nome de arquivo de **.vsix** para **. zip**.

    2.  Extraia o conteúdo do arquivo. zip para uma pasta.

    3.  Exclua o arquivo. zip

3.  Reinicie o [!INCLUDE[esprbuild](../misc/includes/esprbuild_md.md)].
