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
ms.openlocfilehash: 78e9245df26a2de747414a91b9024fde9325ef22
ms.sourcegitcommit: 67374acb6d24019a434d96bf705efdab99d335ee
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/22/2018
---
# <a name="visual-studio-2017-productivity-guide-for-net-developers"></a>Guia de produtividade do Visual Studio 2017 para Desenvolvedores do .NET

O [Visual Studio de 2017](https://www.visualstudio.com/downloads/) faz com que os desenvolvedores alcancem uma produtividade inédita! Melhoramos o desempenho e a confiabilidade na inicialização e carregamento da solução, na detecção de teste e na latência de digitação. Também adicionamos e melhoramos os recursos para ajudá-lo a escrever códigos mais rapidamente. Alguns desses recursos incluem: navegação para assemblies descompiladas, sugestões de nomes de variáveis conforme você digita, um modo de exibição de hierarquia no Gerenciador de Testes, Ir para Todos (**Ctrl+T**) para navegar até as declarações de arquivo/tipo/membro/símbolo, um Auxiliar de Exceção inteligente, configuração e imposição de estilo de código e muitas correções de código e refatorações. 

Siga este guia para otimizar sua produtividade.

##  <a name="im-used-to-my-keyboard-shortcuts-from-a-different-extensioneditoride"></a>Estou acostumado aos meus atalhos de teclado de uma extensão/editor/IDE diferente.

Se estiver vindo de outro ambiente de codificação ou IDE, a instalação de uma das seguintes extensões poderá ser útil a você:

- [Emulação de Emacs](https://marketplace.visualstudio.com/items?itemName=JustinClareburtMSFT.EmacsEmulation)
- [Teclas de acesso para Visual Studio (ReSharper/IntelliJ)](https://marketplace.visualstudio.com/items?itemName=JustinClareburtMSFT.HotKeys)
- [VSVim](https://marketplace.visualstudio.com/items?itemName=JaredParMSFT.VsVim)

![A galeria de extensões do Visual Studio](../ide/media/VSIDE_Productivity_Extensibility.png)

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

## <a name="i-need-a-way-to-quickly-navigate-to-files-or-types"></a>Preciso de uma maneira para navegar rapidamente nos arquivos ou tipos.
O Visual Studio 2017 tem um recurso chamado _Ir para Todos_ (**Ctrl + T**). Ir para Todos permite que você acesse rapidamente qualquer declaração de arquivo, tipo, membro ou símbolo.
- Altere a localização desta barra de pesquisa ou desative a "visualização de navegação dinâmica" com o ícone **engrenagem**
- Filtre os resultados usando nossa sintaxe de consulta (por exemplo, "t mytype"). Você também pode definir o escopo da pesquisa somente para o documento atual.
- Há suporte para a correspondência de camelCase!

![Ir para todos no Visual Studio](../ide/media/VS2017Guide-go-to-all.png)

## <a name="my-team-enforces-code-style-rules-on-our-codebase"></a>Minha equipe impõe regras de estilo de código em nossa base de código.
Você pode usar um arquivo .editorconfig para codificar as convenções de codificação. É recomendável instalar a [extensão Serviços de Linguagem EditorConfig](https://aka.ms/editorconfig) para adicionar e editar um arquivo .editorconfig. É recomendável fazer check-out da [documentação](https://aka.ms/editorconfigDocs) para todas as opções de convenção de codificação .NET.

Confira [este gist](https://gist.github.com/kuhlenh/5471666a7a2c57fea427e81cf0a41da8) para obter um exemplo de .editorconfig.

![Imposição de estilo de código no Visual Studio](../ide/media/VSGuide_CodeStyle.png)

## <a name="i-need-more-refactorings-and-code-fixes"></a>Preciso de mais correções de código e refatorações.
O Visual Studio 2017 vem com muitas ações de geração de código, refatorações e correções de códigos, que podem ser visualizadas na nossa [documentação](https://aka.ms/refactorings). As linhas onduladas vermelhas representam erros, as linhas onduladas verdes representam avisos e os três pontos cinzas representam sugestões de código.

Você pode acessar as correções de código clicando no ícone de lâmpada/chave de fenda ou pressionando **Ctrl +.** ou **Alt+Enter**. Cada correção vem com uma janela de visualização que mostra a diferença do código em tempo real de como a correção funciona.

Aqui estão algumas correções e refatorações rápidas comuns: *Renomear*, *Extrair método*, *Alterar assinatura do método*, *Gerar construtor*, *Gerar método*, *Mover tipo para arquivo*, *Adicionar verificação de nulo*, *Adicionar parâmetro*, *Remover usos desnecessários*.

As correções de código e as refatorações podem ser facilmente escritas com [analisadores Roslyn](https://github.com/dotnet/roslyn/wiki/Getting-Started-Writing-a-Custom-Analyzer-&-Code-Fix). Vários membros da comunidade escreveram extensões *gratuitas* que adicionam inspeções de código adicionais: [Roslynator](https://marketplace.visualstudio.com/items?itemName=josefpihrt.Roslynator2017), [SonarLint para Visual Studio](https://marketplace.visualstudio.com/items?itemName=SonarSource.SonarLintforVisualStudio2017) e [StyleCopAnalyzers](https://www.nuget.org/packages/stylecop.analyzers/). 

![Refatorações no Visual Studio](../ide/media/VSGuide_CodeAnalysis.png "VSGuide_CodeAnalysis")

## <a name="i-need-find-usages-go-to-implementation-navigate-to-decompiled-assemblies"></a>Preciso Localizar Usos, Ir Para Implementação, Navegar para Assemblies Descompiladas
O Visual Studio 2017 tem muitos recursos para ajudá-lo a pesquisar e navegar na base de código, incluindo Localizar Todas as Referências (**Shift+F12**), Ir para Implementação (**Ctrl+F12**), Ir para Definição ( **F12** ou **Ctrl+Clique**). Fizemos vários aprimoramentos nestes recursos no VS2017, por exemplo, Localizar Todas as Referências agora é colorido e permite o agrupamento personalizado. *Navegar para Assemblies Descompilados* em Ir para definição foi adicionado na versão 15.6. Para ativar esse recurso, vá para **Ferramentas > Opções > Editor de Texto > C# > Avançado > Habilitar navegação para códigos-fonte descompilados**.

Outras ferramentas de navegação comuns incluem: Inspecionar Definição (**Alt + F12**), o Visualizador de estrutura (linhas pontilhadas entre chaves focalizáveis) e [muito mais](../ide/navigating-code.md).

![Ir para Todos e Localizar Todas as Referências](../ide/media/VSIDE_Productivity_Navigation.png)

## <a name="i-want-to-run-and-see-my-unit-tests"></a>Preciso executar e ver meus testes de unidade.
Há duas ofertas para teste de unidade no Visual Studio de 2017: o Gerenciador de Testes e o _Live Unit Testing_ (ambos são compatíveis com MSTest v1, MSTest v2, NUnit e XUnit). Nós melhoramos significativamente a velocidade da detecção de testes no Gerenciador de Testes na versão 15.6 (para obter melhores resultados, atualize para a versão mais recente do adaptador de teste). Também reformulamos a interface do usuário para permitir a classificação hierárquica.

O Visual Studio 2017 Enterprise também tem uma recurso de teste de unidade chamado [Live Unit Testing](../test/live-unit-testing.md). O Live Unit Testing é executado continuamente em segundo plano, executa os testes afetados pela sua alteração de código e atualiza os ícones de editor embutido para informar o status dos seus testes.

![Exibição de hierarquia do Gerenciador de Testes no Visual Studio](../ide/media/VSGuide_Testing.png)

## <a name="i-want-to-debug-my-code"></a>Quero depurar meu código.
Nós adicionamos inúmeros recursos de depuração novos no Visual Studio 2017. *Executar até o clique* permite que você passe o mouse ao lado de uma linha de código, pressione o ícone verde 'executar' que é exibido e execute o programa até atingir essa linha. O novo *Auxiliar de Exceção* coloca as informações mais importantes, como qual variável é 'nula' em uma NullReferenceException, na parte superior da caixa de diálogo. E [Retroceder](../debugger/how-to-use-intellitrace-step-back.md) a depuração permite voltar para os pontos de interrupção ou para as etapas anteriores e exibir o estado do aplicativo como ele estava anteriormente.

Se você tiver recursos no Azure, use [Depuração de Instantâneo](/azure/application-insights/app-insights-snapshot-debugger) para investigar o estado de um aplicativo Web em tempo real no momento em que uma exceção foi gerada.

![Novo auxiliar de exceção no VS2017](../ide/media/VSGuide_Debugging.png "VSGuide_Debugging")

## <a name="i-want-to-use-version-control-with-my-projects"></a>Desejo usar o controle de versão com meus projetos.
Você pode usar o Git ou o TFVC para armazenar e atualizar seu código no Visual Studio. No editor, organize as alterações locais com o Team Explorer e use a barra de status para acompanhar confirmações e alterações pendentes. Configure a integração e a entrega contínuas de seus projetos no Visual Studio com a extensão [Ferramentas de Entrega Contínua para Visual Studio](https://marketplace.visualstudio.com/items?itemName=VSIDEDevOpsMSFT.ContinuousDeliveryToolsforVisualStudio) para adotar um fluxo de trabalho de desenvolvedor Agile.

![Controle do código-fonte no Visual Studio](../ide/media/VSIDE_Productivity_SourceControl.png)

## <a name="what-other-features-do-i-need-to-know-about"></a>Quais outros recursos que preciso conhecer?
Aqui está uma lista dos recursos do editor e de produtividade para escrever códigos com mais eficiência. Pode ser necessário ativar alguns recursos, pois eles ficam desativado por padrão (eles podem indexar itens em sua máquina, são controversos ou atualmente são experimentais).
- *Localizar o Arquivo no Gerenciador de Soluções* realça o arquivo ativo no Gerenciador de Soluções.
  - **Ferramentas > Opções > Projetos e Soluções > Acompanhar Item Ativo no Gerenciador de Soluções**
- *Adicionar usos para tipos em assemblies de referência e pacotes do NuGet* mostra uma lâmpada com uma correção de código para instalar um pacote do NuGet para um tipo não referenciado.
  - **Ferramentas > Opções > Editor de Texto > C# > Avançado > Sugerir usos para tipos em assemblies de referência** e **Sugerir usos para tipos em pacotes NuGet**
- *Habilitar análise de solução completa* para ver todos os erros em sua solução na Lista de Erros.
  - **Ferramentas > Opções > Editor de Texto > C# > Avançado > Habilitar análise de solução completa**
- *Habilitar navegação para fontes descompiladas* para habilitar Ir Para a Definição em tipos/membros de fontes externas e usar o descompilador ILSpy para mostrar os corpos de método.
  - **Ferramentas > Opções > Editor de Texto > C# > Avançado > Habilitar navegação para fontes descompiladas**
- *Modo de Sugestão/Conclusão* no IntelliSense muda o comportamento de conclusão. Os desenvolvedores com experiência em IntelliJ tendem a alterar aqui a configuração do padrão.
  - **Menu > Editar > IntelliSense > Alternar Modo de Conclusão**
- *[CodeLens](../ide/find-code-changes-and-other-history-with-codelens.md)* exibe informações de referência de código e o histórico de alterações no editor.
  - **Ferramentas > Opções > Editor de Texto > Todas as Linguagens > CodeLens**
- Temos *trechos de código* para ajudar a criar um stub de texto clichê comum (pressione Tab duas vezes). Veja a [lista completa](../ide/visual-csharp-code-snippets.md).

![Trechos de código no Visual Studio](../ide/media/VSGuide_SmartEditor.png)

## <a name="missing-a-feature-that-makes-you-productive-or-experiencing-poor-performance"></a>Está faltando um recurso que melhora a sua produtividade ou está enfrentando um baixo desempenho?
Há várias maneiras de enviar comentários:
- Solicitações de recursos do .NET podem ser preenchidas em nosso [repositório GitHub](https://github.com/dotnet/roslyn/issues).
- As solicitações de recursos, os bugs e os problemas de desempenho do Visual Studio podem ser informados usando o ícone **Enviar Comentários** no canto superior direito da janela do Visual Studio.
