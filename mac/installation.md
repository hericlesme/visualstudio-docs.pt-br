---
title: Instalar o Visual Studio para Mac | Microsoft Docs
description: "Instruções sobre como instalar o Visual Studio para Mac e os componentes adicionais necessários para o desenvolvimento de plataforma cruzada."
author: asb3993
ms.author: amburns
ms.date: 04/14/2017
ms.topic: article
ms.technology: vs-ide-install
ms.assetid: 22B1F2CD-32AE-464D-80AC-C8AB4786B015
ms.openlocfilehash: 7f91a28449ffad135058438ec767095818cc8527
ms.sourcegitcommit: ebe9fb5eda724936f7a059d35d987c29dffdb50d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/07/2017
---
# <a name="setup-and-install-visual-studio-for-mac"></a>Configurar e instalar o Visual Studio para Mac

## <a name="setup"></a>Configuração

Para começar a desenvolver aplicativos de plataforma cruzada nativos após baixar o Visual Studio para Mac, é necessário preparar-se instalando e configurando alguns itens.

Para trabalhar com iOS no Visual Studio você precisará do seguinte:

* Um Mac com macOS Sierra 10.12 ou superior
* Xcode 8.3 ou posterior. A versão estável mais recente geralmente é recomendada.
* Uma ID da Apple. Se você ainda não tiver uma ID da Apple, crie uma nova em https://appleid.apple.com. Será necessário ter uma ID da Apple para instalar e entrar no Xcode.

## <a name="install"></a>Instalar o

1. Baixar o Visual Studio para Mac de [https://www.visualstudio.com/](https://www.visualstudio.com/)

2. Depois que o pacote do instalador for baixado, clique no arquivo **VisualStudioInstaller.dmg** para montar o instalador e executá-lo clicando duas vezes no logotipo, conforme ilustrado na imagem a seguir:

  ![Caixa de diálogo do instalador](media/installer-image1.png)

3. Você poderá ver uma caixa de diálogo de alerta semelhante à imagem a seguir. Nesse caso, clique em **Abrir**:

  ![caixa de diálogo de alerta](media/installer-image2.png)

4. O instalador inspeciona seu sistema para verificar quais componentes precisam ser instalados ou atualizados:

  ![Avaliando o seu sistema](media/installer-image3.png)

5. Em seguida, você verá uma caixa de diálogo de alerta solicitando que você confirme os termos de Privacidade e de Licença. Pressione o botão **Continuar** para confirmar os termos:

  ![Caixa de diálogo Licença](media/installer-image4.png)

6. O instalador apresenta uma lista de componentes necessários que estão faltando e que precisa ser baixados e instalados. Selecione os produtos que você deseja baixar aqui:

  ![Selecionar itens](media/installer-image5.png)

  Esta tela de instalação exibe a versão e o tamanho de cada componente individual. Você pode clicar em cada componente para exibir uma lista de dependências desse componente (para Android), consultar pacotes adicionais que ele baixa (para .NET Core) ou exibir os aplicativos adicionais necessários (iOS e macOS):

  ![Dependências adicionais de Android](media/installer-image6.png)

7. Quando você estiver satisfeito com sua seleção, pressione o botão **Instalar e Atualizar** para iniciar o processo de instalação.

8. O instalador iniciará o processo de download e instalação dos itens selecionados:

  ![Iniciando a instalação](media/installer-image7.png)

  ![Baixando o Xamarin.Mac](media/installer-image8.png)

  ![Concluindo a instalação](media/installer-image9.png)

9. Pode ser solicitado que você eleve as permissões necessárias para os componentes individuais que são necessários para concluir a instalação. Insira suas credenciais de administrador para continuar o processo de instalação:

  ![Insira as permissões para prosseguir com o instalador](media/installer-image10.png)

10. Depois que a instalação for bem-sucedida, você poderá começar a desenvolver aplicativos no Visual Studio pressionando **Iniciar**:

  ![Abrir o Visual Studio](media/installer-image11.png)

> [!NOTE]
Se você optou por não instalar uma plataforma ou ferramenta durante a instalação original (desmarcando-a na etapa 6), deverá executar o [instalador](https://www.visualstudio.com/vs/) novamente se desejar adicionar os componentes mais tarde.

## <a name="manual-installation"></a>Instalação manual

Se a instalação falhar ou qualquer componente individual de sua instalação falhar, você poderá resolver o problema por meio de uma instalação manual. Para exibir os componentes necessários e baixar cada uma deles, execute as seguintes etapas:

1. Na segunda tela do Instalador do Visual Studio, vá para a barra de menus e selecione **Exibir Instruções de Instalação Manual**:

    ![Opção mostrando o item de menu de instalação manual](media/installer-image12.png)

2. Siga as instruções para baixar e instalar os componentes manualmente:

  ![Caixa de diálogo de instalação manual](media/installer-image13.png)

## <a name="install-visual-studio-for-mac-behind-a-firewall-or-proxy-server"></a>Instalar o Visual Studio para Mac por trás de um firewall ou servidor proxy

Para instalar o Visual Studio para Mac por trás de um firewall, determinados pontos de extremidade devem estar acessíveis para permitir o download das ferramentas necessárias e as atualizações do software.

Configure a rede para permitir o acesso aos seguintes locais:

* [Pontos de extremidade do Visual Studio](https://docs.microsoft.com/visualstudio/install/install-visual-studio-behind-a-firewall-or-proxy-server)