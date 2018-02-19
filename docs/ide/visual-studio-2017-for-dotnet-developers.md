---
title: Visual Studio 2017 para desenvolvedores do .NET | Microsoft Docs
description: "Visão geral das funcionalidades Visual Studio 2017 para ajudá-lo a codificar mais rápido no .NET."
author: kuhlenh
ms.author: kaseyu
manager: ghogen
ms.technology: vs-ide-general
ms.date: 01/16/2018
ms.topic: article
helpviewer_keywords:
- editor
ms.workload:
- dotnet
ms.openlocfilehash: a834f9781ff51779b2216bd7de9dd3e449c9360a
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/09/2018
---
# <a name="visual-studio-2017-for-net-developers"></a>Visual Studio 2017 para desenvolvedores do .NET

## <a name="smart-code-editor"></a>Editor de códigos inteligente

[Documentação: Usando o IntelliSense](using-intellisense.md)  
[Documentação: Funcionalidades do editor inteligente](writing-code-in-the-code-and-text-editor.md)

O Visual Studio apresenta um entendimento profundo do código por meio do compilador .NET (“Roslyn”) para fornecer recursos de edição inteligente, como aplicação de cores na sintaxe, preenchimento de código, verificação ortográfica de variáveis digitadas incorretamente, resolução de tipo não importado, estrutura de tópicos, visualizadores de estrutura, [CodeLens](find-code-changes-and-other-history-with-codelens.md), hierarquia de chamadas, informações rápidas ao focalizar, ajuda de parâmetro, bem como ferramentas para refatoração, aplicação de ações rápidas e geração de código.

![Editor de código inteligente do Visual Studio](../ide/media/VSIDE_Productivity_SmartCodeEditor.png "VSIDE_Productivity_SmartCodeEditor")

## <a name="navigate-and-search-your-codebase"></a>Navegue e pesquise a base de código

[Documentação: Navegação pelo código](navigating-code.md)

Navegue rapidamente pelo código .NET indo para qualquer arquivo, tipo, membro ou declaração de símbolo com o atalho *Ir para Todos* (**Ctrl+T**). Encontre todas as referências de um símbolo ou literal no código, incluindo referências em linguagens .NET (**Shift+F12**). Use os comandos de navegação direcionados para ir diretamente às definições de símbolo (**F12**) ou implementações (**Ctrl+F12**).

![Ir para Todas e Localizar Todas as Referências](../ide/media/VSIDE_Productivity_Navigation.png "VSIDE_Productivity_Navigation")

## <a name="live-code-analysis-for-code-quality"></a>Análise de código dinâmica para qualidade do código

[Documentação: Refatorações e ações rápidas](refactoring-code-generation-quick-actions.md)

O Visual Studio oferece diagnóstico dinâmico de código para ajudar você a melhorar a qualidade do código detectando erros e possíveis problemas no código. Fornecemos ações rápidas (**Ctrl+.**) para resolver os problemas detectados em documentos, projetos ou soluções. Habilite a *análise da solução completa* para encontrar problemas na solução inteira, mesmo sem os arquivos abertos no editor.

Além disso, use as sugestões de código para conhecer as melhores práticas, fazer stub ou gerar código, refatorar o código e adotar novos recursos de linguagem com o atalho **Ctrl +.** atalho.

![Aplicar correções rápidas e refatorações usando o menu de lâmpada](../ide/media/VSIDE_Productivity_CodeAnalysis.png "VSIDE_Productivity_CodeAnalysis")

## <a name="unit-testing"></a>Teste de unidade

[Documentação: Teste de unidade no Visual Studio](../test/improve-code-quality.md)

Execute e depure os testes de unidade com base nas estruturas de teste MSTest, NUnit ou XUnit para qualquer aplicativo direcionado ao .NET Framework, ao .NET Standard ou ao .NET Core. Explore e examine os testes no *Gerenciador de Testes* ou veja imediatamente como as alterações no código afetam os testes de unidade no editor com o *Live Unit Testing* (somente em SKU do Enterprise). 

![Live Unit Testing no Visual Studio](../ide/media/VSIDE_Productivity_LiveUnitTesting.png "VSIDE_Productivity_LiveUnitTesting")

## <a name="code-consistency-and-style"></a>Coerência e estilo do código

[Documentação: Opções do editor personalizado portátil](create-portable-custom-editor-options.md)  
[Documentação: Configurações de estilo de código do EditorConfig para .NET](editorconfig-code-style-settings-reference.md)

O Visual Studio permite a configuração de convenções de codificação, detecta violações de estilo de codificação e fornece correções rápidas para solucionar problemas de estilo com o **Ctrl +.** atalho. Configure e imponha as convenções de formatação, de nomenclatura e de estilo de código da sua equipe em um repositório (permitindo a substituição de valores em nível de arquivo e de projeto) usando o *EditorConfig*.

![Configurar e impor as convenções de codificação com o EditorConfig](../ide/media/VSIDE_Productivity_CodeStyle.png "VSIDE_Productivity_CodeStyle")

## <a name="debugging"></a>Depuração

[Documentação: Depurando no Visual Studio](../debugger/index.md)

