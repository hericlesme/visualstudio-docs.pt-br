---
title: Passo a passo do Mobile Client do Azure para as Ferramentas do Visual Studio para Unity | Microsoft Docs
ms.custom: 
ms.date: 10/19/2017
ms.reviewer: crdun
ms.suite: 
ms.technology: tgt-pltfrm-cross-plat
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5A8762A1-D843-4FD8-A89B-E5E489ECA03D
author: dantogno
ms.author: v-davian
manager: crdun
ms.openlocfilehash: 294942641aa0739d105a888f4fbfe6ba9cf05a16
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/09/2017
---
# <a name="implement-the-azure-mobileserviceclient"></a>Implementar o MobileServiceClient do Azure

O <a href="https://msdn.microsoft.com/en-us/library/azure/microsoft.windowsazure.mobileservices.mobileserviceclient(v=azure.10).aspx">MobileServiceClient</a> é fundamental para o SDK do Azure Mobile Client, pois dá acesso ao back-end do aplicativo móvel.

## <a name="locate-the-url-of-the-mobile-app-backend"></a>Localizar a URL do back-end do aplicativo móvel

O construtor `MobileServiceClient` usa a URL de aplicativo móvel como parâmetro, então, antes de seguir em frente, localize a URL.

1. No Portal do Azure, clique no botão **Serviços de Aplicativos**.

    ![Clique em Serviços de Aplicativos](media/vstu_azure-implement-azure-mobileserviceclient-image1.png)

2. Clique na entrada do seu aplicativo móvel.

    ![Clique em Aplicativo Móvel](media/vstu_azure-implement-azure-mobileserviceclient-image2.png)

3. Localizar a URL do back-end do aplicativo móvel.

    ![Copiar URL](media/vstu_azure-implement-azure-mobileserviceclient-image3.png)

## <a name="create-the-mobileserviceclient-singleton"></a>Criar o singleton do MobileServiceClient

Deve haver apenas uma única instância de `MobileServiceClient`, portanto, o passo a passo usa uma variação do padrão do singleton.

1. Dentro do diretório **Ativos/Scripts** do projeto do Unity, crie um novo script de C# nomeado **AzureMobileServiceClient**.

2. Abra o script `AzureMobileServiceClient` e exclua todos os códigos do modelo, incluindo os com uso de instruções e a declaração de classe.

3. Adicione o seguinte código:

  ```csharp
  using Microsoft.WindowsAzure.MobileServices;

  public static class AzureMobileServiceClient
  {
      private const bool ignoreTls = true;
      private const string backendUrl = "MOBILE_APP_URL";
      private static MobileServiceClient client;

      public static MobileServiceClient Client
      {
          get
          {
              if (client == null)
              {
                  client = new MobileServiceClient(backendUrl);
              }

              return client;
          }
      }
  }
  ```

  > [!NOTE]
  > Se o IntelliSense não reconhecer o namespace Microsoft.WindowsAzure, verifique se você concluiu todas as etapas na seção [Preparar o ambiente de desenvolvimento]().

4. No código acima, substitua `MOBILE_APP_URL` com a URL do back-end do aplicativo móvel.

## <a name="next-step"></a>Próximas etapas

* [Atualizar o repositório de segurança do Unity Mono](visual-studio-tools-for-unity-azure-security.md)
