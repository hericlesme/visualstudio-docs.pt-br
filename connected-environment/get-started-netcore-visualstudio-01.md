---
title: Criar um ambiente de desenvolvimento .NET Core com contêineres usando o Kubernetes na nuvem com o Visual Studio – Etapa 1 – Instalar as ferramentas | Microsoft Docs
author: johnsta
ms.author: johnsta
ms.date: 04/05/2018
ms.topic: get-started-article
ms.technology: vsce-kubernetes
description: Desenvolvimento rápido no Kubernetes com contêineres e microsserviços no Azure
keywords: Docker, Kubernetes, Azure, AKS, Serviço de Contêiner do Azure, contêineres
manager: ghogen
ms.openlocfilehash: 64aa0b322c777baa78da5bf86cb1220a47128d93
ms.sourcegitcommit: 3724338a5da5a6d75ba00452b0a607388b93ed0c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2018
---
# <a name="get-started-on-connected-environment-with-net-core-and-visual-studio"></a>Introdução ao Connected Environment com .NET Core e Visual Studio

Neste guia, você aprenderá como:

1. Criar um ambiente baseado no Kubernetes no Azure, otimizado para desenvolvimento.
1. Desenvolva o código de forma iterativa em contêineres usando o Visual Studio.
1. Desenvolver de forma independente dois serviços separados e usar a descoberta de serviço DNS do Kubernetes para fazer uma chamada para outro serviço.
1. Desenvolver e testar o código de forma produtiva em um ambiente de equipe.

[!INCLUDE[](includes/see-troubleshooting.md)]

## <a name="install-the-connected-environment-cli"></a>Instalar a CLI do Connected Environment
O Connected Environment requer uma configuração mínima do computador local. A maior parte da configuração do ambiente de desenvolvimento é armazenada na nuvem e pode ser compartilhada com outros usuários.

1. Baixe e execute o [Instalador da CLI do Connected Environment](https://aka.ms/get-vsce-windows). 

## <a name="get-kubernetes-debugging-tools"></a>Obter as ferramentas de depuração do Kubernetes
Embora seja possível usar a CLI do Connected Environment como uma ferramenta autônoma, os recursos avançados, como a **depuração do Kubernetes**, estão disponíveis para desenvolvedores .NET Core que usam o **VS Code** ou o **Visual Studio**.

### <a name="visual-studio-debugging"></a>Depuração do Visual Studio 
1. Instale a versão mais recente do [Visual Studio 2017](https://www.visualstudio.com/vs/)
1. No instalador do Visual Studio, verifique se a seguinte carga de trabalho está selecionada:
    * Desenvolvimento do ASP.NET e para a Web
1. Instalar a [extensão do Visual Studio para Connected Environment](https://aka.ms/get-vsce-visualstudio)

Agora estamos prontos para criar um aplicativo Web ASP.NET com o Visual Studio.

> [!div class="nextstepaction"]
> [Criar um aplicativo Web ASP.NET](get-started-netcore-visualstudio-02.md)
