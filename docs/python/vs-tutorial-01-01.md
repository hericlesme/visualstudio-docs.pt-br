---
title: Trabalhando com o Python no Visual Studio, etapa 1 | Microsoft Docs
ms.custom: 
ms.date: 09/26/2017
ms.reviewer: 
ms.suite: 
ms.technology: devlang-python
ms.devlang: python
ms.tgt_pltfrm: 
ms.topic: get-started-article
caps.latest.revision: "1"
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload: python
ms.openlocfilehash: adb49bb6070fee611a2ba67913943e68ee938d29
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="working-with-python-in-visual-studio"></a>Trabalhando com o Python no Visual Studio

O Python é uma linguagem de programação popular confiável, flexível, fácil de aprender, de uso gratuito em todos os sistemas operacionais e com suporte em uma sólida comunidade de desenvolvedores e várias bibliotecas gratuitas. A linguagem é compatível com todas as formas de desenvolvimento, incluindo aplicativos Web, serviços Web, aplicativos de área de trabalho, scripts e computação científica e, da mesma forma, é usada por diversas universidades, vários cientistas e desenvolvedores casuais e profissionais.

O Visual Studio fornece suporte de linguagem de primeira classe para o Python. Este tutorial orienta você nas seguintes etapas:

- [Etapa 0: instalação](vs-tutorial-01-00.md)
- [Etapa 1: criar um projeto do Python (este tópico)](#step-1-create-a-new-python-project)
- [Etapa 2: escrevendo e executando código para ver o IntelliSense do Visual Studio funcionando](vs-tutorial-01-02.md)
- [Etapa 3: criar mais código na janela REPL interativa](vs-tutorial-01-03.md)
- [Etapa 4: executar o programa concluído no depurador do Visual Studio](vs-tutorial-01-04.md)
- [Etapa 5: instalando pacotes e gerenciando ambientes do Python](vs-tutorial-01-05.md)
- [Etapa 6: trabalhando com Git](vs-tutorial-01-06.md)

## <a name="prerequisites"></a>Pré-requisitos

- Visual Studio 2017 com a carga de trabalho do Python instalada. Consulte a [Etapa 0](vs-tutorial-01-00.md) para obter instruções.

## <a name="step-1-create-a-new-python-project"></a>Etapa 1: criar um novo projeto do Python

Um *projeto* é a forma como o Visual Studio gerencia todos os arquivos que são reunidos para produzir um único aplicativo, incluindo código-fonte, recursos, configurações e assim por diante. Um projeto formaliza e mantém a relação entre todos os arquivos do projeto, bem como os recursos externos que são compartilhados entre vários projetos. Sendo assim, o projeto permite que seu aplicativo expanda facilmente e cresça de maneira muito mais fácil do que simplesmente gerenciar relacionamentos de um projeto em pastas ad-hoc, scripts, arquivos de texto e até mesmo em sua própria mente.

Neste tutorial você começará com um projeto simples, contendo um único arquivo de código vazio.

1. No Visual Studio, selecione **Arquivo > Novo > Projeto** (CTRL+SHIFT+N), que abrirá a caixa de diálogo **Novo Projeto**. Aqui você pode procurar modelos em diversas linguagens, selecionar um para o seu projeto e especificar o local em que o Visual Studio colocará os arquivos.

1. Para exibir modelos do Python, selecione **Instalado > Python** à esquerda ou pesquise por “Python”. O uso da pesquisa é uma ótima maneira de localizar um modelo quando você não se lembra da localização na árvore de linguagens.

    ![Nova caixa de diálogo mostrando os projetos do Python](media/vs-getting-started-python-01-new-project.png)

    Observe como o suporte do Python no Visual Studio inclui uma variedade de modelos de projeto, incluindo aplicativos Web usando as estruturas Bottle, Flask e Django. No entanto, para as finalidades deste passo a passo, vamos começar com um projeto vazio.

1. Selecione o modelo **Aplicativo Python**, especifique um nome para o projeto e selecione **OK**. 

1. Após alguns instantes, o Visual Studio mostrará a estrutura do projeto na janela **Gerenciador de Soluções** (1). O arquivo de código padrão será aberto no editor (2). A janela Propriedades (3) também será exibida para mostrar informações adicionais sobre qualquer item selecionado no Gerenciador de Soluções, incluindo sua localização exata no disco.

    ![Gerenciador de Soluções com um projeto do Python](media/vs-getting-started-python-02-windows.png)

1. Gaste alguns minutos para se familiarizar com o Gerenciador de Soluções, que é o local em que você poderá procurar arquivos e pastas em seu projeto.

    ![Gerenciador de Soluções expandido para mostrar vários recursos](media/vs-getting-started-python-03-solution-explorer.png)

    (1) O seu projeto está realçado em negrito, usando o nome que você forneceu na caixa de diálogo Novo Projeto. No disco, este projeto é representado por um arquivo `.pyproj` na pasta do projeto.

    (2) No nível superior está uma *solução* que, por padrão, tem o mesmo nome que o seu projeto. Uma solução, representada por um arquivo `.sln` no disco, é um contêiner para um ou mais projetos relacionados. Por exemplo, se você escreve uma extensão de C++ para o seu aplicativo Python, o projeto de C++ poderá residir na mesma solução. A solução também pode conter um projeto para um serviço Web, juntamente com projetos para programas de teste dedicados. 

    (3) Em seu projeto você vê os arquivos de origem, nesse caso, um único arquivo `.py`. Ao selecionar um arquivo, as respectivas propriedades são exibidas na janela Propriedades. Ao clicar duas vezes em um arquivo, ele será aberto da forma que for apropriada para esse arquivo.

    (4) Também no projeto está o nó **Ambientes do Python**. Quando expandido, você verá os interpretadores de Python disponíveis para você. Expanda um nó de interpretador para ver as bibliotecas que estão instaladas naquele ambiente (5).

    Clique com o botão direito do mouse em qualquer nó ou item no Gerenciador de Soluções para acessar um menu de comandos aplicáveis. Por exemplo, o comando **Renomear** permite que você altere o nome de qualquer nó ou item, incluindo o projeto e a solução.

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Escrevendo e executando um código](vs-tutorial-01-02.md)

## <a name="going-deeper"></a>Aprofundando-se

- [Projetos do Python no Visual Studio](python-projects.md).
- [Saiba mais sobre a linguagem Python em python.org](https://www.python.org)
- [Python para iniciantes](https://www.python.org/about/gettingstarted/) (python.org)
- [Cursos gratuitos do Python na Microsoft Virtual Academy](https://mva.microsoft.com/search/SearchResults.aspx#!q=python)
- [Top Python Questions (Principais perguntas sobre Python) na Microsoft Virtual Academy](https://aka.ms/mva-top-python-questions)
