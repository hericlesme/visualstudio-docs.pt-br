---
title: IDs de carga de trabalho e de componente das Ferramentas de Build do Visual Studio 2017 | Microsoft Docs
description: "Usar IDs de carga de trabalho e de componente do Visual Studio para criar aplicativos clássicos baseados no Windows"
keywords: 
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.date: 12/01/2017
ms.topic: article
helpviewer_keywords:
- workload ID, Visual Studio
- component ID, Visual Studio
- install Visual Studio, administrator guide
ms.service: 
ms.technology: vs-acquisition
ms.assetid: b99298df-0280-47fc-af73-44cd7a8ac553
ms.openlocfilehash: 2c691f2e0d4aae1344afd18f50a858e17f99c547
ms.sourcegitcommit: ae9450e81c4167b3fbc9ee5d1992fc693628eafa
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/04/2017
---
# <a name="visual-studio-build-tools-2017-component-directory"></a>Diretório de componentes das Ferramentas de Build do Visual Studio 2017

As tabelas desta página listam as IDs que podem ser usadas para instalar o Visual Studio usando a linha de comando. Observe que adicionaremos outros componentes conforme atualizações forem liberadas para o Visual Studio.

Além disso, observe o seguinte sobre essa página:

* Cada carga de trabalho tem sua própria seção, seguida pela ID da carga de trabalho e por uma tabela dos componentes que estão disponíveis para a carga de trabalho.
* Por padrão, os componentes **Obrigatórios** serão instalados durante a instalação da carga de trabalho. Se preferir, também será possível instalar os componentes **Recomendados** e **Opcionais**.
* Também adicionamos uma seção que lista os componentes adicionais que não são afiliados a nenhuma carga de trabalho.

Para obter mais informações sobre como usar essas IDs, consulte a página [Usar parâmetros de linha de comando para instalar o Visual Studio 2017](use-command-line-parameters-to-install-visual-studio.md). Além disso, para obter uma lista de IDs de carga de trabalho e de componente para outros produtos, consulte a página [IDs de carga de trabalho e de componente do Visual Studio 2017](workload-and-component-ids.md).

## <a name="msbuild-tools"></a>Ferramentas do MSBuild

**ID:** Microsoft.VisualStudio.Workload.MSBuildTools

**Descrição:** fornece as ferramentas necessárias para criar aplicativos baseados em MSBuild.

### <a name="components-included-by-this-workload"></a>Componentes incluídos por essa carga de trabalho

ID do componente | Nome | Versão | Tipo de dependência
--- | --- | --- | ---
Microsoft.Component.MSBuild | MSBuild | 15.0.27019.1 | Necessária
Microsoft.VisualStudio.Component.CoreBuildTools | Principais Ferramentas de Build do Visual Studio | 15.0.27005.2 | Necessária
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compiladores Roslyn do C# e Visual Basic | 15.0.27019.1 | Necessária
Microsoft.VisualStudio.Component.FSharp.MSBuild | compilador F# | 15.0.27019.1 | Opcional

## <a name="net-core-build-tools"></a>Ferramentas de compilação do .NET Core

**ID:** Microsoft.VisualStudio.Workload.NetCoreBuildTools

**Descrição:** ferramentas para criar aplicativos .NET Core.

### <a name="components-included-by-this-workload"></a>Componentes incluídos por essa carga de trabalho

ID do componente | Nome | Versão | Tipo de dependência
--- | --- | --- | ---
Microsoft.Net.Core.Component.SDK | Ferramentas de desenvolvimento do .NET Core 1.0 a 1.1 | 15.0.26606.0 | Necessária
Microsoft.VisualStudio.Component.NuGet.BuildTools | Os destinos e as tarefas de compilação do NuGet | 15.0.26919.1 | Necessária
Microsoft.Net.Core.Component.SDK.1x | Ferramentas de desenvolvimento do .NET Core 1.0 – 1.1 para Desktop | 15.0.26919.1 | Opcional

