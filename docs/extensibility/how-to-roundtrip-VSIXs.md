---
title: "Como: extensões de ida e volta para o Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 06/25/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2d6cf53c-011e-4c9e-9935-417edca8c486
caps.latest.revision: "1"
author: willbrown
ms.author: willbrown
manager: justinclareburt
ms.openlocfilehash: 99bdd5a0f31b9cbccd84a7c05f6d3cdcc0c267f6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="how-to-make-extensions-compatible-with-visual-studio-2017-and-visual-studio-2015"></a>Como: fazer extensões compatível com 2017 do Visual Studio e o Visual Studio 2015

Este documento explica como criar projetos de extensibilidade ida e volta entre o Visual Studio 2015 e 2017 do Visual Studio. Depois de concluir esta atualização, um projeto será capaz de abrir, criar, instalar e executar no Visual Studio 2015 e 2017 do Visual Studio.  Como referência, algumas extensões que podem viagem entre o Visual Studio 2015 e 2017 do Visual Studio podem ser encontradas [aqui](https://github.com/Microsoft/VSSDK-Extensibility-Samples) nos exemplos de extensibilidade da Microsoft.

Se você pretender criado no Visual Studio de 2017, mas deseja que a saída VSIX para ser executado no Visual Studio 2015 e 2017 do Visual Studio, consulte o [documento de migração de extensão](how-to-migrate-extensibility-projects-to-visual-studio-2017.md).

>**Observação:** devido a alterações no Visual Studio entre versões, algumas coisas que trabalhou em uma versão não funcionará outro. Certifique-se de que os recursos que você está tentando acessar estão disponíveis em ambas as versões ou a extensão terá resultados inesperados.

Aqui está uma descrição das etapas que você concluirá neste documento para viagem um VSIX:

1. Importe pacotes do NuGet corretos.
2. Atualize o manifesto de extensão:
    * Destino de instalação
    * Pré-requisitos
3. Atualize CSProj:
    * Atualização `<MinimumVisualStudioVersion>`.
    * Adicionar o `<VsixType>` propriedade.
    * Adicionar a propriedade de depuração `($DevEnvDir)` 3 vezes.
    * Adicione condições de importação de ferramentas de compilação e destinos.

4. Compilação e teste

## <a name="environment-setup"></a>Configuração de ambiente

Este documento assume que você tenha os seguintes itens instalados em seu computador:

* Visual Studio 2015 com o SDK do VS instalado
* Visual Studio de 2017 com a carga de trabalho de extensibilidade instalada

## <a name="recommended-approach"></a>Abordagem recomendada

É altamente recomendável para iniciar a atualização com o Visual Studio 2015, em vez de 2017 do Visual Studio. O principal benefício de desenvolvimento no Visual Studio 2015 é garantir que você não fizer referência a assemblies que não estão disponíveis no Visual Studio 2015. Se você fizer o desenvolvimento no Visual Studio de 2017, há um risco que você pode introduzir uma dependência em um assembly que só existe no Visual Studio de 2017.

## <a name="ensure-there-is-no-reference-to-projectjson"></a>Certifique-se de que não há nenhuma referência para o Project

Neste documento, podemos irá inserir instruções de importação condicional em seu arquivo csproj.  Isso não funcionará se as referências de NuGet são armazenadas no Project. Como tal, é recomendável mover todas as referências de NuGet para o arquivo Packages. config.
Se o seu projeto contém um arquivo Project. JSON:

* Anote as referências no Project. JSON.
* No Gerenciador de soluções, exclua o arquivo do Project do projeto.
    * Isso excluirá o arquivo Project. JSON e removê-lo do projeto.
* Adicione que as referências de NuGet novamente ao projeto.
    * Com o botão direito na solução e escolha **gerenciar pacotes NuGet para solução...**
    * Visual Studio cria automaticamente o arquivo Packages. config para você

>**Observação:** se seu projeto continha EnvDTE pacotes, talvez eles precisam ser adicionados pelo clique com o botão direito em **referências** selecionando **adicionar referência** e adicionar a referência apropriada.  O uso de pacotes do NuGet pode criar erros durante a tentativa de compilar o projeto.

## <a name="adding-appropriate-build-tools"></a>Adicionar ferramentas de compilação apropriado

Para ter certeza de que precisamos adicionar ferramentas de compilação que permitirão criar e depurar adequadamente. A Microsoft criou um assembly para esta chamada Microsoft.VisualStudio.Sdk.BuildTasks.

Para criar e implantar um VSIXv3 no Visual Studio 2015 e 2017, os seguintes pacotes do NuGet serão necessárias:

Versão | Ferramentas internas
--- | ---
Visual Studio 2015 | Microsoft.VisualStudio.Sdk.BuildTasks.14.0
Visual Studio 2017 | Microsoft.VSSDK.BuildTool

Para fazer isso:

* Adicione o pacote do NuGet Microsoft.VisualStudio.Sdk.BuildTasks.14.0 ao seu projeto.
* Se seu projeto não contém Microsoft.VSSDK.BuildTools, adicioná-lo.
* Certifique-se de que a versão de Microsoft.VSSDK.BuildTools é 15.x ou superior.

## <a name="update-extension-manifest"></a>Atualizar o manifesto de extensão

### <a name="1-installation-targets"></a>1. Destinos de instalação

É necessário informar quais versões para o destino para a criação de um VSIX ao Visual Studio.  Normalmente, essas referências são para a versão 14.0 (Visual Studio 2015) ou versão 15.0 (Visual Studio 2017).  Em nosso caso, queremos desenvolver um VSIX que irá instalar uma extensão para ambas, portanto, precisamos ambas as versões de destino.  Se você quiser o VSIX para compilar e instalar em versões anteriores ao 14.0, isso pode ser feito definindo o número de versão anterior; No entanto, não há suporte para a versão 10.0 e versões anteriores.

* Abra o arquivo source.extension.vsixmanifest no Visual Studio.
* Abra o **instalar destinos** guia.
* Alterar o **versão intervalo** para [14.0, 16.0).  O ' [' informa ao Visual Studio para incluir 14.0 e todas as versões anteriores ele.  O ')' informa ao Visual Studio para incluir todas as versões do 15.0 até, mas não incluindo versão 16.0.
* Salve todas as alterações e feche todas as instâncias do Visual Studio.

![Imagem de destinos de instalação](media/visual-studio-installation-targets-example.png)

### <a name="2-adding-prerequisites-to-the-extensionvsixmanifest-file"></a>2. Adicionando pré-requisitos para o arquivo extension.vsixmanifest

Pré-requisitos são um novo recurso do Visual Studio de 2017.  Nesse caso, é necessário o Editor de núcleo do Visual Studio como um pré-requisito. Desde que o designer de VSIX de 2015 do Visual Studio não lida com a nova `Prerequisites` seção, você precisará editar esta parte manualmente no código XML.  Como alternativa, você pode abrir o Visual Studio de 2017 e usar o designer de manifesto atualizado para inserir os pré-requisitos.

Para fazer isso manualmente:

* Navegue até o diretório de projeto no Explorador de arquivos.
* Abra o `extension.vsixmanifest` arquivo com um editor de texto.
* Adicione a seguinte marca:

```xml
<Prerequisites>
    <Prerequisite Id="Microsoft.VisualStudio.Component.CoreEditor" Version="[15.0,16.0)" DisplayName="Visual Studio core editor" />
</Prerequisites>
```

* Salve e feche o arquivo.

>**Observação:** se você optar por fazer isso com o designer VSIX no Visual Studio de 2017, você precisará editar manualmente a versão pré-requisito para garantir que ele é compatível com todas as versões do Visual Studio de 2017.  Isso ocorre porque o designer irá inserir a versão mínima como sua versão atual do Visual Studio (por exemplo, 15.0.26208.0).  No entanto, desde que outros usuários podem ter uma versão anterior, você deve editar manualmente a para 15.0.

Neste ponto, o arquivo de manifesto deve ser algo assim:

![Exemplo de pré-requisitos](media/visual-studio-prerequisites-example.png)

## <a name="modify-the-project-file-myprojectcsproj"></a>Modificar o arquivo de projeto (myproject.csproj)

É altamente recomendável ter uma referência a um modificado. csproj aberto durante esta etapa.  Você pode encontrar vários exemplos [aqui](https://github.com/Microsoft/VSSDK-Extensibility-Samples).  Selecione uma amostra de extensibilidade, localizar o arquivo. csproj para referência e execute as etapas a seguir:

* Navegue até o diretório de projeto no Explorador de arquivos.
* Abra o arquivo myproject.csproj com um editor de texto.

### <a name="1-update-the-minimumvisualstudioversion"></a>1. Atualizar o MinimumVisualStudioVersion

* Definir a versão mínima do studio visual `$(VisualStudioVersion)` e adicione uma instrução condicional para ele.  Adicione essas marcas se elas não existirem.  Certifique-se de que as marcas são definidas como abaixo:

```xml
<VisualStudioVersion Condition="'$(VisualStudioVersion)' == ''">14.0</VisualStudioVersion>
<MinimumVisualStudioVersion>$(VisualStudioVersion)</MinimumVisualStudioVersion>
```

### <a name="2-add-the-vsixtype-property"></a>2. Adicione a propriedade VsixType

* Adicione a seguinte marca `<VsixType>v3</VsixType>` para um grupo de propriedades.

>**Observação:** é recomendável adicionar isso abaixo o `<OutputType></OutputType>` marca.

### <a name="3-add-the-debugging-properties"></a>3. Adicionar propriedades de depuração

* Adicione o grupo de propriedades a seguir:

```xml
<PropertyGroup>
    <StartAction>Program</StartAction>
    <StartPrograms>$(DevEnvDir)devenv.exe</StartPrograms>
    <StartArguments>/rootsuffix Exp</StartArguments>
</PropertyGroup>
```

* Excluir todas as instâncias das seguintes opções de arquivo. csproj e qualquer. csproj.user arquivos:

```xml
<StartAction>Program</StartAction>
<StartPrograms>$(ProgramFiles)\Microsoft Visual Studio 14.0\Common7\IDE\devenv.exe</StartPrograms>
<StartArguments>/rootsuffix Exp</StartArguments>
```

### <a name="4-add-conditions-to-the-build-tools-imports"></a>4. Adicionar condições para as importações de ferramentas de compilação

* Adicionar instruções condicionais adicionais para o `<import>` marcas que têm uma referência de Microsoft.VSSDK.BuildTools.  Faça isso inserindo `'$(VisualStudioVersion)' != '14.0' And` na frente da instrução de condição.  Essas instruções aparecerá no cabeçalho e rodapé do arquivo csproj.

Por exemplo:

```xml
<Import Project="packages\Microsoft.VSSDK.BuildTools.15.0.26201… Condition="'$(VisualStudioVersion)' != '14.0' And Exists(…/>
```

* Adicionar instruções condicionais adicionais para o `<import>` marcas que têm um Microsoft.VisualStudio.Sdk.BuildTasks.14.0.  Faça isso inserindo `'$(VisualStudioVersion)' == '14.0' And` na frente da instrução de condição. Essas instruções aparecerá no cabeçalho e rodapé do arquivo csproj.

Por exemplo:

```xml
<Import Project="packages\ Microsoft.VisualStudio.Sdk.BuildTasks.14.0.14.0… Condition="'$(VisualStudioVersion)' == '14.0' And Exists(…/>
```

* Adicionar instruções condicionais adicionais para o `<Error>` marcas que têm uma referência de Microsoft.VSSDK.BuildTools.  Faça isso inserindo `'$(VisualStudioVersion)' != '14.0' And` na frente da instrução de condição. Essas instruções serão exibida no rodapé do arquivo csproj.

Por exemplo:

```xml
<Error Condition="'$(VisualStudioVersion)' != '14.0' And Exists('packages\Microsoft.VSSDK.BuildTools.15.0.26201…/>
```

* Adicionar instruções condicionais adicionais para o `<Error>` marcas que têm um Microsoft.VisualStudio.Sdk.BuildTasks.14.0.  Faça isso inserindo `'$(VisualStudioVersion)' == '14.0' And` na frente da instrução de condição. Essas instruções serão exibida no rodapé do arquivo csproj.

Por exemplo:

```xml
<Error Condition="'$(VisualStudioVersion)' == '14.0' And Exists('packages\ Microsoft.VisualStudio.Sdk.BuildTasks.14.0.14.0…/>
```

* Salve o arquivo csproj e fechá-lo.

## <a name="test-the-extension-installs-in-visual-studio-2015-and-visual-studio-2017"></a>Instala a extensão de teste no Visual Studio 2015 e 2017 do Visual Studio

Neste ponto, seu projeto deve estar pronto para criar um VSIXv3 que pode instalar no Visual Studio 2015 e 2017 do Visual Studio.

* Abra seu projeto no Visual Studio 2015
* Compilar seu projeto e Confirmar na saída de um VSIX compilações corretamente
* Navegue até o diretório do projeto
* Pasta de depuração abrir -> Lixeira
* Clique duas vezes no arquivo VSIX e instalar a extensão no Visual Studio 2015 e 2017 do Visual Studio
* Certifique-se de que você pode ver a extensão em Ferramentas -> extensões e atualizações na seção "Instalar".
* Tentativa de execução/usar a extensão para verificar se ele funciona

![Localizando uma VSIX](media/finding-a-VSIX-example.png)

>**Observação:** se seu projeto trava com a mensagem "abrir o arquivo" força de fechar o Visual Studio, navegue até o diretório do projeto, Mostrar pastas ocultas e exclua a pasta do VS.
