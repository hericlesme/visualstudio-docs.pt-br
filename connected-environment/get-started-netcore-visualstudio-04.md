---
title: Criar um ambiente de desenvolvimento .NET Core com contêineres usando o Kubernetes na nuvem com o Visual Studio – Etapa 4 – Depurar um contêiner no Kubernetes | Microsoft Docs
author: johnsta
ms.author: johnsta
ms.date: 02/20/2018
ms.topic: get-started-article
ms.technology: vsce-kubernetes
description: Desenvolvimento rápido no Kubernetes com contêineres e microsserviços no Azure
keywords: Docker, Kubernetes, Azure, AKS, Serviço de Contêiner do Azure, contêineres
manager: ghogen
ms.openlocfilehash: 9b3aa6b0f710707800ea9a1f0533b0c37681ea05
ms.sourcegitcommit: 900ed1e299cd5bba56249cef8f5cf3981b10cb1c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/19/2018
---
# <a name="get-started-on-connected-environment-with-net-core-and-visual-studio"></a>Introdução ao Connected Environment com .NET Core e Visual Studio

Etapa anterior: [Criar um ambiente de desenvolvimento no Azure](get-started-netcore-visualstudio-03.md)

## <a name="debug-a-container-in-kubernetes"></a>Depurar um contêiner no Kubernetes
Depois que o ambiente de desenvolvimento for criado com êxito, você poderá depurar o aplicativo. Defina um ponto de interrupção no código, por exemplo, na linha 20 no arquivo `HomeController.cs` na qual a variável `Message` é definida. Pressione **F5** para iniciar a depuração. 

O Visual Studio se comunicará com o ambiente de desenvolvimento para criar e implantar o aplicativo e, em seguida, abrirá um navegador com o aplicativo Web em execução. Pode parecer que o contêiner está sendo executado localmente, mas, na verdade, ele está sendo executado no nosso ambiente de desenvolvimento no Azure. O motivo para o endereço do localhost é que o Connected Environment cria um túnel SSH temporário para o contêiner em execução no Azure.

Clique no link "**Sobre**" na parte superior da página para disparar o ponto de interrupção. Você tem acesso completo às informações de depuração exatamente como teria se o código tivesse sido executado localmente, como a pilha de chamadas, as variáveis locais, as informações de exceção, etc.

> [!div class="nextstepaction"]
> [Chamar outro contêiner](get-started-netcore-visualstudio-05.md)