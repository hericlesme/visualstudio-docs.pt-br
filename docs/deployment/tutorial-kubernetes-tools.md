---
title: Tutorial do Kubernetes ferramentas | Microsoft Docs
ms.custom: ''
ms.date: 06/08/2018
ms.technology: vs-ide-deployment
ms.topic: conceptual
author: ghogen
ms.author: ghogen
manager: douge
ms.workload:
- azure
ms.openlocfilehash: b354045ceb464a14ff909a503aa62477c73b983c
ms.sourcegitcommit: 4667e6ad223642bc4ac525f57281482c9894daf4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/20/2018
ms.locfileid: "36280871"
---
# <a name="get-started-with-visual-studio-kubernetes-tools"></a>Introdução às ferramentas de Kubernetes do Visual Studio

Ferramentas do Visual Studio Kubernetes ajudar a simplificar o desenvolvimento de aplicativos em contêineres Kubernetes de direcionamento. Visual Studio pode criar automaticamente os arquivos de configuração como código necessários para dar suporte à implantação de Kubernetes, como Dockerfiles e gráficos Helm. Além disso, você pode publicar diretamente a um cluster do serviço de Kubernetes do Azure (AKS) do Visual Studio.

## <a name="prerequisites"></a>Pré-requisitos

Para aproveitar essa nova funcionalidade, você precisará de:

