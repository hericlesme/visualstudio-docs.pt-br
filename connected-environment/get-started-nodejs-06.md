---
title: Criar um ambiente de desenvolvimento Node.js com contêineres usando o Kubernetes na nuvem – Etapa 6 – Saiba mais sobre o desenvolvimento em equipe | Microsoft Docs
author: johnsta
ms.author: johnsta
ms.date: 02/20/2018
ms.topic: get-started-article
ms.technology: vsce-kubernetes
description: Desenvolvimento rápido no Kubernetes com contêineres e microsserviços no Azure
keywords: Docker, Kubernetes, Azure, AKS, Serviço de Contêiner do Azure, contêineres
manager: ghogen
ms.openlocfilehash: 4db1d71c96da29a06884e562a277a7ca427910d4
ms.sourcegitcommit: 900ed1e299cd5bba56249cef8f5cf3981b10cb1c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/19/2018
---
# <a name="get-started-on-connected-environment-with-nodejs"></a>Introdução ao Connected Environment com Node.js

Etapa anterior: [Chamar um serviço em execução em um contêiner separado](get-started-nodejs-05.md)

[!INCLUDE[](includes/team-development-1.md)]

Vamos ver isso em ação:
1. Acesse a janela do VS Code da `mywebapi` e faça uma edição no código do manipulador de GET `/` padrão, por exemplo:

```javascript
app.get('/', function (req, res) {
    res.send('mywebapi now says something new');
});
```

[!INCLUDE[](includes/team-development-2.md)]

> [!div class="nextstepaction"]
> [Avançar](get-started-nodejs-07.md)

