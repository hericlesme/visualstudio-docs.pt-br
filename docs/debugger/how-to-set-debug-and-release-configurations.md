---
title: Define a depuração e configurações de versão | Microsoft Docs
ms.custom: ''
ms.date: 04/10/2017
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.builds
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- configurations, release
- build configurations, release
- projects [Visual Studio], release configurations
- debugging [Visual Studio], release configurations
- release builds, changing settings
- debug builds
- debug builds, switching to release build
- debug builds, changing configuration settings
- debugging [Visual Studio], debug configurations
- projects [Visual Studio], debug configurations
- build configurations, debug
- debug configurations
- release builds, switching to debug build
- Visual Basic projects, debug and release builds
ms.assetid: 57b6bbb7-f2af-48f7-8773-127d75034ed2
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ea27fdccaadc70f22d9c9c02d75ddef98a11be13
ms.sourcegitcommit: 0e5289414d90a314ca0d560c0c3fe9c88cb2217c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/19/2018
ms.locfileid: "39153092"
---
# <a name="set-debug-and-release-configurations-in-visual-studio"></a>Define a depuração e configurações no Visual Studio de versão
Projetos do Visual Studio tem a versão separada e configurações para o seu programa de depuração. Como os nomes já dizem, você compila a versão de depuração para depuração e a versão de lançamento para a distribuição da versão final.  
  
A configuração de depuração do seu programa é compilada com informações de depuração simbólica e sem otimização. A otimização complica a depuração, porque a relação entre o código fonte e as instruções geradas é mais complexa.  
  
A configuração de versão do seu programa não contém nenhuma informação de depuração simbólica e é totalmente otimizada. Depurar informações podem ser geradas em arquivos. PDB [dependendo das opções de compilador](#BKMK_symbols_release) que são usados. Criar arquivos. PDB pode ser muito útil se você posteriormente precisa depurar a versão de lançamento.  
  
Para obter mais informações sobre configurações de build, consulte [Noções básicas sobre configurações de build](../ide/understanding-build-configurations.md).  
  
Você pode alterar a configuração de compilação a **Build** menu, na barra de ferramentas ou nas páginas de propriedades do projeto. Páginas de propriedades do projeto são específicas do idioma. O procedimento a seguir mostra como alterar a configuração de build no menu e barra de ferramentas. Para obter mais informações sobre como alterar a configuração de build em projetos em linguagens diferentes, consulte a seção Consulte também abaixo.  
  
## <a name="change-the-build-configuration"></a>Alterar a configuração de build  
  
1.  Dos **Build** menu, selecione **Configuration Manager**, em seguida, selecione **depurar** ou **versão**.  
  
2.  Na barra de ferramentas, escolha **Debug** ou **Release** do **configurações da solução** caixa de listagem.  
  
     ![configuração de build da barra de ferramentas](../debugger/media/toolbarbuildconfiguration.png "ToolbarBuildConfiguration")  
  
     Essa barra de ferramentas não está disponível nas edições Express. Você pode usar o **solução de compilação F6** e **iniciar depuração F5** itens de menu para escolher a configuração.

## <a name="BKMK_symbols_release"></a>Gerar arquivos de símbolo (. PDB) para uma compilação

Para a maioria dos tipos de projeto, os arquivos. PDB são gerados por padrão para ambos os debug e builds de versão, mas as configurações padrão são diferentes dependendo do seu tipo de projeto específico e a versão do Visual Studio. Você pode configurar se o compilador gera arquivos. PDB e que tipo de informação de depuração incluem.

> [!IMPORTANT] 
> O depurador carregará apenas um arquivo .pdb para um arquivo executável que corresponde exatamente ao arquivo .pdb criado quando o executável foi compilado (isto é, o .pdb deve ser o original ou uma cópia do arquivo .pdb original). Para obter mais informações, consulte [por que o Visual Studio exige arquivos de símbolo do depurador para corresponder exatamente os arquivos binários que eles foram criados?](https://blogs.msdn.microsoft.com/jimgries/2007/07/06/why-does-visual-studio-require-debugger-symbol-files-to-exactly-match-the-binary-files-that-they-were-built-with/)

Cada tipo de projeto pode ter uma maneira diferente de como definir essas opções.

### <a name="generate-symbol-files-for-a-c-aspnet-or-visual-basic-project"></a>Gerar arquivos de símbolo para um projeto c#, ASP.NET ou Visual Basic

Para obter informações detalhadas sobre configurações do projeto para configurações de depuração em c#, consulte [configurações do projeto para uma configuração de c# depuração](../debugger/project-settings-for-csharp-debug-configurations.md). Para o Visual Basic, consulte [neste tópico](../debugger/project-settings-for-a-visual-basic-debug-configuration.md).

1. Clique com botão direito no projeto no Gerenciador de soluções e escolha **propriedades**.

2. Escolha uma **Release** ou **Debug** criar com base a **configuração** lista.

2. Escolher **construir** configurações e, em seguida, clique o **avançado** botão.

    No Visual Basic, você deve escolher o **Compile** as configurações e o **opções avançadas de compilação** botão em vez disso.

3. Escolher **completo**, **portátil**, ou **pdb_only** no **informações de depuração** caixa de listagem (**gerar informações de depuração** no Visual Basic).

    O formato portátil é o formato de plataforma cruzada mais recente para o .NET Core. Para obter mais informações sobre as opções, consulte [caixa de diálogo Configurações avançadas de compilação (c#)](../ide/reference/advanced-build-settings-dialog-box-csharp.md).

    ![Gerar PDBs para compilações em c#](../debugger/media/dbg_project_properties_pdb_csharp.png "GeneratePDBsForCSharp")

4. Criar o projeto.

    Os arquivos de símbolo são criados na mesma pasta que o executável ou o arquivo de saída principal.

### <a name="generate-symbol-files-for-a-c-project"></a>Gerar arquivos de símbolo para um projeto do C++

1. Clique com botão direito no projeto no Gerenciador de soluções e escolha **propriedades**.

2. Escolha uma **Release** ou **Debug** criar com base a **configuração** lista.

2. Sob **vinculador > Debugging**, selecione desejado opções para **gerar informações de depuração**.

    Para obter informações detalhadas sobre configurações do projeto para configurações de depuração em C++, consulte [configurações do projeto para uma configuração de depuração de C++](../debugger/project-settings-for-a-cpp-debug-configuration.md).

4. Configurar as opções para gerar arquivos de banco de dados do programa

    Na maioria dos projetos do C++, o valor padrão é `$(OutDir)$(TargetName).pdb`, que gera arquivos. PDB na pasta de saída.

    ![Gerar PDBs para compilações em C++](../debugger/media/dbg_project_properties_pdb_cplusplus.png "GeneratePDBsforCPlusPlus") 

5. Criar o projeto.

    Os arquivos de símbolo são criados na mesma pasta que o executável ou o arquivo de saída principal.
  
## <a name="see-also"></a>Consulte também  
 [Especificar arquivos de símbolo (. PDB) e arquivos de origem no depurador do Visua Studio](../debugger/debugger-settings-and-preparation.md)  
 [Preparação e configurações do depurador](../debugger/debugger-settings-and-preparation.md)   
 [Configurações do projeto para uma configuração de depuração de C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)   
 [Configurações do projeto para configurações de depuração de C#](../debugger/project-settings-for-csharp-debug-configurations.md)   
 [Configurações do projeto para uma configuração de depuração do Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)   
 [Como criar e editar configurações](../ide/how-to-create-and-edit-configurations.md)
