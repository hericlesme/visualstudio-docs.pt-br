---
title: Visual Studio 2017 para desenvolvedores do .NET | Microsoft Docs
description: Visão geral das funcionalidades Visual Studio 2017 para ajudá-lo a codificar mais rápido no .NET.
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
ms.openlocfilehash: 7e910c50682d45d209d993cb883ca01d1ea436f2
ms.sourcegitcommit: 236c250bb97abdab99d00c6525d106fc0035d7d0
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/17/2018
---
# <a name="visual-studio-2017-productivity-guide-for-net-developers"></a>Guia de produtividade do Visual Studio 2017 para Desenvolvedores do .NET

- [Guia de produtividade](#guide)
- [Visão geral do Visual Studio de 2017](#overview)

## <a name="a-idguide-productivity-guide"></a><a id="guide"/>Guia de produtividade
O [Visual Studio de 2017](https://www.visualstudio.com/downloads/) faz com que os desenvolvedores alcancem uma produtividade inédita! Melhoramos o desempenho e a confiabilidade na inicialização e carregamento da solução, na detecção de teste e na latência de digitação. Também adicionamos e melhoramos os recursos para ajudá-lo a escrever códigos mais rapidamente. Alguns desses recursos incluem: navegação para assemblies descompiladas, sugestões de nomes de variáveis conforme você digita, um modo de exibição de hierarquia no Gerenciador de Testes, Ir para Todos (**Ctrl+T**) para navegar até as declarações de arquivo/tipo/membro/símbolo, um Auxiliar de Exceção inteligente, configuração e imposição de estilo de código e muitas correções de código e refatorações. 

Siga este guia para otimizar sua produtividade.

###  <a name="im-used-to-my-keyboard-shortcuts-from-a-different-extensioneditoride"></a>Estou acostumado aos meus atalhos de teclado de uma extensão/editor/IDE diferente.

Se estiver vindo de outro ambiente de codificação ou IDE, a instalação de uma das seguintes extensões poderá ser útil a você:

- [Emulação de Emacs](https://marketplace.visualstudio.com/items?itemName=JustinClareburtMSFT.EmacsEmulation)
- [Teclas de acesso para Visual Studio (ReSharper/IntelliJ)](https://marketplace.visualstudio.com/items?itemName=JustinClareburtMSFT.HotKeys)
- [VSVim](https://marketplace.visualstudio.com/items?itemName=JaredParMSFT.VsVim)

Estes são os atalhos populares do Visual Studio. 

> [!NOTE]
> Algumas extensões desvinculam as associações de teclas padrão do Visual Studio, então, é necessário restaurá-las para usar os comandos a seguir. Para restaurar suas associações de teclas padrão do Visual Studio, vá para: **Ferramentas > Importar e Exportar Configurações... > Redefinir todas as configurações** ou **Ferramentas > Opções > Teclado > Redefinir**.

| Atalho (todos os perfis) | Comando | Descrição |
|-|-|-|
| **Ctrl+T** | Ir para Todos | Navegue diretamente para qualquer declaração de arquivo/tipo/membro/símbolo |
| **F12** (também **Ctrl+Clique**) | Ir para definição | Vá até onde um símbolo estiver definido |
| **Ctrl+F12** | Ir Para Implementação | Navegue de um membro ou tipo base até suas várias implementações |
| **Shift+F12** | Localizar Todas as Referências | Veja todas as referências de símbolo ou de literal |
| **Ctrl**+**.** (também **ALT+ENTER** no Perfil C#) | Ações e Refatorações Rápidas | Veja quais correções de código, ações de geração de código, refatorações ou outras ações rápidas estão disponíveis na posição do cursor ou na seleção do código |
| **Ctrl**+**D** | Duplicar linha | Duplica a linha de código onde o cursor está posicionado (disponível no **Visual Studio 2017 versão 15.6** e posterior) |
| **Shift**+**Alt**+**+**/**-** | Expandir/Reduzir seleção | Expande ou reduz a seleção atual no editor (disponível no **Visual Studio 2017 versão 15.5** e posteriores) |
| **Ctrl+Q** | Início Rápido | Pesquise todas as configurações do Visual Studio |
| **F5** | Iniciar a depuração | Inicie a depuração do aplicativo |
| **Ctrl+F5** | Executar sem Depurar | Execute o aplicativo localmente sem depuração |
| **Ctrl+K, D** (Perfil Padrão) ou **Ctrl+E, D** (Perfil C#) | Formatar Documento | Limpe as violações de formatação de um arquivo com base nas configurações de nova linha, de espaçamento e de recuo |
| **Ctrl+\\E** (Perfil Padrão) ou **Ctrl+W, E** (Perfil C#) | Exibir Lista de Erros | Veja todos os erros no documento, no projeto ou na solução |

### <a name="i-need-a-way-to-quickly-navigate-to-files-or-types"></a>Preciso de uma maneira para navegar rapidamente nos arquivos ou tipos.
O Visual Studio 2017 tem um recurso chamado _Ir para Todos_ (**Ctrl + T**). Ir para Todos permite que você acesse rapidamente qualquer declaração de arquivo, tipo, membro ou símbolo.
- Altere a localização desta barra de pesquisa ou desative a "visualização de navegação dinâmica" com o ícone **engrenagem**
- Filtre os resultados usando nossa sintaxe de consulta (por exemplo, "t mytype"). Você também pode definir o escopo da pesquisa somente para o documento atual.
- Há suporte para a correspondência de camelCase!

![Ir para Todos no Visual Studio](../ide/media/VS2017Guide-go-to-all.png "VS2017Guide-go-to-all")

### <a name="my-team-enforces-code-style-rules-on-our-codebase"></a>Minha equipe impõe regras de estilo de código em nossa base de código.
Você pode usar um arquivo .editorconfig para codificar as convenções de codificação. É recomendável instalar a [extensão Serviços de Linguagem EditorConfig](https://aka.ms/editorconfig) para adicionar e editar um arquivo .editorconfig. É recomendável fazer check-out da [documentação](https://aka.ms/editorconfigDocs) para todas as opções de convenção de codificação .NET.

Faça o check-out [deste gist](https://gist.github.com/kuhlenh/5471666a7a2c57fea427e81cf0a41da8) como um exemplo de arquivo .editorconfig.

![Imposição de estilo de código no Visual Studio](../ide/media/VS2017Guide-code-style.png "VS2017Guide-code-style")

### <a name="i-need-more-refactorings-and-code-fixes"></a>Preciso de mais correções de código e refatorações.
O Visual Studio 2017 vem com muitas ações de geração de código, refatorações e correções de códigos, que podem ser visualizadas na nossa [documentação](https://aka.ms/refactorings). As linhas onduladas vermelhas representam erros, as linhas onduladas verdes representam avisos e os três pontos cinzas representam sugestões de código.

Você pode acessar as correções de código clicando no ícone de lâmpada/chave de fenda ou pressionando **Ctrl +.** ou **Alt+Enter**. Cada correção vem com uma janela de visualização que mostra a diferença do código em tempo real de como a correção funciona.

Estas são algumas refatorações e correções rápidas e populares: Renomear, Extrair Método, Alterar Assinatura do Método, Gerar Construtor, Gerar Método, Mover Tipo para o Arquivo, Adicionar Verificação Nula, Adicionar Parâmetro, Remover Usos Desnecessários.

As correções de código e as refatorações podem ser facilmente escritas com [analisadores Roslyn](https://github.com/dotnet/roslyn/wiki/Getting-Started-Writing-a-Custom-Analyzer-&-Code-Fix). Vários membros da comunidade escreveram extensões *gratuitas* que adicionam inspeções de código adicionais: Roslynator e SonarLint para o Visual Studio. 

![Refatorações no Visual Studio](../ide/media/VS2017Guide-refactoring.png "VS2017Guide-refactoring")

### <a name="i-need-find-usages-go-to-implementation-navigate-to-decompiled-assemblies"></a>Preciso Localizar Usos, Ir Para Implementação, Navegar para Assemblies Descompiladas
O Visual Studio 2017 tem muitos recursos para ajudá-lo a pesquisar e navegar na base de código, incluindo Localizar Todas as Referências (**Shift+F12**), Ir para Implementação (**Ctrl+F12**), Ir para Definição ( **F12** ou **Ctrl+Clique**). Navegar para Assemblies Descompiladas foi adicionado na versão 15.6. Para ativar esse recurso, vá para **Ferramentas > Opções > Editor de Texto > C# > Avançado > Habilitar navegação para códigos-fonte descompilados**.

![Navegue até as fontes descompiladas no Visual Studio](../ide/media/VS2017Guide-navigate-to-source.png "VS2017Guide-navigate-to-source")

### <a name="i-want-to-run-and-see-my-unit-tests"></a>Preciso executar e ver meus testes de unidade.
Temos duas ofertas para teste de unidade no Visual Studio 2017: o Gerenciador de testes e o _Live Unit Testing_. Melhoramos significativamente a velocidade da detecção de testes do Gerenciador de Testes na versão 15.6. Também reformulamos a interface do usuário para permitir a classificação hierárquica.

O Visual Studio também tem o recurso de teste de unidade chamado [Live Unit Testing](/test/live-unit-testing). O Live Unit Testing é executado continuamente em segundo plano, executa os testes afetados pela sua alteração de código e atualiza os ícones de editor embutido para informar o status dos seus testes.

![Modo de exibição da hierarquia do Gerenciador de Testes no Visual Studio](../ide/media/VS2017Guide-hiearchy-test-explorer.png "VS2017Guide-hiearchy-test-explorer")

### <a name="what-other-features-do-i-need-to-know-about"></a>Quais outros recursos que preciso conhecer?
Aqui está uma lista dos recursos do editor e de produtividade para escrever códigos com mais eficiência. Pode ser necessário ativar alguns recursos, pois eles ficam desativado por padrão (eles podem indexar itens em sua máquina, são controversos ou atualmente são experimentais).
- *Localizar o Arquivo no Gerenciador de Soluções* realça o arquivo ativo no Gerenciador de Soluções.
  - **Ferramentas>Opções>Projetos e Soluções>Controlar Item Ativo no Gerenciador de Soluções**
- *Adicionar usos para tipos em assemblies de referência e pacotes do NuGet* mostra uma lâmpada com uma correção de código para instalar um pacote do NuGet para um tipo não referenciado.
  - **Ferramentas>Opções>Editor de Texto>C#>Avançado>Sugerir usos para tipos nos assemblies de referência** e **Sugerir usos para tipos nos pacotes NuGet**
- *Habilitar análise de solução completa* para ver todos os erros em sua solução na Lista de Erros.
  - **Ferramentas>Opções>Editor de Texto>C#>Avançado>Habilitar análise de solução completa**
- *Habilitar navegação para fontes descompiladas* para habilitar Ir Para a Definição em tipos/membros de fontes externas e usar o descompilador ILSpy para mostrar os corpos de método.
  - **Ferramentas>Opções>Editor de Texto>C#>Avançado>Habilitar navegação para fontes descompiladas**
- *Modo de Sugestão/Conclusão* no IntelliSense muda o comportamento de conclusão. Os desenvolvedores com experiência em IntelliJ tendem a alterar aqui a configuração do padrão.
  - **Menu > Editar > IntelliSense -> Ativar/Desativar Modo de Conclusão**
- Temos *trechos de código* para ajudar a criar um stub de texto clichê comum (pressione Tab duas vezes). Veja a [lista completa](/ide/visual-csharp-code-snippets).

![Trechos de código no Visual Studio](../ide/media/VS2017Guide-code-snippet.png "VS2017Guide-code-snippet")

### <a name="missing-a-feature-that-makes-you-productive-or-experiencing-poor-performance"></a>Está faltando um recurso que melhora a sua produtividade ou está enfrentando um baixo desempenho?
Há várias maneiras de enviar comentários:
- Solicitações de recursos do .NET podem ser preenchidas em nosso [repositório GitHub](https://github.com/dotnet/roslyn/issues).
- As solicitações sobre recursos, os bugs e os problemas de desempenho no Visual Studio podem ser preenchidos usando o ícone **Enviar Comentários** no canto superior da janela do Visual Studio.


## <a name="a-idoverview-overview-of-visual-studio-2017-for-net-developers"></a><a id="overview"/> Visão geral do Visual Studio 2017 para Desenvolvedores do .NET

### <a name="smart-code-editor"></a>Editor de códigos inteligente

- [Documentação: Usando o IntelliSense](using-intellisense.md)
- [Documentação: Funcionalidades do editor inteligente](writing-code-in-the-code-and-text-editor.md)

O Visual Studio apresenta um entendimento profundo do código por meio do compilador .NET (“Roslyn”) para fornecer recursos de edição inteligente, como aplicação de cores na sintaxe, preenchimento de código, verificação ortográfica de variáveis digitadas incorretamente, resolução de tipo não importado, estrutura de tópicos, visualizadores de estrutura, [CodeLens](find-code-changes-and-other-history-with-codelens.md), hierarquia de chamadas, informações rápidas ao focalizar, ajuda de parâmetro, bem como ferramentas para refatoração, aplicação de ações rápidas e geração de código.

![Editor de código inteligente do Visual Studio](../ide/media/VSIDE_Productivity_SmartCodeEditor.png "VSIDE_Productivity_SmartCodeEditor")

### <a name="navigate-and-search-your-codebase"></a>Navegue e pesquise a base de código

[Documentação: Navegação pelo código](navigating-code.md)

Navegue rapidamente pelo código .NET indo para qualquer arquivo, tipo, membro ou declaração de símbolo com o atalho *Ir para Todos* (**Ctrl+T**). Encontre todas as referências de um símbolo ou literal no código, incluindo referências em linguagens .NET (**Shift+F12**). Use os comandos de navegação direcionados para ir diretamente às definições de símbolo (**F12**) ou implementações (**Ctrl+F12**).

![Ir para Todas e Localizar Todas as Referências](../ide/media/VSIDE_Productivity_Navigation.png "VSIDE_Productivity_Navigation")

### <a name="live-code-analysis-for-code-quality"></a>Análise de código dinâmica para qualidade do código

[Documentação: Refatorações e ações rápidas](refactoring-code-generation-quick-actions.md)

O Visual Studio oferece diagnóstico dinâmico de código para ajudar você a melhorar a qualidade do código detectando erros e possíveis problemas no código. Fornecemos ações rápidas (**Ctrl**+**.**) para resolver os problemas detectados em documentos, projetos ou soluções. Habilite a *análise da solução completa* para encontrar problemas na solução inteira, mesmo sem os arquivos abertos no editor.

Além disso, use as sugestões de código para conhecer as melhores práticas, fazer stub ou gerar código, refatorar o código e adotar novos recursos de linguagem com o atalho **Ctrl**+**.** atalho.

![Aplicar correções rápidas e refatorações usando o menu de lâmpada](../ide/media/VSIDE_Productivity_CodeAnalysis.png "VSIDE_Productivity_CodeAnalysis")

### <a name="unit-testing"></a>Teste de unidade

[Documentação: Teste de unidade no Visual Studio](../test/improve-code-quality.md)

Execute e depure os testes de unidade com base nas estruturas de teste MSTest, NUnit ou XUnit para qualquer aplicativo direcionado ao .NET Framework, ao .NET Standard ou ao .NET Core. Explore e examine os testes no *Gerenciador de Testes* ou veja imediatamente como as alterações no código afetam os testes de unidade no editor com o *Live Unit Testing* (somente em SKU do Enterprise).

![Live Unit Testing no Visual Studio](../ide/media/VSIDE_Productivity_LiveUnitTesting.png "VSIDE_Productivity_LiveUnitTesting")

### <a name="code-consistency-and-style"></a>Coerência e estilo do código

- [Documentação: Opções do editor personalizado portátil](create-portable-custom-editor-options.md)
- [Documentação: Configurações de estilo de código do EditorConfig para .NET](editorconfig-code-style-settings-reference.md)

O Visual Studio permite a configuração de convenções de codificação, detecta violações de estilo de codificação e fornece correções rápidas para solucionar problemas de estilo com o **Ctrl**+**.** atalho. Configure e imponha as convenções de formatação, de nomenclatura e de estilo de código da sua equipe em um repositório (permitindo a substituição de valores em nível de arquivo e de projeto) usando o *EditorConfig*.

![Configurar e impor as convenções de codificação com o EditorConfig](../ide/media/VSIDE_Productivity_CodeStyle.png "VSIDE_Productivity_CodeStyle")

### <a name="debugging"></a>Depuração

[Documentação: Depurando no Visual Studio](../debugger/index.md)

O Visual Studio inclui um depurador excelente que permite depurar os aplicativos .NET direcionados ao .NET Framework, ao .NET Standard e ao .NET Core. Ative/desative e defina os pontos de interrupção condicionais (**F9**), intervenha nas chamadas de método, avalie expressões e lambda e LINQ, defina inspeções de variáveis, reconecte-se a processos, examine a pilha de chamadas ou até mesmo faça edições dinâmicas de código durante a depuração com *Editar e Continuar*.

Se seu serviço for executado no Azure, use a *Depuração de instantâneo* para diagnosticar de maneira dinâmica problemas em aplicativos de nuvem implantados no Visual Studio 2017 Enterprise.

![Depuração no Visual Studio](../ide/media/VSIDE_Productivity_Debugging.png "VSIDE_Productivity_Debugging")

### <a name="version-control"></a>Controle de versão

[Documentação: Controle de versão no Visual Studio](/vsts/index)

Use GIT ou TFVC para armazenar e atualizar código no Visual Studio. No editor, organize as alterações locais com o Team Explorer e use a barra de status para acompanhar confirmações e alterações pendentes. Configure a integração e a entrega contínua no Visual Studio com nossa extensão [Ferramentas de Entrega Contínua para Visual Studio](https://marketplace.visualstudio.com/items?itemName=VSIDEDevOpsMSFT.ContinuousDeliveryToolsforVisualStudio) para adotar um fluxo de trabalho de desenvolvedor Agile.

![Controle do código-fonte no Visual Studio](../ide/media/VSIDE_Productivity_SourceControl.png "VSIDE_Productivity_SourceControl")

### <a name="extensibility"></a>Extensibilidade

[Documentação: Estendendo o Visual Studio](../extensibility/index.md)

O Visual Studio tem um ecossistema de extensões rico que você pode instalar ou criar conforme necessário. Instale as extensões da *Galeria de Extensões* ou do *Visual Studio Marketplace*, compile seu próprio plug-in de editor com o *SDK do VS* ou crie seu próprio analisador de código dinâmico ou refatoração usando a *Plataforma do Compilador .NET SDK*. Você pode encontrar correções adicionais de código e sugestões baixando a extensão [Análise de Código Microsoft](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.MicrosoftCodeAnalysis2017).

![A Galeria de Extensões do Visual Studio](../ide/media/VSIDE_Productivity_Extensibility.png "VSIDE_Productivity_Extensibility")
