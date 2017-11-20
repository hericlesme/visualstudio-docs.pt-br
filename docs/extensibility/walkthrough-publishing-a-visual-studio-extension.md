---
title: "Passo a passo: Publicando uma extensão do Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- publishing web controls
- web controls, publishing
ms.assetid: a7816161-0490-4043-86f5-0f7331ed83b3
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d8eac89a2bdde3b0a20ea3a98775de84a503f86c
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/09/2017
---
# <a name="walkthrough-publishing-a-visual-studio-extension"></a>Passo a passo: Publicando uma extensão do Visual Studio

Este passo a passo mostra como publicar uma extensão do Visual Studio para o Visual Studio Marketplace. Quando você adicionar a extensão Marketplace, os desenvolvedores podem usar **extensões e atualizações** existe procurar extensões novas e atualizadas.

## <a name="prerequisites"></a>Pré-requisitos

 Para acompanhar este passo a passo, você deve instalar o SDK do Visual Studio. Para obter mais informações, consulte [instalar o SDK do Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-visual-studio-extension"></a>Criar uma extensão do Visual Studio

Nesse caso, usaremos uma extensão de VSPackage padrão, mas as mesmas etapas são válidas para cada tipo de extensão.

1. Crie um VSPackage no c# chamado "TestPublish" que tem um comando de menu. Para obter mais informações, consulte [criando sua primeira extensão: Hello World](../extensibility/extensibility-hello-world.md).

## <a name="package-your-extension"></a>A extensão do pacote

1. Atualize a extensão vsixmanifest com as informações corretas sobre o nome do produto, autor e versão.

  ![Atualizar vsixmanifest de extensão](media/update-extension-vsixmanifest.png)

2. A extensão de compilação **versão** modo. Agora a sua extensão será ser empacotada como um VSIX na pasta \bin\Release..

3. Você pode clicar duas vezes o VSIX para verificar a instalação.

## <a name="test-the-extension"></a>A extensão de teste

 Antes de distribuir a extensão, compilação e teste para verificar se que ele está instalado corretamente na instância experimental do Visual Studio.

1. No Visual Studio, inicie a depuração. Para abrir uma instância experimental do Visual Studio.

2. Na instância experimental, vá para o **ferramentas** menu e clique em **extensões e atualizações...** . A extensão TestPublish deve aparecer no painel central e ser habilitada.

3. Sobre o **ferramentas** menu, verifique se o comando de teste.

## <a name="publish-the-extension-to-the-visual-studio-marketplace"></a>Publicar a extensão para o Visual Studio Marketplace

1. Certifique-se de que você criou a versão de lançamento de sua extensão e que está atualizado.

2. Em um navegador da web, abra o [Visual Studio Marketplace](https://marketplace.visualstudio.com/vs) site.

3. No canto superior direito, clique em **entrar**.

4. Use sua conta da Microsoft para entrar. Se você não tiver uma conta da Microsoft, você pode criar um neste momento.

5. Clique em **publicar extensões**.  Isso fará com que você navegue para a página de gerenciamento para todas as suas extensões.  Se você não tiver uma conta do publicador, você precisará criar um neste momento.

  ![Carregar no Marketplace](media/upload-to-marketplace.png)

6. Escolha o editor que você deseja usar para carregar a extensão.  Você pode alterar os editores clicando no nome do publicador no canto superior esquerdo.

  ![Editor de alteração de Marketplace](media/change-marketplace-publisher.png)

7. Em **1: carregar a extensão**, você pode optar por carregar um arquivo VSIX diretamente no Visual Studio Marketplace ou simplesmente adiciona um link para seu próprio site. Nesse caso, estamos carregará nossa extensão, TestPublish.vsix.  Arraste e solte a sua extensão ou use o **clique** link para navegar até o arquivo.  A extensão pode ser encontrada na pasta \bin\Release. do projeto.  Clique em **Continue**.

8. Em **2: fornecer detalhes da extensão**, alguns campos são preenchidos automaticamente no arquivo source.extension.vsixmanifest da sua extensão.  Para obter mais detalhes sobre cada um podem ser encontrados abaixo:

    * **Nome interno** será usado na URL da página de detalhes da extensão. Por exemplo, uma extensão sob o nome do publicador "myname" de publicação e especificando o nome interno para ser "myextension" resultará em uma URL de "marketplace.visualstudio\.com/items?itemName=myname.myextension" para a sua extensão. página de detalhes.
    
    * **Nome de exibição** de sua extensão.  Isso é preenchido automaticamente do arquivo source.extension.vsixmanifest.
   
    * **Versão** número da extensão que você está carregando.  Isso é preenchido automaticamente do arquivo source.extension.vsixmanifest.
    
    * **ID do VSIX** é o identificador exclusivo que o Visual Studio usa para a sua extensão.  Isso é necessário se você gostaria de ter a extensão a ser atualizado automaticamente.  Isso é preenchido automaticamente do arquivo source.extension.vsixmanifest.
    
    * **Logotipo** que será usado para a sua extensão.  Ele será preenchido automaticamente o arquivo source.extension.vsixmanifest se fornecido.
    
    * **Descrição breve** do que faz a sua extensão.  Ele será preenchido automaticamente o arquivo source.extension.vsixmanifest.
    
    * **Visão geral** é um bom lugar para incluir capturas de tela e informações detalhadas sobre o que faz a sua extensão.
    
    * **Suporte para versões do Visual Studio** permite que você escolha quais versões do Visual Studio funcione em sua extensão.  A extensão será instalada apenas para essas versões.
    
    * **Edições do Visual Studio** permite que você escolha quais edições do Visual Studio funcionem em sua extensão.  A extensão será instalada apenas para essas edições.
    
    * **Tipo**.  O tipo mais comum de extensões são **ferramentas**.
    
    * **Categorias**.  Selecione até três são o melhor ajuste para a sua extensão.
    
    * **Marcas** são palavras-chave que ajudam os usuários a localizar a extensão. Marcas podem ajudar a aumentar a relevância da pesquisa de suas extensões no Marketplace.
    
    * **Categoria de preços** é o custo de sua extensão.
    
    * **Repositório de código fonte** permite que você compartilhe um link para seu código-fonte com a comunidade.
    
    * **Permitir que o p e r para a sua extensão** permitirá que os usuários deixem perguntas em sua página de entrada de extensão.

9. Clique em **salvar e carregar**. Isso o levará página Gerenciar de volta para o publicador.  A extensão ainda não foram publicada.  Para publicar seu foco extensão sobre a entrada de sua extensão e clique em **...**  e **tornar público**.  Você pode exibir a sua extensão de aparência semelhante no Marketplace selecionando **exibir detalhes**.  Para obter números de aquisição, clique em **relatórios**.  Para fazer alterações em sua extensão, clique em **editar*.

  ![Menu de entrada de extensão](media/extension-entry-menu.png)

10. Depois de clicar em **tornar público**, sua extensão agora é pública.  Pesquise o Visual Studio Marketplace para a sua extensão.

## <a name="install-the-extension-from-the-visual-studio-marketplace"></a>Instalar a extensão do Visual Studio Marketplace

Agora que a extensão é publicada, instale-o no Visual Studio e testá-lo lá.

1. No Visual Studio, no **ferramentas** menu, clique em **extensões e atualizações...** .

2. Clique em **Online** e, em seguida, procure TestPublish.

3. Clique em **Baixar**. A extensão, em seguida, será agendada para instalação.

4. Para concluir a instalação, feche todas as instâncias do Visual Studio.

## <a name="removing-the-extension"></a>Removendo a extensão

Você pode remover a extensão do Visual Studio Marketplace e do computador.

### <a name="to-remove-the-extension-from-the-visual-studio-marketplace"></a>Para remover a extensão do Visual Studio Marketplace

1. Abra o [Visual Studio Marketplace](https://marketplace.visualstudio.com/vs) site.

2. No canto superior direito, clique em **publicar** extensões.  Selecione o editor que é usado para publicar TestPublish.  A listagem de TestPublish é exibida.

3. Passe o mouse sobre a entrada de extensão e clique em **...**  e **remover...** Você será solicitado a confirmar se deseja remover a extensão.  Clique em **OK**.

### <a name="to-remove-the-extension-from-your-computer"></a>Para remover a extensão do computador

1. No Visual Studio, no **ferramentas** menu, clique em **extensão e atualizações...** .

2. Selecione TestPublish e, em seguida, clique em **desinstalação**. A extensão, em seguida, será agendada para desinstalação.

3. Para concluir a desinstalação, feche todas as instâncias do Visual Studio.
