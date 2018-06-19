---
title: Introdução ao Azure Functions
description: Usando o Azure Functions no Visual Studio para Mac.
author: asb3993
ms.author: amburns
ms.date: 05/06/2018
ms.topic: article
ms.technology: vs-ide-install
ms.assetid: 25CD47A4-5B32-4734-8EF3-E24A02AABF29
ms.openlocfilehash: 5d787efbd09ad7f2d4a1f5f72b8f1493d8c6c587
ms.sourcegitcommit: 33c954fbc8e05f7ba54bfa2c0d1bc1f9bbc68876
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33870407"
---
# <a name="introduction-to-azure-functions"></a>Introdução ao Azure Functions

O Azure Functions é uma maneira de criar e executar trechos de código controlados por eventos – funções – na nuvem sem a necessidade de gerenciar ou provisionar explicitamente a infraestrutura. Para obter mais informações sobre o Azure Functions, consulte a [Documentação do Azure Functions](https://docs.microsoft.com/azure/azure-functions/).

## <a name="requirements"></a>Requisitos

As ferramentas do Azure Functions estão incluídas no **Visual Studio para Mac 7.5**.

Para criar e implantar funções, você também precisará de uma assinatura do Azure, que está disponível gratuitamente em [https://azure.com/free](https://azure.com/free).

## <a name="creating-your-first-azure-functions-project"></a>Criando seu primeiro projeto do Azure Functions

1. No Visual Studio para Mac, selecione **Arquivo > Nova Solução…** 
2. Na caixa de diálogo Novo Projeto, selecione o modelo do Azure Functions em **Nuvem > Geral** e clique em **Próximo**:

    ![Caixa de diálogo Novo Projeto mostrando a opção do Azure Functions](media/azure-functions-image1.png)

3. Insira um **Nome do Projeto** e selecione **Criar**.

O Visual Studio para Mac cria um projeto .NET Standard com uma função HttpTrigger padrão incluída. Ela também inclui referências de NuGet a uma variedade de pacotes do **AzureWebJobs**, bem como ao pacote **Newtonsoft.Json**.

![Editor do Visual Studio para Mac exibindo uma nova função do Azure do modelo](media/azure-functions-newproj.png)

O novo projeto contém os seguintes arquivos:

* **HttpTrigger.cs** – Esta classe contém código de texto clichê para uma função disparada por HTTP. Ela contém um atributo **FunctionName** com o nome da função e um atributo de gatilho, **HttpTrigger**, que especifica que a função é disparada por uma solicitação HTTP. Para obter mais informações sobre o método de função, consulte o artigo [Referência do desenvolvedor de C# do Azure Functions](https://docs.microsoft.com/azure/azure-functions/functions-dotnet-class-library).
* **host.json** – Este arquivo descreve as opções de configuração global para o host de funções. Para ver um arquivo de exemplo e obter informações sobre as configurações disponíveis para esse arquivo, consulte a [Referência de host.json para o Azure Functions](https://docs.microsoft.com/azure/azure-functions/functions-host-json).
* **local.settings.json** – Este arquivo contém todas as configurações para executar funções localmente. Essas configurações são usadas pelas Ferramentas Básicas do Azure Functions. Para obter mais informações, consulte [Arquivo de configurações local](https://docs.microsoft.com/en-us/azure/azure-functions/functions-run-local#local-settings-file) no artigo sobre as Ferramentas Básicas do Azure Functions.

Agora que criou um novo projeto do Azure Functions no Visual Studio para Mac, você pode testar a função disparada por HTTP padrão do computador local.

<!--
## Create an Azure storage account

[Describe why this step is necessary and what it does]

1. Log on to your account at [https://portal.azure.com](https://portal.azure.com).
2. Under the **Favorites** section, located on the left of the screen, select **Storage Accounts**:
    ![]()
3. Select **Add** to create a new storage account:
    ![]()
4. Enter a globally unique name for the **Name** and reuse it for the **Resource group**. You can keep all the other items as their default.
    ![]()
5. Click **Create**. It might take a few minutes to create the storage account. You'll get a notification once it has been successfully created.
6. Select the **Go to resource** button from the notification:
    ![]()
-->

## <a name="testing-the-function-locally"></a>Testando a função localmente

Com o suporte para Azure Functions no Visual Studio para Mac, você pode testar e depurar sua função no computador de desenvolvimento local.

1. Para testar a função localmente, pressione o botão **Executar** no Visual Studio para Mac:

    ![Botão Iniciar depuração no Visual Studio para Mac](media/azure-functions-run.png)

1. Executar o projeto inicia a depuração local na função do Azure e abre uma nova janela do Terminal, conforme ilustrado na imagem a seguir: 

    ![Janela do Terminal mostrando a saída da função](media/azure-functions-terminal.png) 

    Copie a URL da saída.

3. Cole a URL da solicitação HTTP na barra de endereços do navegador. Adicione a cadeia de caracteres de consulta `?name=<yourname>` ao final da URL e execute a solicitação. A imagem a seguir mostra a resposta no navegador para a solicitação GET local retornada pela função:

    ![Solicitação HTTP no navegador](media/azure-functions-httpreq.png)

## <a name="creating-a-new-function"></a>Criando uma nova função

Modelos de função permitem que você crie rapidamente novas funções usando os gatilhos e modelos mais comuns. Quando um novo projeto do Azure Functions é criado, ele inclui automaticamente uma função HttpTrigger. Para criar outro tipo de função, faça o seguinte:

1. Remova o arquivo **HttpTrigger.cs** clicando nele com o botão direito do mouse e selecionando **Remover**. No alerta a seguir, selecione **Excluir** para removê-lo de seu projeto:

    ![Caixa de diálogo para remover o arquivo do projeto](media/azure-functions-remove.png)

2. Para adicionar uma nova função, clique com o botão direito do mouse no nome do projeto e selecione **Adicionar > Adicionar Função...**:

    ![Ação de contexto para adicionar nova função](media/azure-functions-addnew.png)

3. Na caixa de diálogo **Nova Função do Azure**, selecione a função de que precisa:

    ![Caixa de diálogo Nova Função do Azure](media/azure-functions-newfunction.png)

    Uma lista dos modelos de função do Azure é fornecida na seção a seguir.

## <a name="available-function-templates"></a>Modelos de função disponíveis

- **HTTP** – Dispare a execução de seu código usando uma solicitação HTTP. Há modelos explícitos para os gatilhos HTTP a seguir:
    - Http GET CRUD
    - Http POST CRUD
    - Gatilho Http com parâmetros
    - Gatilho Http
- **Temporizador** – Execute a limpeza ou outras tarefas em lote seguindo um cronograma predefinido. Esse modelo tem dois campos: um nome e um cronograma, que é uma expressão CRON de seis campos. Para obter mais informações, consulte o [Artigo do Azure Functions sobre o Temporizador](https://docs.microsoft.com/azure/azure-functions/functions-create-scheduled-function)
- **Gatilho do GitHub** – Responda a eventos que ocorrerem em seus repositórios do GitHub. Para obter mais informações, consulte o [Artigo do Azure Functions sobre o GitHub](https://docs.microsoft.com/azure/azure-functions/functions-create-github-webhook-triggered-function)
    - Autor de comentários do GitHub – Esta função será executada quando receber um webhook do GitHub para uma solicitação de pull ou emissão e adicionará um comentário.
    - WebHook do GitHub – Esta função será executada sempre que receber um webhook do GitHub
- **Gatilho de blob** – Processe blobs do Armazenamento do Azure quando eles forem adicionados a um contêiner. Além do nome da função, esse modelo também tem uma propriedade de conexão e de caminho. A propriedade de caminho é o caminho em sua conta de armazenamento que o gatilho monitorará. A conta de conexão é o nome da configuração do aplicativo que contém a cadeia de conexão da sua conta de armazenamento. Para obter mais informações, consulte o [Artigo do Azure Functions sobre o Armazenamento de Blobs](https://docs.microsoft.com/azure/azure-functions/functions-create-storage-blob-triggered-function).
- **Gatilho de fila** – Esta é uma função que responderá às mensagens conforme elas chegarem na fila do Armazenamento do Azure. Além do nome da função, esse modelo tem um **Caminho** (o nome da fila da qual a mensagem será lida) e uma **Conexão** da conta de armazenamento (o nome da configuração de aplicativo que contém a cadeia de conexão da conta de armazenamento). Para obter mais informações, consulte o [Artigo do Azure Functions sobre o Armazenamento de Filas](https://docs.microsoft.com/azure/azure-functions/functions-create-storage-queue-triggered-function).
- **WebHook genérico** – É uma função simples que será executada sempre que receber uma solicitação de qualquer serviço que dá suporte a webhooks. Para obter mais informações, consulte o [Artigo do Azure Functions sobre webhooks genéricos](https://docs.microsoft.com/azure/azure-functions/functions-create-generic-webhook-triggered-function)
- **Redimensionador de imagem** – Esta função cria imagens redimensionadas sempre que um blob é adicionado a um contêiner. O modelo usa a cadeia de conexão e o caminho para o gatilho, uma saída de imagem pequena e uma saída de imagem média.
- **Token SAS** – Esta função gera um token SAS para um determinado contêiner do Armazenamento do Azure e um nome de blob. Além do nome da função, esse modelo também tem uma propriedade de conexão e de caminho. A propriedade de caminho é o caminho em sua conta de armazenamento que o gatilho monitorará. A conta de conexão é o nome da configuração do aplicativo que contém a cadeia de conexão da sua conta de armazenamento. Os **Direitos de acesso** também precisam ser definidos. O nível de autorização controla se a função requer uma chave de API e qual chave deve ser usada; Função usa uma tecla de função; Admin usa a chave mestra. Para obter mais informações, consulte o exemplo de [Função do Azure em C# para gerar tokens SAS](https://azure.microsoft.com/resources/samples/functions-dotnet-sas-token/).
- **Orquestração de Funções Duráveis** – Funções Duráveis permitem que você escreva funções com estado em um ambiente sem servidor. A extensão gerencia o estado, os pontos de verificação e as reinicializações para você. Para obter mais informações, consulte os guias do Azure Functions sobre as [Funções Duráveis](https://docs.microsoft.com/azure/azure-functions/durable-functions-overview)