## <a name="visual-c-build-tools"></a>Ferramentas de build do Visual C++

**ID:** Microsoft.VisualStudio.Workload.VCTools

**Descrição:** criar aplicativos clássicos baseados no Windows usando o poder do conjunto de ferramentas do Visual C++, ATL e recursos opcionais como MFC e C++/CLI.

### <a name="components-included-by-this-workload"></a>Componentes incluídos por essa carga de trabalho

ID do componente | Nome | Versão | Tipo de dependência
--- | --- | --- | ---
Microsoft.VisualStudio.Component.VC.CoreBuildTools | Principais recursos das Ferramentas de Build do Visual C++ | 15.0.27005.2 | Necessária
Microsoft.VisualStudio.Component.VC.Redist.14.Latest | Atualização Redistribuível do Visual C++ 2017 | 15.0.27019.1 | Necessária
Microsoft.VisualStudio.Component.Windows10SDK | Tempo de execução C Universal do Windows | 15.0.26621.2 | Necessária
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Ferramentas de análise estática | 15.0.26208.0 | Recomendado
Microsoft.VisualStudio.Component.VC.CMake.Project | Ferramentas do Visual C++ para CMake | 15.0.27019.1 | Recomendado
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | Conjunto de ferramentas do VC++ 2017 v141 (x86, x64) | 15.0.27019.1 | Recomendado
Microsoft.VisualStudio.Component.Windows10SDK.16299.Desktop | SDK do Windows 10 (10.0.16299.0) para Desktop C++ [x86 e x64] | 15.0.27128.1 | Recomendado
Microsoft.VisualStudio.Component.Windows10SDK.16299.UWP | SDK do Windows 10 (10.0.16299.0) para UWP: C#, VB, JS | 15.0.27128.1 | Recomendado
Microsoft.VisualStudio.Component.Windows10SDK.16299.UWP.Native | SDK do Windows 10 (10.0.16299.0) para UWP: C++ | 15.0.27128.1 | Recomendado
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Desenvolvimento do ASP.NET e para a Web | 15.0.27005.2 | Recomendado
Microsoft.Component.VC.Runtime.UCRTSDK | SDK do CRT Universal do Windows | 15.0.27019.1 | Opcional
Microsoft.Net.Component.4.6.1.SDK | SDK do .NET Framework 4.6.1 | 15.0.26621.2 | Opcional
Microsoft.Net.Component.4.6.1.TargetingPack | Pacote de direcionamento do .NET Framework 4.6.1 | 15.0.26621.2 | Opcional
Microsoft.VisualStudio.Component.VC.140 | Conjunto de ferramentas do VC++ 2015.3 v140 para área de trabalho (x86,x64) | 15.0.27019.1 | Opcional
Microsoft.VisualStudio.Component.VC.ATL | Suporte ao Visual C++ ATL | 15.0.26823.1 | Opcional
Microsoft.VisualStudio.Component.VC.ATLMFC | Suporte ao MFC e ATL (x86 e x64) | 15.0.27005.2 | Opcional
Microsoft.VisualStudio.Component.VC.ClangC2 | Clang/C2 (experimental) | 15.0.27019.1 | Opcional
Microsoft.VisualStudio.Component.VC.CLI.Support | Suporte ao C++/CLI | 15.0.27019.1 | Opcional
Microsoft.VisualStudio.Component.VC.Modules.x86.x64 | Módulos de Biblioteca Padrão (experimental) | 15.0.27019.1 | Opcional
Microsoft.VisualStudio.Component.VC.Tools.ARM | Compiladores e bibliotecas do Visual C++ para o ARM | 15.0.27019.1 | Opcional
Microsoft.VisualStudio.Component.VC.Tools.ARM64 | Compiladores e bibliotecas do Visual C++ para ARM64 | 15.0.27019.1 | Opcional
Microsoft.VisualStudio.Component.Windows10SDK.10240 | SDK do Windows 10 (10.0.10240.0) | 15.0.26208.0 | Opcional
Microsoft.VisualStudio.Component.Windows10SDK.10586 | SDK do Windows 10 (10.0.10586.0) | 15.0.26208.0 | Opcional
Microsoft.VisualStudio.Component.Windows10SDK.14393 | SDK do Windows 10 (10.0.14393.0) | 15.0.26208.0 | Opcional
Microsoft.VisualStudio.Component.Windows10SDK.15063.Desktop | SDK do Windows 10 (10.0.15063.0) para Desktop C++ [x86 e x64] | 15.0.27128.1 | Opcional
Microsoft.VisualStudio.Component.Windows10SDK.15063.UWP | SDK do Windows 10 (10.0.15063.0) para UWP: C#, VB, JS | 15.0.27128.1 | Opcional
Microsoft.VisualStudio.Component.Windows10SDK.15063.UWP.Native | SDK do Windows 10 (10.0.15063.0) para UWP: C++ | 15.0.27128.1 | Opcional
Microsoft.VisualStudio.Component.Windows10SDK.16299.Desktop.arm | SDK do Windows 10 (10.0.16299.0) para Desktop C++ [ARM e ARM64] | 15.0.27128.1 | Opcional
Microsoft.VisualStudio.Component.Windows81SDK | SDK do Windows 8.1 | 15.0.26208.0 | Opcional
Microsoft.VisualStudio.ComponentGroup.NativeDesktop.Win81 | SDK do Windows 8.1 e SDK do UCRT | 15.0.27019.1 | Opcional

