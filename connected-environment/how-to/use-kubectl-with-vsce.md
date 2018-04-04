---
title: Como usar o kubectl com um Connected Environment | Microsoft Docs
author: johnsta
ms.author: johnsta
ms.date: 03/12/2018
ms.topic: article
ms.technology: vsce-kubernetes
description: Desenvolvimento rápido no Kubernetes com contêineres e microsserviços no Azure
keywords: Docker, Kubernetes, Azure, AKS, Serviço de Contêiner do Azure, contêineres
manager: ghogen
ms.openlocfilehash: 46c69f80e58a4265aa5e4320e731c3ad241a8116
ms.sourcegitcommit: e01ccb5ca4504a327d54f33589911f5d8be9c35c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2018
---
# <a name="use-kubectl-with-a-connected-environment"></a>Usar o `kubectl` com um Connected Environment

Você pode acessar o cluster do Kubernetes em um Connected Environment e usar as ferramentas existentes do Kubernetes, como o `kubectl`.

Executar `vsce env create` ou `vsce env select` adicionará automaticamente um contexto de configuração do `kubectl`, portanto, o kubectl já deverá estar conectado ao seu cluster do Kubernetes do VSCE. Exemplos:
- Confirmar o contexto atual: `kubectl config current-context`
- Listar todos os contextos disponíveis: `kubectl config get-contexts`. Um cluster do Kubernetes criado pelo VSCE será nomeado de forma semelhante a "vsce-<guid>".
- Mudar de contexto: `kubectl config use-context <context-name>`
- Exibir o painel do Kubernetes: execute `kubectl proxy` e, em seguida, abra o navegador no endereço que esse comando emite (acrescente `/ui` à URL para navegar até o painel do Kubernetes).
- Listar os serviços em execução no espaço do VSCE padrão chamado *mainline*: `kubectl get services --namespace=mainline`

