---
title: Criar um ambiente de desenvolvimento do .NET Core com contêineres usando o Kubernetes na nuvem com o Visual Studio – Etapa 3 – Criar um ambiente de desenvolvimento do Kubernetes | Microsoft Docs
author: johnsta
ms.author: johnsta
ms.date: 02/20/2018
ms.topic: get-started-article
ms.technology: vsce-kubernetes
description: Desenvolvimento rápido no Kubernetes com contêineres e microsserviços no Azure
keywords: Docker, Kubernetes, Azure, AKS, Serviço de Contêiner do Azure, contêineres
manager: ghogen
ms.openlocfilehash: 01451ca57cbd4bac5c6bf08d040905b9463b15a3
ms.sourcegitcommit: 900ed1e299cd5bba56249cef8f5cf3981b10cb1c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/19/2018
---
# <a name="get-started-on-connected-environment-with-net-core-and-visual-studio"></a>Introdução ao Connected Environment com .NET Core e Visual Studio

Etapa anterior: [Criar aplicativos Web ASP.NET](get-started-netcore-visualstudio-02.md)

## <a name="create-a-dev-environment-in-azure"></a>Criar um ambiente de desenvolvimento no Azure
Com o Connected Environment, você pode criar ambientes de desenvolvimento baseados no Kubernetes totalmente gerenciados pelo Azure e otimizados para desenvolvimento. Com o projeto que acabamos de criar aberto, selecione **Connected Environment para AKS** na lista suspensa de configurações de inicialização, conforme é mostrado abaixo.

![](images/LaunchSettings.png)

Na caixa de diálogo que é exibida, verifique se você está conectado com a conta apropriada e, em seguida, selecione um ambiente de desenvolvimento existente ou selecione **<Criar Novo Connected Environment para AKS...>** para criar um novo.

![](images/ConnectedEnvDialog.png)

Você pode usar os valores padrão fornecidos ou ajustá-los como desejar. Clique em **OK** quando os valores estiverem definidos corretamente.

![](images/NewEnvDialog.png)

De volta na caixa de diálogo anterior, deixe a lista suspensa **Espaço** como `mainline` por enquanto. Falaremos sobre isso mais tarde com mais detalhes. Marque a caixa de seleção **Acessível Publicamente** para que o aplicativo Web fique acessível por meio de um ponto de extremidade público. Isso não é obrigatório, mas será útil para demonstrar alguns conceitos mais adiante neste passo a passo. Mas não se preocupe, em ambos os casos, você poderá depurar o site usando o Visual Studio.

![](images/ConnectedEnvDialog2.png)

Clique em **OK** para selecionar ou criar o ambiente de desenvolvimento. Uma tarefa em segundo plano será iniciada para executar essa ação, que levará alguns minutos para ser concluída. Você pode ver se ele ainda está sendo criado passando o cursor sobre o ícone **Tarefas em segundo plano** no canto inferior esquerdo da barra de status (veja abaixo).

![](images/BackgroundTasks.png)

> [!Note]
Até que o ambiente de desenvolvimento seja criado com êxito, você não pode depurar o aplicativo.

## <a name="look-at-the-files-added-to-project"></a>Examinar os arquivos adicionados ao projeto
Enquanto esperamos até que o ambiente de desenvolvimento seja criado, vamos examinar os arquivos que foram adicionados ao projeto quando você escolheu usar um ambiente de desenvolvimento.

Primeiro, você pode ver que uma pasta chamada `charts` foi adicionada e dentro dela um [gráfico do Helm](https://docs.helm.sh) para o aplicativo foi usado como scaffold. Esses arquivos são usados para implantar o aplicativo no ambiente de desenvolvimento.

Você verá que um arquivo chamado `Dockerfile` foi adicionado. Este arquivo tem as informações necessárias para empacotar o aplicativo no formato padrão do Docker. Um arquivo `HeaderPropagation.cs` também é criado. Vamos discutir esse arquivo mais tarde no passo a passo. 

Por fim, você verá um arquivo chamado `vsce.yaml` que contém as informações de configuração necessárias para o ambiente de desenvolvimento, por exemplo, se o aplicativo deve ser acessível por meio de um ponto de extremidade público.

![](images/ProjectFiles.png)

> [!div class="nextstepaction"]
> [Depurar um contêiner no Kubernetes](get-started-netcore-visualstudio-04.md)