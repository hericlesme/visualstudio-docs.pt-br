---
title: Como migrar uma linguagem específica do domínio para uma nova versão
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 83f80e9fe0bf68f5d10d8f3b76840b55de025f33
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/20/2018
---
# <a name="how-to-migrate-a-domain-specific-language-to-a-new-version"></a>Como migrar uma linguagem específica do domínio para uma nova versão
Você pode migrar projetos que definem e usam a linguagem específica de domínio para [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)] da versão do [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] que foi distribuído com [!INCLUDE[vs_orcas_long](../debugger/includes/vs_orcas_long_md.md)].

 Uma ferramenta de migração é fornecida como parte do [!INCLUDE[vssdk_current_long](../misc/includes/vssdk_current_long_md.md)]. A ferramenta converte [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] projetos e soluções que usam ou definem as ferramentas de DSL.

 Você deve executar a ferramenta de migração explicitamente: ele não será iniciado automaticamente quando você abrir uma solução em [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. A ferramenta e o documento de diretrizes detalhadas podem ser encontrados no seguinte caminho:

 **% Programa Files%\Microsoft Visual Studio 2010 SDK\VisualStudioIntegration\Tools\DSLTools\DslProjectsMigrationTool.exe**

## <a name="before-you-migrate-your-dsl-projects"></a>Antes de migrar seus projetos DSL
 A ferramenta de migração modifica [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] arquivos de projeto (**. csproj**) e arquivos de solução (**. sln**).

#### <a name="to-prepare-projects-for-migration"></a>Para preparar os projetos para migração.

-   Verifique se o **. csproj** e **. sln** arquivos podem ser gravados. Se estiverem sob controle de origem, certifique-se de que eles são check-out.

-   Faça uma cópia das pastas que você deseja migrar.

## <a name="migrating-a-collection-of-projects"></a>Migrar uma coleção de projetos

#### <a name="to-migrate-dsl-projects-and-solutions-to-visual-studio-2010"></a>Para migrar DSL projetos e soluções para o Visual Studio 2010

1.  Inicie a ferramenta de migração de DSL.

    -   Você pode clique duas vezes a ferramenta no Windows Explorer (ou Explorador de arquivos) ou iniciar a ferramenta de prompt de comando. A ferramenta está neste local:

         **%ProgramFiles%\Microsoft visual Studio 2010 SDK\VisualStudioIntegration\Tools\DSLTools\DslProjectsMigrationTool.exe**

2.  Escolha uma pasta que contém as soluções e projetos que você deseja converter.

    -   Digite o caminho na caixa na parte superior da ferramenta, ou clique **procurar**.

     A ferramenta de migração exibe uma árvore de projetos que definem ou usar DSLs. A árvore inclui todos os projetos que usa o **Microsoft.VisualStudio.Modeling.Sdk** ou **TextTemplating** assemblies.

3.  Examine a árvore de projetos e desmarque os projetos que você não deseja converter.

    -   Selecione um projeto ou solução para ver uma lista das alterações que fará com que a ferramenta.

        > [!NOTE]
        >  As caixas de seleção que aparecem ao lado dos nomes de pasta não têm nenhum efeito. Você deve expandir as pastas para inspecionar os projetos e soluções.

4.  Converta os projetos.

    1.  Clique em **converter**.

         Antes de cada arquivo de projeto é convertido, uma cópia do *projeto *. csproj** é salvo como *projeto * * *.vs2008.csproj**

         Uma cópia de cada *solução *. sln** é salvo como *solução *.vs2008.sln**

    2.  Investigue quaisquer conversões com falha que são relatados.

         Falhas são reportadas na janela de texto. Além disso, o modo de exibição de árvore mostra um sinalizador vermelho em cada nó que falhou ao converter. Você pode clicar no nó para obter mais informações sobre essa falha.

5.  **Transformar todos os modelos** em soluções que contém com êxito convertido projetos.

    1.  Abra a solução.

    2.  Clique o **transformar todos os modelos** botão no cabeçalho do Gerenciador de soluções.

        > [!NOTE]
        >  Você pode tornar esta etapa desnecessária. Para obter mais informações, consulte [como automatizar a transformação de todos os modelos](http://msdn.microsoft.com/b63cfe20-fe5e-47cc-9506-59b29bca768a).

6.  Atualize seu código personalizado no projeto convertido.

    -   Tentativa de compilar os projetos e investigar quaisquer falhas.

    -   O designer de teste.


[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="see-also"></a>Consulte também

- [Postagens de blog relacionados](https://blogs.msdn.microsoft.com/visualstudioalm/tag/code-index/)