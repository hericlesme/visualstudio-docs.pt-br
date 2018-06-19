---
ms.topic: include
ms.openlocfilehash: b10d15b90f7f413d26adf8037c6f52c711a9ed69
ms.sourcegitcommit: 928885ace538bef5b25961358d4f166d648f196a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/27/2018
ms.locfileid: "32030928"
---
## <a name="build-and-run-code-in-kubernetes"></a>Compilar e executar o código no Kubernetes
Vamos executar nosso código! Na janela do terminal, execute este comando da **pasta raiz do código**, o webfrontend:

```cmd
vsce up
```

Fique atento à saída do comando, você verá várias coisas a medida que ele progride:
1. O código-fonte é sincronizado com o ambiente de desenvolvimento no Azure.
1. Uma imagem de contêiner é criada no Azure, conforme a especificação dos ativos do Docker na pasta do código.
1. São criados objetos do Kubernetes que utilizam a imagem de contêiner conforme a especificação do gráfico do Helm na pasta do código.
1. São exibidas informações sobre os pontos de extremidade do contêiner. No nosso caso, estamos esperando uma URL HTTPS pública.
1. Considerando que as etapas acima tenham sido concluídas com êxito, você começará a ver a saída `stdout` (e `stderr`) à medida em que o contêiner for inicializado.

> [!Note]
> Essas etapas demorarão mais na primeira vez em que o comando `up` for executado, mas as próximas execuções serão mais rápidas.

## <a name="test-the-web-app"></a>Testar o aplicativo Web
Examine a saída do console para obter informações sobre a URL pública que foi criada com o comando `up`. Ela estará no formato: 

`Running at public URL: https://<servicename>-<environmentname>.vsce.io` 

Abra essa URL em uma janela do navegador e o aplicativo Web deverá ser carregado. À medida em que o contêiner é executado, as saídas `stdout` e `stderr` são transmitidas para a janela do terminal.