O Visual Studio inclui um depurador excelente que permite depurar os aplicativos .NET direcionados ao .NET Framework, ao .NET Standard e ao .NET Core. Ative/desative e defina os pontos de interrupção condicionais (**F9**), intervenha nas chamadas de método, avalie expressões e lambda e LINQ, defina inspeções de variáveis, reconecte-se a processos, examine a pilha de chamadas ou até mesmo faça edições dinâmicas de código durante a depuração com *Editar e Continuar*.

Se seu serviço for executado no Azure, use a *Depuração de instantâneo* para diagnosticar de maneira dinâmica problemas em aplicativos de nuvem implantados no Visual Studio 2017 Enterprise.

![Depuração no Visual Studio](../ide/media/VSIDE_Productivity_Debugging.png "VSIDE_Productivity_Debugging")

## <a name="version-control"></a>Controle de versão

[Documentação: Controle de versão no Visual Studio](/vsts/index)

Use GIT ou TFVC para armazenar e atualizar código no Visual Studio. No editor, organize as alterações locais com o Team Explorer e use a barra de status para acompanhar confirmações e alterações pendentes. Configure a integração e a entrega contínua no Visual Studio com nossa extensão [Ferramentas de Entrega Contínua para Visual Studio](https://marketplace.visualstudio.com/items?itemName=VSIDEDevOpsMSFT.ContinuousDeliveryToolsforVisualStudio) para adotar um fluxo de trabalho de desenvolvedor Agile.

![Controle do código-fonte no Visual Studio](../ide/media/VSIDE_Productivity_SourceControl.png "VSIDE_Productivity_SourceControl")

## <a name="extensibility"></a>Extensibilidade

[Documentação: Estendendo o Visual Studio](../extensibility/index.md)

O Visual Studio tem um ecossistema de extensões rico que você pode instalar ou criar conforme necessário. Instale as extensões da *Galeria de Extensões* ou do *Visual Studio Marketplace*, compile seu próprio plug-in de editor com o *SDK do VS* ou crie seu próprio analisador de código dinâmico ou refatoração usando a *Plataforma do Compilador .NET SDK*. Você pode encontrar correções adicionais de código e sugestões baixando a extensão [Análise de Código Microsoft](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.MicrosoftCodeAnalysis2017).

![A Galeria de Extensões do Visual Studio](../ide/media/VSIDE_Productivity_Extensibility.png "VSIDE_Productivity_Extensibility")

## <a name="popular-extensions--shortcuts"></a>Extensões populares e atalhos

Se estiver vindo de outro ambiente de codificação ou IDE, a instalação de uma das seguintes extensões poderá ser útil a você:

- [Emulação de Emacs](https://marketplace.visualstudio.com/items?itemName=JustinClareburtMSFT.EmacsEmulation )
- [Teclas de acesso para Visual Studio (ReSharper/IntelliJ)](https://marketplace.visualstudio.com/items?itemName=JustinClareburtMSFT.HotKeys)
- [VSVim](https://marketplace.visualstudio.com/items?itemName=JaredParMSFT.VsVim)

Estes são os atalhos populares do Visual Studio. Observe que algumas extensões desvinculam as associações de teclas padrão do Visual Studio e você deve restaurar essas associações para usar os comandos abaixo. Para redefinir suas associações de teclas padrão do Visual Studio, acesse **Ferramentas > Importar e exportar configurações... > Redefinir todas as configurações**.

| Atalho (todos os perfis) | Comando | Descrição |
|-|-|-|
| **Ctrl+T** | Ir para Todos | Navegue diretamente para qualquer declaração de arquivo/tipo/membro/símbolo |
| **F12** (também **Ctrl+Clique**) | Ir para definição | Vá até onde um símbolo estiver definido |
| **Ctrl+F12** | Ir Para Implementação | Navegue de um membro ou tipo base até suas várias implementações |
| **Shift+F12** | Localizar Todas as Referências | Veja todas as referências de símbolo ou de literal |
| **Ctrl+.** (também **ALT+ENTER** no Perfil C#) | Ações e Refatorações Rápidas | Veja quais correções de código, ações de geração de código, refatorações ou outras ações rápidas estão disponíveis na posição do cursor ou na seleção do código |
| **Ctrl**+**E**,**V** | Duplicar linha | Duplica a linha de código onde o cursor está posicionado (disponível no **Visual Studio 2017 versão 15.6 versão prévia 2** e posterior) |
| **Ctrl**+**W** | Expandir seleção | Expande a seleção atual em uma unidade estrutural (disponível no **Visual Studio 2017 versão 15.5**) |
| **Ctrl**+**Shift**+**W** | Seleção de contrato | Reduz (diminui) a seleção atual em uma unidade estrutural (disponível no **Visual Studio 2017 versão 15.5**) |
| **Ctrl+Q** | Início Rápido | Pesquise todas as configurações do Visual Studio |
| **F5** | Iniciar a depuração | Inicie a depuração do aplicativo |
| **Ctrl+F5** | Executar sem Depurar | Execute o aplicativo localmente sem depuração |
| **Ctrl+K, D** (Perfil Padrão) ou **Ctrl+E, D** (Perfil C#) | Formatar Documento | Limpe as violações de formatação de um arquivo com base nas configurações de nova linha, de espaçamento e de recuo |
| **Ctrl+\\E** (Perfil Padrão) ou **Ctrl+W, E** (Perfil C#) | Exibir Lista de Erros | Veja todos os erros no documento, no projeto ou na solução |