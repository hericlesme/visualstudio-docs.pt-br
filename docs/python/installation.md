---
title: "Instalação do Python no Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 09/22/2017
ms.reviewer: 
ms.suite: 
ms.technology: devlang-python
ms.devlang: python
ms.tgt_pltfrm: 
ms.topic: article
caps.latest.revision: "11"
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload: python
ms.openlocfilehash: a8136bd3e694ae544b176b8da6bfc2b721eb0c89
ms.sourcegitcommit: 5f436413bbb1e8aa18231eb5af210e7595401aa6
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2018
---
# <a name="installing-python-support-in-visual-studio-on-windows"></a>Instalando o suporte do Python no Visual Studio no Windows

Para instalar o suporte do Python para Visual Studio, siga as instruções da seção que corresponde à sua versão do Visual Studio:

- [Visual Studio 2017](#visual-studio-2017)
- [Visual Studio 2015](#visual-studio-2015)
- [Visual Studio 2013 e anterior](#visual-studio-2013-and-earlier)

Para o Visual Studio 2015 e anterior, também é necessário instalar separadamente um interpretador do Python de sua escolha (Python 3.5 e anterior; a versão 3.6 não é compatível e gerará a mensagem “Versão 3.6 do Python incompatível”). Para obter detalhes, consulte [Ambientes do Python](python-environments.md). A mesma página também contém instruções para adicionar um interpretador do Python existente ao Visual Studio 2017.

Para testar rapidamente o suporte do Python depois de seguir as etapas de instalação, abra a janela Interativa do Python pressionando Alt-I e inserindo `2+2`. Se você não vir a saída de `4`, verifique as etapas novamente.

> [!Tip]
> A carga de trabalho do Python inclui a extensão útil Cookiecutter, que fornece uma interface gráfica do usuário para descobrir modelos e opções de modelo de entrada e criar projetos e arquivos. Para obter detalhes, consulte [Usando o Cookiecutter](cookiecutter.md).

> [!Note]
> O suporte ao Python não está disponível atualmente no Visual Studio para Mac, mas está disponível no Mac e no Linux por meio do Visual Studio Code. Consulte [Perguntas e respostas](python-in-visual-studio.md#questions-and-answers).

## <a name="visual-studio-2017"></a>Visual Studio 2017

1. Baixe e execute o Instalador do Visual Studio 2017 mais recente:

    > [!div class="nextstepaction"]
    > <a target="frameTarget" href="https://www.visualstudio.com/thank-you-downloading-visual-studio/?sku=Community&rel=15&rid=34347&utm_source=docs&utm_medium=clickbutton&utm_campaign=python_install">Instalar Visual Studio 2017 Community</a>

    >[!Tip]
    > A edição Community é para desenvolvedores individuais, aprendizado em sala de aula, pesquisa acadêmica e desenvolvimento de software livre. Para outros usos, instale o <a target="frameTarget" href="https://www.visualstudio.com/thank-you-downloading-visual-studio/?sku=Professional&rel=15&rid=34347&utm_source=docs&utm_medium=clickbutton&utm_campaign=python_install">Visual Studio 2017 Professional</a> ou o <a target="frameTarget" href="https://www.visualstudio.com/thank-you-downloading-visual-studio/?sku=Enterprise&rel=15&rid=34347&utm_source=docs&utm_medium=clickbutton&utm_campaign=python_install">Visual Studio 2017 Enterprise</a>.

1. O instalador apresenta uma lista de cargas de trabalho, que são grupos de opções relacionadas para áreas de desenvolvimento específicas. Para Python, selecione a carga de trabalho **Desenvolvimento do Python**.

    ![Carga de trabalho de desenvolvimento do Python no instalador do Visual Studio](media/installation-python-workload.png)

    Opcional: se estiver trabalhando com ciência de dados, considere também a carga de trabalho para **Aplicativos de ciência de dados e análise**. Essa carga de trabalho inclui suporte para Python, bem como para linguagens R e F#. Para obter mais informações, veja [Carga de trabalho para Aplicativos de ciência de dados e análise](../rtvs/data-science-workload.md).

    > [!Note]
    > As cargas de trabalho para Python e para Ciência de dados estão disponíveis apenas com a versão Visual Studio 2017 15.2 e posterior.

1. No lado direito do instalador, escolha opções adicionais se desejado. Ignore essa etapa para aceitar as opções padrão.

    ![Opções de desenvolvimento do Python no instalador do Visual Studio](media/installation-python-options.png)

    | Opção | Descrição |
    | --- | --- |
    | Distribuições do Python | Escolha qualquer combinação de variantes de 32 bits e de 64 bits das distribuições do Python 2, do Python 3, do Anaconda2 e do Anaconda3 com as quais planeja trabalhar. Cada uma delas inclui o interpretador, o tempo de execução e as bibliotecas da distribuição. O Anaconda, especificamente, é uma plataforma de ciência de dados aberta que inclui uma grande variedade de pacotes. (Você pode retornar ao Instalador do Visual Studio a qualquer momento para adicionar ou remover distribuições.) |
    | Suporte do modelo Cookiecutter | Instala a interface gráfica do usuário Cookiecutter para descobrir modelos, inserir opções de modelo e criar projetos e arquivos. Consulte [Usando a extensão Cookiecutter](cookiecutter.md). |
    | Suporte Web do Python | Instala as ferramentas para desenvolvimento para a Web, incluindo suporte à edição HTML, CSS e JavaScript, juntamente com modelos para projetos que usam as estruturas Bottle, Flask e Django. Veja [Modelos de projeto Web do Python](template-web.md). |
    | Suporte ao Python IoT | Compatível com o desenvolvimento do Windows IoT Core usando Python. |
    | Ferramentas de desenvolvimento nativo do Python | Instala o compilador do C++ e outros componentes necessários para desenvolver extensões nativas para Python. Veja [Criando uma extensão do C++ para o Python](cpp-and-python.md). |
    | Principais ferramentas dos Serviços de Nuvem do Azure | Fornece suporte adicional para os Serviços de Nuvem do Azure do desenvolvedor no Python. Consulte [Projeto de Serviço de Nuvem do Azure](template-azure-cloud-service.md). |

1. Após a instalação, o instalador fornece opções para modificar, iniciar, reparar ou desinstalar o Visual Studio. O botão **Modificar** transforma-se em **Atualizar** quando há atualizações para o Visual Studio disponíveis para os componentes instalados. (A opção Modificar ficará disponível no menu suspenso.) Você também pode iniciar o Visual Studio e o instalador no menu Iniciar do Windows pesquisando "Visual Studio".

    ![Iniciando, modificando ou desinstalando o Visual Studio no instalador](media/installation-vs-launch.png)

> [!VIDEO https://mva.microsoft.com/en-US/training-courses-embed/python-tools-for-visual-studio-2017-18121/Video-Installing-Visual-Studio-Python-Support-go1id3LWE_1705918567]

## <a name="visual-studio-2015"></a>Visual Studio 2015

1. Execute o instalador do Visual Studio por meio do **Painel de Controle > Programas e Recursos**, selecionando **Microsoft Visual Studio 2015** e, em seguida, **Alterar**.

1. No instalador, selecione **Modificar**.

1. Selecione **Linguagens de Programação > Ferramentas Python para Visual Studio** e, em seguida, **Avançar**:

    ![Opção PTVS no instalador do Visual Studio 2015](media/installation-vs2015.png)

1. Depois que a instalação do Visual Studio for concluída, [instale um interpretador do Python de sua escolha](python-environments.md#selecting-and-installing-python-interpreters). Se você já tiver um interpretador instalado, consulte [Criando um ambiente para um interpretador existente](python-environments.md#creating-an-environment-for-an-existing-interpreter).

## <a name="visual-studio-2013-and-earlier"></a>Visual Studio 2013 e anterior

1. Instale a versão apropriada das Ferramentas Python para Visual Studio para sua versão do Visual Studio:

    - Visual Studio 2013: [PTVS 2.2 para Visual Studio 2013](https://github.com/Microsoft/PTVS/releases/v2.2). A caixa de diálogo **Arquivo > Novo Projeto** no Visual Studio 2013 fornece um atalho para esse processo.
    - Visual Studio 2012: [PTVS 2.1 para Visual Studio 2012](https://pytools.codeplex.com/downloads/get/920478)
    - Visual Studio 2010: [PTVS 2.1 para Visual Studio 2010](https://pytools.codeplex.com/downloads/get/920479)

1. [Instale um interpretador do Python de sua escolha](python-environments.md#selecting-and-installing-python-interpreters). Se você já tiver um interpretador instalado, consulte [Criando um ambiente para um interpretador existente](python-environments.md#creating-an-environment-for-an-existing-interpreter).

## <a name="install-locations"></a>Locais de instalação

Por padrão, o suporte do Python é instalado para todos os usuários em um computador.

Para o Visual Studio 2017, a carga de trabalho do Python é instalada em `%ProgramFiles(x86)%\Microsoft Visual Studio\2017\<VS_edition>Common7\IDE\Extensions\Microsoft\Python`, em que &lt;VS_edition&gt; é Community, Professional ou Enterprise.

Para o Visual Studio 2015 e anterior, os caminhos de instalação são os seguintes:

- 32 bits:
  - Caminho: `%Program Files(x86)%\Microsoft Visual Studio <VS_ver>\Common7\IDE\Extensions\Microsoft\Python Tools for Visual Studio\<PTVS_ver>`
  - Local do Registro do caminho: `HKEY_LOCAL_MACHINE\Software\Microsoft\PythonTools\<VS_ver>\InstallDir`
- 64 bits:
  - Caminho: `%Program Files%\Microsoft Visual Studio <VS_ver>\Common7\IDE\Extensions\Microsoft\Python Tools for Visual Studio\<PTVS_ver>`
  - Local do Registro do caminho: `HKEY_LOCAL_MACHINE\Software\Wow6432Node\Microsoft\PythonTools\<VS_ver>\InstallDir`

em que:

- &lt;VS_ver&gt; é:
  - 14.0 para Visual Studio 2015
  - 12.0 para Visual Studio 2013
  - 11.0 para Visual Studio 2012
  - 10.0 para Visual Studio 2010
- &lt;PTVS_ver&gt; é um número de versão, como 2.2, 2.1, 2.0, 1.5, 1.1 ou 1.0.

### <a name="user-specific-installations-15-and-earlier"></a>Instalações específicas ao usuário (1.5 e anterior)

A instalação das Ferramentas Python para o Visual Studio 1.5 e anteriores é permitida somente para o usuário atual. O caminho de instalação é `%LocalAppData%\Microsoft\VisualStudio\<VS_ver>\Extensions\Microsoft\Python Tools for Visual Studio\<PTVS_ver>`, em que &lt;VS_ver&gt; e &lt;PTVS_ver&gt; são iguais ao descrito acima.

<iframe src="" height="0" width="0" frameborder="0" name="frameTarget" />