## <a name="web-development-build-tools"></a>Ferramentas de build de desenvolvimento para a Web

**ID:** Microsoft.VisualStudio.Workload.WebBuildTools

**Descrição:** tarefas e destinos do MSBuild para a compilação de aplicativos Web.

### <a name="components-included-by-this-workload"></a>Componentes incluídos por essa carga de trabalho

ID do componente | Nome | Versão | Tipo de dependência
--- | --- | --- | ---
Microsoft.Net.Component.4.6.1.SDK | SDK do .NET Framework 4.6.1 | 15.0.26621.2 | Necessária
Microsoft.Net.Component.4.6.1.TargetingPack | Pacote de direcionamento do .NET Framework 4.6.1 | 15.0.26621.2 | Necessária
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Ferramentas de desenvolvimento do .NET Framework 4.6.1 | 15.0.27005.2 | Necessária
Microsoft.VisualStudio.Wcf.BuildTools.ComponentGroup | Ferramentas de build de desenvolvimento do WCF | 15.0.27019.1 | Necessária
Microsoft.VisualStudio.Web.BuildTools.ComponentGroup | Ferramentas de build de desenvolvimento para a Web | 15.0.26323.1 | Necessária
Microsoft.Net.Component.4.5.1.TargetingPack | Pacote de direcionamento do .NET Framework 4.5.1 | 15.0.26621.2 | Recomendado
Microsoft.Net.Component.4.5.2.TargetingPack | Pacote de direcionamento do .NET Framework 4.5.2 | 15.0.26621.2 | Recomendado
Microsoft.Net.Component.4.5.TargetingPack | Pacote de direcionamento do .NET Framework 4.5 | 15.0.26621.2 | Recomendado
Microsoft.Net.Component.4.6.TargetingPack | Pacote de direcionamento do .NET Framework 4.6 | 15.0.26621.2 | Recomendado
Microsoft.Net.Component.4.TargetingPack | Pacote de direcionamento do .NET Framework 4 | 15.0.26621.2 | Recomendado
Microsoft.Net.ComponentGroup.TargetingPacks.Common | Ferramentas de desenvolvimento do .NET Framework 4 a 4.6 | 15.0.26606.0 | Recomendado
Microsoft.Net.Core.Component.SDK | Ferramentas de desenvolvimento do .NET Core 1.0 a 1.1 | 15.0.26606.0 | Recomendado
Microsoft.VisualStudio.Component.NuGet.BuildTools | Os destinos e as tarefas de compilação do NuGet | 15.0.26919.1 | Recomendado
Microsoft.Net.Component.3.5.DeveloperTools | Ferramentas de desenvolvimento do .NET Framework 3.5 | 15.0.26621.2 | Opcional
Microsoft.Net.Component.4.6.2.SDK | SDK do .NET Framework 4.6.2 | 15.0.26208.0 | Opcional
Microsoft.Net.Component.4.6.2.TargetingPack | Pacote de direcionamento do .NET Framework 4.6.2 | 15.0.26208.0 | Opcional
Microsoft.Net.Component.4.7.1.SDK | .NET Framework 4.7.1 SDK | 15.0.27128.1 | Opcional
Microsoft.Net.Component.4.7.1.TargetingPack | Pacote de direcionamento do .NET Framework 4.7.1 | 15.0.27019.1 | Opcional
Microsoft.Net.Component.4.7.SDK | SDK do .NET Framework 4.7 | 15.0.26419.1 | Opcional
Microsoft.Net.Component.4.7.TargetingPack | Pacote de direcionamento do .NET Framework 4.7 | 15.0.26621.2 | Opcional
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | Ferramentas de desenvolvimento do .NET Framework 4.6.2 | 15.0.26621.2 | Opcional
Microsoft.Net.ComponentGroup.4.7.1.DeveloperTools | Ferramentas de desenvolvimento do .NET Framework 4.7.1 | 15.0.27019.1 | Opcional
Microsoft.Net.ComponentGroup.4.7.DeveloperTools | Ferramentas de desenvolvimento do .NET Framework 4.7 | 15.0.27005.2 | Opcional