- A visualização mais recente do [Visual Studio 2017](https://visualstudio.microsoft.com/vs/preview) com a carga de trabalho de desenvolvimento do Azure.

- O [Kubernetes tools para Visual Studio](https://aka.ms/get-vsk8stools), disponível como um download separado.

- [Docker para Windows](https://store.docker.com/editions/community/docker-ce-desktop-windows) instalado em sua estação de trabalho de desenvolvimento (ou seja, em que você executar o Visual Studio)

- Se você quiser publicar no AKS do Visual Studio:

    1.  O [AKS ferramentas de publicação](https://aka.ms/get-vsk8spublish), disponível como um download separado.

    1.  Um cluster do serviço Kubernetes do Azure. Para obter mais informações, consulte [criando um cluster do AKS](/azure/aks/kubernetes-walkthrough-portal#create-aks-cluster). Não se esqueça [conectar-se ao cluster](/azure/aks/kubernetes-walkthrough#connect-to-the-cluster) em sua estação de trabalho de desenvolvimento.

    1.  Helm CLI instalada em sua estação de trabalho de desenvolvimento. Para obter mais informações, consulte [instalação do Helm](https://github.com/kubernetes/helm/blob/master/docs/install.md).

    1.  Helm configurado no cluster do AKS. Para obter mais informações sobre como fazer isso, consulte [como configurar o Helm](/azure/aks/kubernetes-helm#configure-helm).

## <a name="create-a-new-kubernetes-project"></a>Criar um novo projeto de Kubernetes

Depois de instalar as ferramentas apropriadas, inicie o Visual Studio e crie um novo projeto. Sob **Cloud**, escolha o **aplicativo de contêiner para Kubernetes** tipo de projeto. Selecione este tipo de projeto e escolha **Okey**.

![Captura de tela de criar um novo projeto de aplicativo do Kubernetes](media/k8s-tools-new-k8s-app.png)

Em seguida, você pode escolher qual tipo de ASP.NET Core aplicativo web para criar. Escolher **aplicativo Web** e escolha **Okey**. O usual **Habilitar suporte ao Docker** opção não aparecerá nessa caixa de diálogo.  Suporte ao docker está habilitado por padrão para um aplicativo de contêiner para Kubernetes.

![Captura de tela da seleção do aplicativo web](media/k8s-tools-web-app-selection-screen.png)

## <a name="add-kubernetes-support-to-an-existing-project"></a>Adicionar suporte a Kubernetes a um projeto existente

Como alternativa, você pode adicionar suporte a Kubernetes a um projeto de aplicativo web ASP.NET Core existente. Para fazer isso, clique com botão direito no projeto e escolha **Add** > **suporte de orquestrador de contêiner**.

![Item de menu de captura de tela de orquestrador de contêiner adicionar](media/k8s-tools-add-container-orchestrator.png)

Na caixa de diálogo, selecione "Kubernetes Helm" e escolha **Okey**.

![Caixa de diálogo de captura de tela de orquestrador de contêiner adicionar](media/k8s-tools-add-container-orchestrator-dialog-box.PNG)

## <a name="what-visual-studio-creates-for-you"></a>O que o Visual Studio cria para você

Depois de criar um novo **aplicativo de contêiner para Kubernetes** projeto ou adicionar suporte de orquestrador de contêiner do Kubernetes a um projeto existente, você ver alguns arquivos adicionais em seu projeto que facilitam a implantação de Kubernetes.

![Captura de tela do Gerenciador de soluções após a adição de suporte de orquestrador de contêiner](media/k8s-tools-solution-explorer.png)

Os arquivos adicionados são:

- um Dockerfile, que permite que você gere um Docker este aplicativo web de hospedagem da imagem de contêiner. Como você verá, as ferramentas do Visual Studio utiliza esse Dockerfile ao depurar e implantar no Kubernetes. Se você preferir trabalhar diretamente com a imagem do Docker, você pode clique duas vezes em que o Dockerfile e escolha **compilar a imagem do Docker**.

   ![Opção de captura de tela da imagem do Docker Build](media/k8s-tools-build-docker-image.png)

- um gráfico do Helm e um *gráficos* pasta. Esses arquivos yaml compõem o gráfico do Helm para o aplicativo, que pode ser usada para implantá-lo no Kubernetes. Para obter mais informações sobre o Helm, consulte [ https://www.helm.sh ](https://www.helm.sh).

- *azds.YAML*. Isso contém configurações para espaços de desenvolvimento do Azure, um novo serviço que fornece uma experiência de depuração rápida e interativa no serviço Kubernetes do Azure. Esse arquivo está sendo utilizado, mas é reservado para uso futuro por espaços de desenvolvimento do Azure.

## <a name="publish-to-azure-kubernetes-service-aks"></a>Publicar no serviço de Kubernetes do Azure (AKS)

Com todos esses arquivos em vigor, você pode usar o IDE do Visual Studio para escrever e depurar o código do aplicativo, assim como você sempre tenha.

Uma vez que o código em execução da maneira desejada, você pode publicar diretamente do Visual Studio em um cluster do AKS.

Para fazer isso, primeiro você precisa configurar um perfil de publicação que publica sua imagem de contêiner ao registro de contêiner do Azure (ACR). Em seguida, AKS pode efetuar pull de sua imagem de contêiner do ACR e implantá-lo no cluster.

1. Na **Gerenciador de soluções**, clique com botão direito no seu *project* e escolha **publicar**.

   ![Captura de tela de publicar o item de menu](media/k8s-tools-publish-project.png)

1. No **Publish** tela, escolha **registro de contêiner** como a publicação de destino e siga os prompts para selecionar o registro de contêiner. Se você ainda não tiver um registro de contêiner, escolha **criar novo registro de contêiner do Azure** criá-lo do Visual Studio. Para obter mais informações, consulte [publicar seu contêiner no registro de contêiner do Azure](#publish-your-container-to-azure-container-registry).

   ![Captura de tela da escolha de uma tela de destino de publicação](media/k8s-tools-publish-to-acr.png)

1. No Gerenciador de soluções, clique com botão direito no seu *solução* e clique em **publicar no Azure AKS**.

   ![Captura de tela de publicar o item de menu do AKS do Azure](media/k8s-tools-publish-solution.png)

1. Escolha sua assinatura e o cluster do AKS, juntamente com o ACR publicar perfil que você acabou de criar. Clique em **OK**.

   ![Captura de tela de publicar a tela AKS](media/k8s-tools-publish-to-aks.png)

   Isso leva você para o **publicar no Azure AKS** tela.

1.  Escolha o **Helm configurar** link para atualizar a linha de comando usada para instalar os gráficos do Helm no servidor.

   ![Link de captura de tela de configurar o Helm](media/k8s-tools-configure-helm.png)

   Atualização da linha de comando é útil se houver argumentos de linha de comando personalizada que você deseja especificar como um nome diferente de contexto ou um gráfico de Kubernetes.

   ![Tela de configurar a captura de tela do Helm](media/k8s-tools-helm-configure-screen.png)

1. Quando estiver pronto para implantar, clique o **publicar** botão para publicar seu aplicativo no AKS.

   ![Captura de tela de publicar a tela de AKS do Azure](media/k8s-tools-publish-screen.png)

Parabéns! Agora você pode usar todo o poder do Visual Studio para todo o desenvolvimento de aplicativos Kubernetes.

## <a name="next-steps"></a>Próximas etapas

Saiba mais sobre o desenvolvimento do Kubernetes no Azure lendo o [documentação do AKS](/azure/aks).