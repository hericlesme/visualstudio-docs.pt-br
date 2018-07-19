---
title: Remover o Visual Studio 2017 | Microsoft Docs
description: Saiba como remover completamente o Visual Studio de seu computador, passo a passo.
ms.custom: ''
ms.date: 09/12/2017
ms.technology: vs-acquisition
ms.prod: visual-studio-dev15
ms.topic: conceptual
f1_keywords:
- uninstall
- uninstall Visual Studio
- remove
- remove Visual Studio
- cleanup
- cleanup Visual Studio
- clean up
- clean up Visual Studio
ms.assetid: 9c81a777-9c95-4934-b517-c60c6dc78799
author: heaths
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: db775eb56a8328e3688e20ce07ce7d045c97c3c7
ms.sourcegitcommit: 4667e6ad223642bc4ac525f57281482c9894daf4
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/20/2018
ms.locfileid: "36280013"
---
# <a name="remove-visual-studio"></a>Remover o Visual Studio

Se você encontrar um erro fatal e não puder reparar ou desinstalar o Visual Studio, será possível executar a ferramenta `InstallCleanup.exe` para remover os arquivos de instalação e informações do produto. Essa ferramenta deverá ser executada como um último recurso se a reparação ou a desinstalação falhararem. Ela pode desinstalar recursos de outras instalações do Visual Studio ou outros produtos que precisam ser reparados.

Nas instruções a seguir, você pode executar a ferramenta com diferentes opções de linha de comando com o seguinte comportamento:

| Alternar | Comportamento |
| ------ | -------- |
| `-i`   | Esta será a opção padrão se nenhuma outra opção for passada. Ela remove apenas o diretório de instalação principal e as informações do produto. Esse comportamento é preferível se você pretende reinstalar a mesma versão depois de executar a ferramenta `InstallCleanup.exe`. |
| `-f`   | Especificar essa opção remove o diretório de instalação principal, as informações do produto e a maioria dos outros recursos instalados fora do diretório de instalação que podem ser compartilhados com outras instalações do Visual Studio ou outros produtos. Esse comportamento é preferível se você pretende remover o Visual Studio sem instalá-lo novamente mais tarde. |

1. Fechar o instalador do Visual Studio.
2. Abrir um prompt de comando de administrador. Para abrir um prompt de comando de administrador, siga estas etapas:
   * Clique no menu **Iniciar**
   * Digite **cmd**.
   * Clique com o botão direito em **Prompt de Comando**e em **Executar como administrador**.
3. Digite o caminho completo do utilitário `InstallCleanup.exe` e passe qualquer opção de linha de comando desejada. Por padrão, o caminho do utilitário é o seguinte:
   ```
   C:\Program Files (x86)\Microsoft Visual Studio\Installer\resources\app\layout\InstallCleanup.exe
   ```

Se não encontrar o `InstallCleanup.exe` no diretório do Instalador do Visual Studio (sempre localizado em `%ProgramFiles(x86)%\Microsoft Visual Studio`), siga as instruções de [instalação do Visual Studio](install-visual-studio.md) e quando a tela de seleção de carga de trabalho for exibida, feche a janela e siga as etapas anteriores novamente.

## <a name="get-support"></a>Obter suporte

Às vezes, as coisas podem dar errado. Caso a instalação do Visual Studio falhe, confira a página [Solução de problemas de instalação e atualização do Visual Studio 2017](troubleshooting-installation-issues.md). Se nenhuma das etapas de solução de problemas ajudar, entre em contato conosco por meio de um chat ao vivo para obter ajuda com a instalação (somente em inglês). Para saber mais detalhes, confira a [página de suporte do Visual Studio](https://visualstudio.microsoft.com/vs/support/#talktous).

Aqui estão algumas outras opções de suporte:

* Você pode nos relatar problemas do produto por meio da ferramenta [Relatar um Problema](../ide/how-to-report-a-problem-with-visual-studio-2017.md), exibida no Instalador do Visual Studio e no IDE do Visual Studio.
* Você pode compartilhar uma sugestão de produto conosco no [UserVoice](https://visualstudio.uservoice.com/forums/121579).
* Você pode acompanhar os problemas do produto e encontrar respostas na [Visual Studio Developer Community](https://developercommunity.visualstudio.com/) (Comunidade de desenvolvedores do Visual Studio).
* Também é possível interagir conosco e com outros desenvolvedores do Visual Studio por meio das [conversas sobre o Visual Studio na comunidade do Gitter](https://gitter.im/Microsoft/VisualStudio). (Esta opção requer uma conta do [GitHub](https://github.com/).)

## <a name="see-also"></a>Consulte também

* [Instalar o Visual Studio 2017](install-visual-studio.md)
* [Atualizar o Visual Studio 2017](update-visual-studio.md)
* [Modificar o Visual Studio 2017](modify-visual-studio.md)
* [Desinstalar o Visual Studio 2017](uninstall-visual-studio.md)
