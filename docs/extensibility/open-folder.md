---
title: Visão geral de extensibilidade do Visual Studio abrir pasta | Microsoft Docs
ms.custom: ''
ms.date: 02/21/2018
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 94c3f8bf-1de3-40ea-aded-7f40c4b314c7
author: vukelich
ms.author: svukel
manager: viveis
ms.workload:
- vssdk
ms.openlocfilehash: 1bbe9638777bc672a0cec494498a38f4bd8ce1f4
ms.sourcegitcommit: 768118d470da9c7164d2f23ca918dfe26a4be72f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/28/2018
---
# <a name="open-folder-extensibility"></a>Abra a extensibilidade de pasta

O [Abrir pasta](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md) recurso permite aos usuários abrir qualquer código no Visual Studio sem a necessidade de arquivos de projeto ou solução. Abrir pasta fornece que os recursos que os usuários esperam do Visual Studio, como:

* Pesquisa e integração do Gerenciador de soluções
* Coloração de editor
* Ir para navegação
* Localizar em busca de arquivos

Quando usado com cargas de trabalho como para desenvolvimento de .NET e C++, os usuários também obtém:

* Intellisense avançada
* Recursos específicos de idioma

Com a pasta aberta, os autores de extensão podem criar recursos avançados para qualquer idioma. Existem APIs para dar suporte a criação, depuração e a pesquisa de símbolo para qualquer arquivo de um usuário da Base de código. Extensores atuais podem atualizar seus recursos existentes do Visual Studio para entender o código sem o suporte de projetos ou uma solução.

## <a name="an-api-without-project-systems"></a>Uma API sem sistemas de projeto

Historicamente, o Visual Studio entendido apenas arquivos em uma solução e seus projetos usando sistemas de projeto. Um sistema de projeto é responsável pelas interações do usuário e a funcionalidade de um projeto carregado. Ele entende que contém os arquivos de seu projeto, a representação visual do conteúdo do projeto, as dependências em outros projetos, e o arquivo de projeto de modificação de subjacente. É por meio desses recursos que outros componentes funcionam em nome do usuário e hierarquias. Nem todas as bases de código também são representados em uma estrutura de projeto e solução. Linguagens de script e código do código-fonte aberto escrito em C++ para Linux são bons exemplos. Com a pasta aberta, o Visual Studio fornece aos usuários uma nova maneira de interagir com seu código-fonte.

As APIs de pasta aberta estão sob o `Microsoft.VisualStudio.Workspace.*` namespace e estão disponíveis para os extensores produzir e consumir dados ou ações em torno de arquivos na pasta aberta. Extensões podem usar essas APIs para fornecer funcionalidade para várias áreas, incluindo:

- [Espaços de trabalho](workspaces.md) - o a partir de extensibilidade do ponto de abrir pasta é o espaço de trabalho e suas APIs.
- [Ações e os contextos de arquivo](workspace-file-contexts.md) -inteligência de código específico fornecido por meio de contextos de arquivo do arquivo.
- [Indexação](workspace-indexing.md) - coletar e persistir dados sobre espaços de trabalho de abrir a pasta.
- [Serviços de idioma](workspace-language-services.md) -integrar serviços de idioma em espaços de trabalho de abrir a pasta.
- [Criar](workspace-build.md) -suporte para espaços de trabalho de abrir a pasta de compilação.

Serão necessário adotar novas APIs para dar suporte a abrir a pasta recursos que usam os seguintes tipos:

- `IVsHierarchy`
- `IVsProject`
- `DTE`

## <a name="feedback-comments-issues"></a>Comentários, comentários, problemas

Abra a pasta e o `Microsoft.VisualStudio.Workspace.*` APIs estão em desenvolvimento ativo. Se você vir um comportamento inesperado, consulte os problemas conhecidos da versão do seu interesse. A comunidade de desenvolvedores é o local recomendado para votar e crie quaisquer problemas. Para cada comentários, é altamente recomendável obter uma descrição detalhada do problema. Inclui a versão do Visual Studio que você desenvolve para, as APIs que você está usando (o que é implementado e que você está interagindo com), o resultado esperado e o resultado real. Se possível, inclua um despejo do processo devenv.exe. Use o problema do GitHub de controle para fazer comentários sobre isso e relacionados a documentação.

## <a name="next-steps"></a>Próximas etapas

* [Espaços de trabalho](workspaces.md) -Saiba mais sobre o espaço de trabalho de abrir a pasta API.