## <a name="unaffiliated-components"></a>Componentes não afiliados

Estes são os componentes que não são incluídos com nenhuma carga de trabalho, mas que podem ser selecionados como um componente individual.

ID do componente | Nome | Versão
--- | --- | ---
Microsoft.VisualStudio.Component.VC.Tools.14.11 | Conjunto de ferramentas do VC++ 2017 versão 15.4 v14.11 | 15.0.27128.1

## <a name="get-support"></a>Obter suporte
Às vezes, as coisas podem dar errado. Caso a instalação do Visual Studio falhe, confira a página [Solução de problemas de instalação e atualização do Visual Studio 2017](troubleshooting-installation-issues.md). Se nenhuma das etapas de solução de problemas ajudar, entre em contato conosco por meio de um chat ao vivo para obter ajuda com a instalação (somente em inglês). Para saber mais detalhes, confira a [página de suporte do Visual Studio](https://www.visualstudio.com/vs/support/#talktous).

Aqui estão algumas outras opções de suporte:
* Você pode nos relatar problemas do produto por meio da ferramenta [Relatar um Problema](../ide/how-to-report-a-problem-with-visual-studio-2017.md), exibida no Instalador do Visual Studio e no IDE do Visual Studio.
* Você pode compartilhar uma sugestão de produto conosco no [UserVoice](https://visualstudio.uservoice.com/forums/121579).
* É possível acompanhar os problemas do produto na [Comunidade de Desenvolvedores do Visual Studio](https://developercommunity.visualstudio.com/), além de fazer perguntas e encontrar respostas.
* Você pode também interagir conosco e com outros desenvolvedores do Visual Studio por meio das [conversas sobre o Visual Studio na comunidade do Gitter](https://gitter.im/Microsoft/VisualStudio).  (Esta opção requer uma conta do [GitHub](https://github.com/).)

## <a name="see-also"></a>Consulte também

* [Carga de trabalho do Visual Studio e IDs do componente](workload-and-component-ids.md)
* [Guia do administrador do Visual Studio](visual-studio-administrator-guide.md)
* [Usar parâmetros de linha de comando para instalar o Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
  * [Exemplos de parâmetro de linha de comando](command-line-parameter-examples.md)
* [Criar uma instalação offline do Visual Studio](create-an-offline-installation-of-visual-studio.md)
