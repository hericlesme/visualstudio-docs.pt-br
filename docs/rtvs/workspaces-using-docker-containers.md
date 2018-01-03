---
title: "Ferramentas do R para Visual Studio e Contêineres do Docker | Microsoft Docs"
ms.custom: 
ms.date: 12/04/2017
ms.reviewer: 
ms.suite: 
ms.technology: devlang-r
ms.devlang: r
ms.tgt_pltfrm: 
ms.topic: article
caps.latest.revision: "1"
author:
- kraigb
- karthiknadig
ms.author:
- kraigb
- karthiknadig
manager: ghogen
ms.workload: data-science
ms.openlocfilehash: 45bfebe905b9cae502247fbd0b46d9b856fb2fea
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="using-docker-containers-with-r-tools-for-visual-studio"></a>Usando contêineres do Docker com as Ferramentas do R para Visual Studio

As RTVS (Ferramentas do R para Visual Studio) versão 1.3+, juntamente com uma instalação do [Docker para Windows](https://www.docker.com/docker-windows), dão suporte ao trabalho com os contêineres do Docker.

- [Criando um contêiner](#creating-a-container)
- [Conectando-se a um contêiner](#connecting-to-a-container)
- [Usando imagens personalizadas](#using-custom-built-images)

## <a name="creating-a-container"></a>Criar um contêiner

1. Selecione o botão **Contêineres...** no canto superior direito da janela **Espaços de trabalho** (**Ferramentas do R > Windows > Espaços de trabalho**). A janela informará se você não tiver instalado o Docker para Windows e fornecerá um link para o download. A instalação do Docker pode exigir uma reinicialização do computador.

    ![Janela Espaços de trabalho nas Ferramentas do R para Visual Studio (VS2017) com o comando Contêineres](media/container-workspaces-window.png)

1. Na janela **Contêineres**, selecione **Criar**:

    ![Criar comando na janela Contêineres](media/containers-window-create.png)

1. Preencha as informações obrigatórias na caixa de diálogo e selecione **Criar**. As credenciais inseridas também são usadas para criar uma conta no Linux, com a qual você entrará mais tarde.

    ![Inserindo um nome e credenciais de contêiner ao criar um contêiner](media/containers-window-create-fill.png)

1. Talvez demore um pouco para as RTVS montarem a imagem. A janela **Saída** no Visual Studio mostra o andamento, mas talvez pareça que ela não esteja fazendo muita coisa durante os downloads demorados de imagem; seja paciente. Depois que a imagem for montada, as RTVS iniciam o contêiner e ele é exibido na janela **Contêiner**. Os controles à direita interrompem, removem ou reiniciam o contêiner.

    ![Janela Contêineres mostrando um contêiner concluído](media/containers-window-created.png)

## <a name="connecting-to-a-container"></a>Conectando-se a um contêiner

1. A seção **Contêineres Locais em Execução** da janela **Espaços de trabalho** exibe os contêineres que estão executando o daemon das RTVS na porta 5444. (Consulte [Remote R Server for Linux](workspaces-remote-r-service-for-linux.md) (R Server Remoto para Linux) para obter detalhes sobre como o daemon está configurado.)

    ![Janela Espaços de trabalho mostrando contêineres disponíveis](media/workspaces-window-running-containers.png)

1. Para conectar-se a um contêiner, clique duas vezes no nome do contêiner ou selecione o botão de seta para frente à sua direita. Quando conectado, você verá uma janela **R Interativo** (consulte [Working with the R Interactive window](interactive-repl.md) (Trabalhando com a janela do R Interativo)):

    ![Janelas Espaços de trabalho e janela REPL aberta para um contêiner](media/workspaces-window-container-connected.png)

## <a name="using-custom-built-images"></a>Usando imagens personalizadas

As RTVS detectam e permitem o gerenciamento de contêineres criados usando imagens personalizadas, como a imagem microsoft/rtvs descrita no arquivo do docker abaixo. A imagem base usada aqui tem rtvs-daemon, R 3.4.2 e os pacotes R comuns pré-instalados. **Observação**: altere o nome de usuário e a senha mostrados aqui, conforme necessário.

```docker
FROM microsoft/rtvs:1.3-ub1604-r3.4.2
RUN useradd --create-home ruser1
RUN echo "ruser1:foobar" | chpasswd

#Install additional R packages. You may have to install OS dependencies, see package info or error messages during build.
#RUN Rscript --vanilla -e "install.packages(c('AzureML','wordcloud'), repos = 'http://cran.us.r-project.org');"
```

Use o seguinte comando para montar a imagem, alterando o nome do contêiner (o argumento `--name`) conforme desejado:

```bash
docker build -t my-rtvs-image:latest .
docker run -p 6056:5444 --name my-rtvs-container my-rtvs-image:latest rtvsd
```

O argumento `-p 6056:5444` mapeia a porta 6056 para a porta 5444 interna, que as RTVS usam para detectar o rtvs-daemon. Qualquer contêiner que expõe a porta de contêiner 5444 está listado na janela **Espaços de trabalho**. É possível usar a janela **Espaços de trabalho** para se conectar a um contêiner usando `<<unix>>\ruser1` como o nome de usuário e "foobar" como a senha, a menos que você tenha especificado credenciais diferentes no arquivo do docker.
