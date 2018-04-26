---
title: Criar um ambiente de desenvolvimento Node.js com contêineres usando o Kubernetes na nuvem – Etapa 6 – Saiba mais sobre o desenvolvimento em equipe | Microsoft Docs
author: ghogen
ms.author: ghogen
ms.date: 02/20/2018
ms.topic: tutorial
ms.prod: visual-studio-dev15
ms.technology: vs-azure
description: Desenvolvimento rápido no Kubernetes com contêineres e microsserviços no Azure
keywords: Docker, Kubernetes, Azure, AKS, Serviço de Contêiner do Azure, contêineres
manager: douge
ms.openlocfilehash: 6a17dfc3eeebccf1508ea3f69aecb53d067de7af
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
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

