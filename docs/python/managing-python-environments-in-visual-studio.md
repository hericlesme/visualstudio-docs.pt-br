---
title: Gerenciar ambientes e interpretadores Python
description: Use a janela Ambientes Python para gerenciar ambientes globais, virtuais e conda, para instalar interpretadores e pacotes Python e atribuir ambientes a projetos do Visual Studio.
ms.date: 03/21/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- python
- data-science
ms.openlocfilehash: f3a3fa14a2772171b2968514867d35ea4ad126f1
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-create-and-manage-python-environments-in-visual-studio"></a>Como criar e gerenciar ambientes Python no Visual Studio

Um *ambiente* Python é um contexto em que você executa o código Python e inclui ambientes globais, virtuais e conda. Um ambiente é composto por um interpretador, uma biblioteca (normalmente a Biblioteca Padrão do Python) e um conjunto de pacotes instalados. Juntos, esses componentes determinam quais constructos de linguagem e qual sintaxe são válidos, qual funcionalidade do sistema operacional pode ser acessada e quais pacotes podem ser usados.

No Visual Studio no Windows, a janela [Ambientes Python](#managing-python-environments-in-visual-studio), conforme descrito neste artigo, é onde você gerencia esses ambientes e seleciona um como padrão para novos projetos. Para qualquer projeto, você também pode selecionar um ambiente específico, em vez de usar o padrão.

**Observação**: se você for um novo usuário do Python no Visual Studio, veja os seguintes artigos para obter as informações necessárias:

- [Trabalhando com o Python no Visual Studio](overview-of-python-tools-for-visual-studio.md)
- [Instalando o suporte do Python no Visual Studio](installing-python-support-in-visual-studio.md)

Observe também que você não pode gerenciar ambientes para código Python abertos somente como uma pasta usando o comando **Arquivo > Abrir > Pasta**. Em vez disso, [Crie um projeto em Python com o código existente](quickstart-01-python-in-visual-studio-project-from-existing-code.md) para aproveitar os recursos do ambiente do Visual Studio.

Se você quiser instalar pacotes em um ambiente, veja a [guia Pacotes](python-environments-window-tab-reference.md#packages-tab).

## <a name="types-of-environments"></a>Tipos de ambientes

### <a name="global-environments"></a>Ambientes globais

Cada instalação do Python (por exemplo, Python 2.7, Python 3.6, Anaconda 4.4.0 etc., confira [Selecionar e instalar interpretadores Python](installing-python-interpreters.md)) mantém seu próprio ambiente global. Cada ambiente é composto pelo interpretador do Python específico, sua biblioteca padrão e por um conjunto de pacotes pré-instalados. A instalação de um pacote em um ambiente global o torna disponível para todos os projetos que usam esse ambiente. Se o ambiente estiver em uma área de proteção do sistema de arquivos (dentro de `c:\program files`, por exemplo), a instalação de pacotes exigirá privilégios de administrador.

Os ambientes globais estão disponíveis para todos os projetos no computador. No Visual Studio, selecione um ambiente global como o padrão, que é usado para todos os projetos, a menos que você escolha especificamente um diferente para um projeto. Para saber mais, confira [Selecionar um ambiente para um projeto](selecting-a-python-environment-for-a-project.md).

### <a name="virtual-environments"></a>Ambientes virtuais

Como os pacotes instalados em um ambiente global estão disponíveis para todos os projetos que usam esse ambiente, poderão ocorrer conflitos quando dois projetos exigirem pacotes incompatíveis ou versões diferentes do mesmo pacote. Ambientes virtuais evitam esses conflitos usando o interpretador e a biblioteca padrão de um ambiente global, mas mantêm seus próprios armazenamentos de pacote em pastas isolados.

No Visual Studio, é possível criar um ambiente virtual para um projeto específico, que é armazenado em uma subpasta no projeto. O Visual Studio fornece um comando para gerar um arquivo `requirements.txt` do ambiente virtual, tornando mais fácil recriar o ambiente em outros computadores. Para saber mais, confira [Usar ambientes virtuais](selecting-a-python-environment-for-a-project.md#using-virtual-environments).

### <a name="conda-environments"></a>Ambientes do Conda

Um ambiente do conda é criado usando a ferramenta `conda`. Os ambientes do Conda normalmente são armazenados na pasta `envs` dentro de uma instalação do Anaconda e, portanto, agem como os ambientes globais. Por exemplo, a instalação de um novo pacote em um ambiente do conda torna esse pacote disponível para todos os projetos que usam esse ambiente.

O Visual Studio não detecta automaticamente, no momento, ambientes do conda, mas você pode apontar manualmente o Visual Studio para ele. Confira [Identificar manualmente um ambiente existente](#manually-identifying-an-existing-environment).

## <a name="the-python-environments-window"></a>A janela Ambientes do Python

Os ambientes conhecidos pelo Visual Studio são exibidos na janela **Ambientes Python**. Para abrir a janela, use um dos seguintes métodos:

- Selecione o comando de menu **Exibir > Outras Janelas > Ambientes do Python**.
- Clique com o botão direito no nó **Ambientes do Python** de um projeto no Gerenciador de Soluções e selecione **Exibir Todos os Ambientes do Python**:

    ![Comando Exibir Todos os Ambientes no Gerenciador de Soluções](media/environments-view-all.png)

Em ambos os casos, a janela **Ambientes do Python** é exibida como uma guia irmã do Gerenciador de Soluções:

![Janela Ambientes do Python](media/environments-default-view.png)

A imagem acima mostra que o Visual Studio detectou duas instalações do Python 3.6 (32 bits) junto com o Anaconda 5.0.0.

O ambiente padrão em negrito é o Python 3.6 (nesse caso, parte de uma instalação do Anaconda), que usa o Visual Studio para quaisquer projetos novos. Os comandos na parte inferior da janela se aplicam ao interpretador do Python 3.6 selecionado, que, como você pode ver, é a instalação específica no `C:\Python36-32`. Se você não vir um ambiente esperado, confira [Identificar manualmente um ambiente existente](#manually-identifying-an-existing-environment).

À direita de cada ambiente listado está um controle que abre uma janela interativa para esse ambiente. Outro controle pode parecer que atualiza o banco de dados do IntelliSense para esse ambiente (veja [Referência da janela de ambientes](python-environments-window-tab-reference.md#intellisense-tab) para obter detalhes sobre o banco de dados).

Abaixo da lista de ambientes há um seletor de lista suspensa para as opções **Visão geral**, **Pacotes** e **IntelliSense** descritas em [Referência à guia da janela Ambientes](python-environments-window-tab-reference.md). Além disso, se você expandir a janela **Ambientes do Python** até o tamanho suficiente, essas opções serão mostradas como guias, o que talvez você considere mais conveniente para trabalhar:

![Exibição expandida da janela Ambientes do Python](media/environments-expanded-view.png)

> [!Note]
> Embora o Visual Studio respeite a opção de pacotes de site do sistema, ele não fornece uma maneira de alterá-lo no próprio Visual Studio.

|   |   |
|---|---|
| ![ícone de câmera para vídeo](../install/media/video-icon.png "Assistir a um vídeo") | [Assista a um vídeo (Microsoft Virtual Academy)](https://mva.microsoft.com/en-US/training-courses/python-tools-for-visual-studio-2017-18121?l=qrDmN4LWE_8305918567) sobre os ambientes do Python no Visual Studio (2min35s).|

### <a name="what-if-no-environments-appear"></a>E se nenhum ambiente aparecer?

Se nenhum ambiente aparecer, isso significa que o Visual Studio não conseguiu detectar as instalações de Python nos locais padrão. Por exemplo, você pode ter instalado o Visual Studio 2017 mas limpou todas as opções de interpretador nas opções do instalador para a carga de trabalho do Python. Da mesma forma, você pode ter instalado o Visual Studio 2015 ou anterior, mas não instalou um interpretador manualmente (confira [Como instalar interpretadores Python](installing-python-interpreters.md)).

Se você souber que tem um intérprete Python em seu computador, mas o Visual Studio (qualquer versão) não detectá-lo, use o comando **+Personalizado...**  para especificar o local manualmente. Confira a próxima seção, [Identificar manualmente um ambiente existente](#manually-identifying-an-existing-environment).

> [!Tip]
> O Visual Studio detecta atualizações para um interpretador existente, como a atualização do Python 2.7.11 para 2.7.14 usando os instaladores de python.org. Durante o processo de instalação, o ambiente mais antigo desaparece da lista **Ambientes Python** antes de a atualização aparecer em seu lugar.
>
> No entanto, se você mover manualmente um interpretador e seu ambiente usando o sistema de arquivos, o Visual Studio não saberá o novo local. Para saber mais, veja [Mover um intérprete](installing-python-interpreters.md#moving-an-interpreter).

## <a name="manually-identifying-an-existing-environment"></a>Identificar manualmente um ambiente existente

Use as etapas a seguir para identificar um ambiente que está instalado em um local não padrão, incluindo ambientes do conda:

1. Selecione **+Personalizado...**  na janela **Ambientes Python**, que abre a guia **Configurar**:

    ![Exibição padrão de um novo ambiente personalizado](media/environments-custom-1.png)

1. Insira um nome para o ambiente no campo **Descrição**.

1. Insira ou procure (usando **...***) o caminho do interpretador no campo **Caminho do prefixo**.

1. Se o Visual Studio detectar um interpretador Python nessa localização (como o caminho mostrado abaixo para um ambiente de conda), ele habilitará o comando **Detecção Automática**. Selecionar **Detecção Automática* preenche os campos restantes. Você também pode preencher esses campos manualmente.

    ![Habilitar o comando Detecção Automática](media/environments-custom-2.png)

    ![Preenchimento dos campos de ambiente depois de usar a Detecção Automática](media/environments-custom-3.png)

1. Quando os campos contiverem os valores desejados, selecione **Aplicar** para salvar a configuração. Agora, você pode usar o ambiente como qualquer outro no Visual Studio.

1. Se você precisar remover um ambiente identificado manualmente, selecione o comando **Remover** na guia **Configurar**. Ambientes detectados automaticamente não oferecem essa opção. Para saber mais, confira [Guia Configurar](python-environments-window-tab-reference.md#configure-tab).

## <a name="see-also"></a>Consulte também

- [Instalar interpretadores do Python](installing-python-interpreters.md)
- [Selecionar um intérprete para um projeto](selecting-a-python-environment-for-a-project.md)
- [Usando requirements.txt para dependências](managing-required-packages-with-requirements-txt.md)
- [Caminhos de pesquisa](search-paths.md)
- [Referência à janela Ambientes do Python](python-environments-window-tab-reference.md)