---
title: Como usar o kubectl com um Connected Environment | Microsoft Docs
author: ghogen
ms.author: ghogen
ms.date: 03/12/2018
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-azure
description: Desenvolvimento rápido no Kubernetes com contêineres e microsserviços no Azure
keywords: Docker, Kubernetes, Azure, AKS, Serviço de Contêiner do Azure, contêineres
manager: douge
ms.openlocfilehash: 138dce09e0d53dc47703b9c6f56a7efda4adc255
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="use-kubectl-with-a-connected-environment"></a>Usar o `kubectl` com um Connected Environment

Você pode acessar o cluster do Kubernetes em um Connected Environment e usar as ferramentas existentes do Kubernetes, como o `kubectl`.

Executar `vsce env create` ou `vsce env select` adicionará automaticamente um contexto de configuração do `kubectl`, portanto, o kubectl já deverá estar conectado ao seu cluster do Kubernetes do VSCE. Exemplos:
- Confirmar o contexto atual: `kubectl config current-context`
- Listar todos os contextos disponíveis: `kubectl config get-contexts`. Um cluster do Kubernetes criado pelo VSCE será nomeado de forma semelhante a "vsce-<guid>".
- Mudar de contexto: `kubectl config use-context <context-name>`
- Exibir o painel do Kubernetes: execute `kubectl proxy` e, em seguida, abra o navegador no endereço que esse comando emite (acrescente `/ui` à URL para navegar até o painel do Kubernetes).
- Listar os serviços em execução no espaço do VSCE padrão chamado *mainline*: `kubectl get services --namespace=mainline`

