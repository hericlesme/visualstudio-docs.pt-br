---
title: Criar um ambiente de desenvolvimento .NET Core com contêineres usando o Kubernetes na nuvem – Etapa 6 – Saiba mais sobre o desenvolvimento em equipe | Microsoft Docs
author: ghogen
ms.author: ghogen
ms.date: 02/20/2018
ms.topic: tutorial
ms.prod: visual-studio-dev15
ms.technology: vs-azure
description: Desenvolvimento rápido no Kubernetes com contêineres e microsserviços no Azure
keywords: Docker, Kubernetes, Azure, AKS, Serviço de Contêiner do Azure, contêineres
manager: douge
ms.openlocfilehash: 4da5051b760a12f8fd8837072ada44c8c5a9b239
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31884337"
---
# <a name="get-started-on-connected-environment-with-net-core"></a>Introdução ao Connected Environment com .NET Core

Etapa anterior: [Chamar outro contêiner](get-started-netcore-05.md)

[!INCLUDE[](includes/team-development-1.md)]

Vamos ver isso em ação:
1. Acesse a janela do VS Code da `mywebapi` e faça uma edição no código do método `string Get(int id)`, por exemplo:

```csharp
[HttpGet("{id}")]
public string Get(int id)
{
    return "mywebapi now says something new";
}
```

[!INCLUDE[](includes/team-development-2.md)]

> [!div class="nextstepaction"]
> [Avançar](get-started-netcore-07.md)
