---
title: Como usar um feed personalizado do NuGet em um ambiente conectado | Microsoft Docs
author: johnsta
ms.author: johnsta
ms.date: 03/27/2018
ms.topic: article
description: Use um feed personalizado do NuGet para acessar e usar pacotes do NuGet em um ambiente conectado.
keywords: Docker, Kubernetes, Azure, AKS, Serviço de Contêiner do Azure, contêineres
manager: ghogen
ms.openlocfilehash: 94956e061302281ef232205081346c0aa90eab90
ms.sourcegitcommit: efd8c8e0a9ba515d47efcc7bd370eaaf4771b5bb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/03/2018
---
#  <a name="use-a-custom-nuget-feed-in-a-connected-environment"></a>Usar um feed personalizado do NuGet em um ambiente conectado

Um feed do NuGet fornece uma maneira conveniente de incluir fontes de pacote em um projeto. Será necessário que o Connected Environment consiga acessar este feed para que as dependências sejam instaladas corretamente no contêiner do Docker.

Para configurar um feed do NuGet:
1. Adicione uma [referência de pacote](https://docs.microsoft.com/en-us/nuget/consume-packages/package-references-in-project-files) no arquivo `*.csproj` do nó `PackageReference`.

   ```xml
   <ItemGroup>
       <!-- ... -->
       <PackageReference Include="Contoso.Utility.UsefulStuff" Version="3.6.0" />
       <!-- ... -->
   </ItemGroup>
   ```

2. Crie um arquivo [NuGet.Config](https://docs.microsoft.com/en-us/nuget/reference/nuget-config-file) na pasta do projeto.
     * Use a seção `packageSources` para fazer referência à localização do feed do NuGet. Importante: o feed do NuGet deve ser publicamente acessível.
     * Use a seção `packageSourceCredentials` para configurar as credenciais de nome de usuário e senha. 

   ```xml
   <packageSources>
       <add key="Contoso" value="https://contoso.com/packages/" />
   </packageSources>

   <packageSourceCredentials>
       <Contoso>
           <add key="Username" value="user@contoso.com" />
           <add key="ClearTextPassword" value="33f!!lloppa" />
       </Contoso>
   </packageSourceCredentials>
   ```

3. Se você estiver usando o controle do código-fonte:
    - Faça referência a `NuGet.Config` no arquivo `.gitignore` para que você não confirme acidentalmente as credenciais do repositório de origem.
    - Abra o arquivo `vsce.yaml` em seu projeto, encontre a seção `build` e insira o trecho a seguir para garantir que o arquivo `NuGet.Config` seja sincronizado com o Azure e usado durante o processo de criação de imagem de contêiner. Por padrão, o Connected Environment não sincroniza arquivos que correspondem às regras `.gitignore` e `.dockerignore`.

        ```yaml
        build:
        useGitIgnore: true
        ignore:
        - “!NuGet.Config”
        ```


## <a name="next-steps"></a>Próximas etapas

Depois de concluir as etapas acima, na próxima vez que executar `vsce up` (ou pressionar `F5` no VSCode ou no Visual Studio), o Connected Environment sincronizará o arquivo `NuGet.Config` com o Azure, que será, então, usado por `dotnet restore` para instalar as dependências do pacote no contêiner.

