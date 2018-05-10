---
title: Ferramentas de dados do Visual Studio para .NET
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c3175080-1dfb-4ab8-a460-92dadbb844b4
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
- dotnet
ms.openlocfilehash: 2b7fc572541e0c2f0f5aa04c6e676d1e2913ff9f
ms.sourcegitcommit: 33c954fbc8e05f7ba54bfa2c0d1bc1f9bbc68876
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2018
---
# <a name="visual-studio-data-tools-for-net"></a>Ferramentas de dados do Visual Studio para .NET

O Visual Studio e o .NET Framework juntas fornecem amplo API e as ferramentas de suporte para se conectar aos bancos de dados, modelagem de dados na memória e exibir os dados na interface do usuário. As classes do .NET Framework que fornecem a funcionalidade de acesso a dados são conhecidas como [ADO.NET](/dotnet/framework/data/adonet/index). ADO.NET, juntamente com os dados de ferramentas no Visual Studio, foi projetado principalmente para dar suporte a bancos de dados relacionais e XML. Atualmente, muitos fornecedores de banco de dados NoSQL, ou de terceiros, oferecem provedores ADO.NET.

[.NET core](/dotnet/core/) suporta ADO.NET, exceto para conjuntos de dados e tipos relacionados. Se você tiver como alvo o núcleo do .NET e exige uma camada de mapeamento relacional de objeto (ORM), use [Entity Framework Core](/ef/core/).

O diagrama a seguir mostra uma exibição simplificada de arquitetura básica:

![Arquitetura do ADO.NET](../data-tools/media/raddata-ado-net-architecture-diagram.png)

## <a name="typical-workflow"></a>Fluxo de trabalho típico

O fluxo de trabalho típico é a seguinte:

1. Instale um desenvolvimento ou um banco de dados de teste em seu computador local. Consulte [instalar sistemas de banco de dados, ferramentas e exemplos de](../data-tools/installing-database-systems-tools-and-samples.md). Se você estiver usando um serviço de dados do Azure, esta etapa não é necessária.

2. Teste a conexão para o banco de dados (ou serviço ou arquivo local) no Visual Studio. Consulte [adicionar novas conexões](../data-tools/add-new-connections.md).

3. (Opcional) Use as ferramentas para gerar e configurar um novo modelo. Modelos com base na estrutura de entidade são a recomendação padrão para novos aplicativos. O modelo, qualquer um que você usa, é a fonte de dados que o aplicativo interage com. O modelo logicamente fica entre o banco de dados ou serviço e o aplicativo. Consulte [adicionar novas fontes de dados](../data-tools/add-new-data-sources.md).

4. Arraste a fonte de dados de **fontes de dados** janela em uma superfície de design de formulários do Windows, o ASP.NET ou o Windows Presentation Foundation para gerar o código de associação de dados que exibirão os dados para o usuário da maneira que você especificar. Consulte [associar controles a dados no Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md).

5. Adicione código personalizado para coisas como regras de negócio, pesquisa e a validação de dados, ou para tirar proveito da funcionalidade personalizada que expõe o banco de dados subjacente.

Você pode ignorar a etapa 3 e programar um aplicativo .NET para emitir comandos diretamente para um banco de dados, em vez de usar um modelo. Nesse caso, você encontrará a documentação relevante aqui: [ADO.NET](/dotnet/framework/data/adonet/index). Observe que você ainda pode usar o Assistente de configuração de fonte de dados e designers para gerar código de associação de dados ao preencher seus próprios objetos em memória e, em seguida, controles de interface do usuário de associação de dados para esses objetos.

## <a name="see-also"></a>Consulte também

- [Acessar dados no Visual Studio](../data-tools/accessing-data-in-visual-studio.md)