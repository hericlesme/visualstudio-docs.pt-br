---
title: Suporte a NGen no VSIX v3 | Microsoft Docs
ms.custom: 
ms.date: 11/09/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1472e884-c74e-4c23-9d4a-6d8bdcac043b
caps.latest.revision: "1"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 15277f0a1038e43bb316d604cbc415da4a5d80bd
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ngen-support-in-vsix-v3"></a>Suporte a NGen no VSIX v3

Com 2017 do Visual Studio e o novo v3 VSIX extensão (versão 3) o manifesto formato, extensão desenvolvedores pode "ngen" seus assemblies no momento da instalação.

Abaixo está um trecho do MSDN que explica o que "ngen":

>O Gerador de Imagem Nativa (Ngen.exe) é uma ferramenta que melhora o desempenho de aplicativos gerenciados. Ngen.exe cria imagens nativas, que são arquivos que contém o código de máquina específico do processamento compilado e as instala no cache de imagem nativa do computador local. O tempo de execução pode usar imagens nativas do cache em vez de usar o compilador JIT (Just-In-Time) para compilar o assembly original.
>
>de [Ngen.exe (gerador de imagem nativa)](https://msdn.microsoft.com/en-us/library/6t9t5wcf(v=vs.110).aspx)

Em ordem "NGen" um assembly, VSIX deve ser instalado "por instância por máquina". Isso pode ser habilitado, marcando a caixa de seleção "todos os usuários" no designer de extension.vsixmanifest:

![Verifique todos os usuários](media/check-all-users.png)

## <a name="how-to-enable-ngen"></a>Como habilitar o Ngen

Para habilitar o ngen para um assembly, você pode usar o **propriedades** janela no Visual Studio.

Há 4 propriedades que podem ser definidas:

1. **NGen** (Boolean) - se for true, o instalador do Visual Studio será "ngen" do assembly.
2. **Aplicativo NGen** (string) - Ngen fornece a oportunidade de usar o arquivo App. config de um aplicativo para resolver as dependências de assembly. Esse valor deve ser definido como um aplicativo cujo App. config que você deseja usar (relativo ao diretório de instalação do Visual Studio).
3. **Arquitetura do NGen** (enum) - arquitetura nativamente compilar seu assembly. As opções são: uma. B NotSpecified. X86 c. X64 d. Todos
4. **Prioridade do NGen** (número inteiro entre 1 e 3) - nível de prioridade do Ngen está documentado em [níveis de prioridade Ngen.exe](https://msdn.microsoft.com/en-us/library/6t9t5wcf(v=vs.110).aspx#Anchor_3).

Aqui está uma visão de **propriedades** janela em ação:

![NGen nas propriedades](media/ngen-in-properties.png)

Isso adicionará metadados para a referência de projeto dentro o VSIX arquivo do projeto. csproj:

```xml
 <ProjectReference Include="..\ClassLibrary1\ClassLibrary1.csproj">
    <Project>{69a979f1-eba2-43e7-9346-0e56e803508b}</Project>
    <Name>ClassLibrary1</Name>
    <Ngen>True</Ngen>
    <NgenApplication>vsn.exe</NgenApplication>
    <NgenArchitecture>X86</NgenArchitecture>
    <NgenPriority>2</NgenPriority>
</ProjectReference>
 ```

 >**Observação:** você pode editar o arquivo. csproj diretamente, se você preferir.

## <a name="extra-information"></a>Informações adicionais

As alterações de propriedade designer se aplicam a mais do que apenas as referências do projeto; Você pode definir os metadados do Ngen de itens dentro de seu projeto também desde que os itens são assemblies .NET (usando os métodos descritos acima).