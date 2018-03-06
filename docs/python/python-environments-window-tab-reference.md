---
title: "Referência à janela Ambientes do Python - Visual Studio | Microsoft Docs"
description: Detalhes sobre cada uma das guias que aparecem na janela Ambientes de Python no Visual Studio.
ms.custom: 
ms.date: 02/20/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.devlang: python
ms.tgt_pltfrm: 
ms.topic: article
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload:
- python
- data-science
ms.openlocfilehash: 92d5014c257cf35e556eca1928e1c5612f4913eb
ms.sourcegitcommit: c0a2385a16cc4f47d2e1ff23d35c4da40f5605e0
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/23/2018
---
# <a name="python-environments-window-tabs-reference"></a>Referência as guias da janela Ambientes do Python

Para abrir a janela **Ambientes de Python**:

- Selecione o comando de menu **Exibir > Outras Janelas > Ambientes do Python**.
- Clique com o botão direito do mouse no nó **Ambientes do Python** de um projeto no Gerenciador de Soluções e selecione **Exibir Todos os Ambientes do Python**

Se você expandir a janela **Ambientes do Python** até um tamanho grande o suficiente, essas opções serão mostradas como guias, o que talvez você considere mais conveniente para trabalhar. Para maior clareza, as guias neste artigo são mostradas na exibição expandida.

![Exibição expandida da janela Ambientes do Python](media/environments-expanded-view.png)

## <a name="overview-tab"></a>Guia Visão Geral

Fornece informações básicas e comandos para o ambiente:

![Guia Visão Geral de Ambientes do Python](media/environments-overview-tab.png)

| Comando | Descrição |
| --- | --- |
| Tornar este ambiente padrão para novos projetos | Definir o ambiente ativo, o que pode fazer com que o Visual Studio pare de responder brevemente enquanto ele carrega o banco de dados do IntelliSense. Ambientes com muitos pacotes podem parar de responder por um período maior. |
| Visitar o site do distribuidor | Abre um navegador para a URL fornecida para a distribuição de Python. Python 3. x, por exemplo, vai para python.org. |
| Abrir a janela interativa | Abre a [janela interativa (REPL)](python-interactive-repl-in-visual-studio.md) para esse ambiente dentro do Visual Studio, aplicando quaisquer [scripts de inicialização (veja abaixo)](#startup-scripts). |
| Explorar scripts interativos | Confira [Scripts de inicialização](#startup-scripts). |
| Usar o modo interativo do IPython | Quando definido, abre a janela interativa com IPython por padrão. Isso habilita os gráficos embutidos e a sintaxe estendida do IPython como `name?` para exibir a ajuda e `!command` para comandos shell. Essa opção é recomendada quando estiver usando uma distribuição Anaconda, pois ela requer pacotes extras. Para obter mais informações, consulte [Usando o IPython na Janela Interativa](interactive-repl-ipython.md). |
| Abrir no PowerShell | Inicia o interpretador em uma janela de comando do PowerShell. |
| (Links de pasta e do programa) | Fornecem acesso rápido à pasta de instalação do ambiente, o interpretador python.exe e o interpretador pythonw.exe. O primeiro abre no Windows Explorer, os dois últimos abrem uma janela do console. |

### <a name="startup-scripts"></a>Scripts de inicialização

Como você janelas interativas no fluxo de trabalho diário, provavelmente desenvolverá funções auxiliares que você usa regularmente. Por exemplo, você pode criar uma função que abre um DataFrame no Excel e, em seguida, salvar esse código como um script de inicialização para que ele esteja sempre disponível na janela interativa.

Os scripts de inicialização contêm o código que a janela interativa carrega e executa automaticamente, incluindo importações, definições de função e literalmente qualquer outra coisa. Esses scripts são referenciados de duas maneiras:

1. Quando você instala um ambiente, o Visual Studio cria uma pasta `Documents\Visual Studio 2017\Python Scripts\<environment>` em que &lt;environment&gt' corresponde ao nome do ambiente. Você pode navegar facilmente para a pasta específica do ambiente com o comando **Explorar scripts interativos**. Quando você inicia a janela interativa para esse ambiente, ela carrega e executa qualquer arquivo `.py` que for encontrado aqui em ordem alfabética.

1. O controle **Scripts** na guia **Ferramentas > Opções > Ferramentas do Python > Janelas Interativas** (consulte [Opções de janelas interativas](python-support-options-and-settings-in-visual-studio.md#interactive-windows-options)) destina-se a especificar uma pasta adicional para os scripts de inicialização que estão carregados e são executados em todos os ambientes. No entanto, esse recurso não funciona no momento.

## <a name="configure-tab"></a>Guia Configurar

Se estiver disponível, conterá detalhes, conforme descrito na tabela abaixo. Se essa guia não estiver presente, isso significa que o Visual Studio está gerenciando todos os detalhes automaticamente.

![Guia Configurar de Ambientes do Python](media/environments-configure-tab.png)

| Campo | Descrição |
| --- | --- |
| **Descrição** | O nome a ser fornecido para o ambiente. |
| **Caminho do prefixo** | A localização da pasta base do interpretador. Ao preencher esse valor e clicar em **Detecção Automática**, o Visual Studio tenta preencher os outros campos para você. |
| **Caminho do interpretador** | O caminho para o executável do interpretador, normalmente, o caminho do prefixo seguido por `python.exe` |
| **Interpretador de janela** | O caminho para o executável que não é de console, geralmente, o caminho do prefixo seguido por `pythonw.exe`. |
| **Caminho da biblioteca**<br/>(se estiver disponível) | Especifica a raiz da biblioteca padrão, mas esse valor poderá ser ignorado se o Visual Studio conseguir solicitar um caminho mais preciso do interpretador. |
| **Versão da linguagem** | Selecionada no menu suspenso. |
| **Arquitetura** | Normalmente, detectada e preenchida automaticamente; caso contrário, especifica 32 ou 64 bits. |
| **Variável de ambiente do caminho** | A variável de ambiente que o interpretador usa para encontrar caminhos de pesquisa. O Visual Studio altera o valor da variável ao iniciar o Python, para que ela contenha os caminhos de pesquisa do projeto. Normalmente, essa propriedade deve ser definida como `PYTHONPATH`, mas alguns interpretadores usam outro valor. |

## <a name="packages-tab"></a>Guia Pacotes

*Também chamada de "pip" em versões anteriores.*

Gerencia os pacotes instalados no ambiente, permitindo também pesquisar e instalar novos (incluindo as dependências). A pesquisa filtra seus pacotes instalados no momento e [PyPI](https://pypi.python.org). Também é possível inserir diretamente qualquer comando `pip install` na caixa de pesquisa, incluindo sinalizadores como `--user` ou `--no-deps`.

![Guia de pacotes de ambientes do Python](media/environments-pip-tab.png)

Instalar um pacote cria subpastas dentro da pasta `Lib` do ambiente no sistema de arquivos. Por exemplo, se você tiver Python 3.6 instalados em `c:\Python36`, os pacotes são instalados em `c:\Python36\Lib`, se você tiver o Anaconda3 instalado em `c:\Program Files\Anaconda3`, os pacotes serão instalados em `c:\Program Files\Anaconda3\Lib`.

No último caso, como o ambiente está localizado em uma área protegida do sistema de arquivos, `c:\Program Files`, o Visual Studio deve executar `pip install` com privilégios elevados para permitir que ele crie subpastas do pacote. Quando a elevação é necessária, o Visual Studio exibe o prompt, "Podem ser necessários privilégios de administrador para instalar, atualizar ou remover pacotes para esse ambiente":

![Solicitação de elevação para a instalação do pacote](media/environments-pip-elevate.png)

**Elevar agora** concede privilégios administrativos para executar o PIP para uma única operação, sujeita também a qualquer prompt de permissão do sistema operacional. Selecionar **Continuar sem Privilégios de administrador** tenta instalar o pacote, mas o PIP falha ao tentar criar pastas com uma saída como “erro: não foi possível criar 'C:\Arquivos de Programas\Anaconda3\Lib\site-packages\png.py': permissão negada”.

Selecionar **Sempre elevar ao instalar o u remover pacotes** impede que a caixa de diálogo apareça para o ambiente em questão. Para fazer a caixa de diálogo aparecer novamente, vá para **Ferramentas > Opções > Ferramentas do Python > Geral** e selecione o botão **Redefinir todas as caixas de diálogo permanentemente ocultas**.

Nessa mesma guia de opções, você também pode selecionar **Sempre executar o PIP como administrador** para suprimir a caixa de diálogo para todos os ambientes. Consulte [Opções – guia Geral](python-support-options-and-settings-in-visual-studio.md#general-options).

## <a name="intellisense-tab"></a>Guia IntelliSense

Mostra o status atual do banco de dados de preenchimento do IntelliSense:

![Guia IntelliSense de Ambientes do Python](media/environments-intellisense-tab.png)

O banco de dados contém metadados para todas as bibliotecas do ambiente, melhora a velocidade do IntelliSense e reduz o uso de memória. Quando o Visual Studio detecta um novo ambiente (ou você adiciona um), ele começa a compilar o banco de dados automaticamente, analisando os arquivos de origem da biblioteca. Esse processo pode levar de um minuto a uma hora ou mais, dependendo do que está instalado. (O Anaconda, por exemplo, é fornecido com várias bibliotecas e leva algum tempo para compilar o banco de dados.) Depois de concluído, você obtém um IntelliSense detalhado não precisa atualizar o banco de dados novamente (com o botão **Atualizar Banco de Dados**) quando instalar mais bibliotecas.

As bibliotecas para as quais os dados não foram compilados serão marcadas com um **!**; se o banco de dados de um ambiente não estiver concluído, um **!** também é exibido ao lado da lista do ambiente principal.

## <a name="see-also"></a>Consulte também

- [Gerenciando ambientes do Python no Visual Studio](managing-python-environments-in-visual-studio.md)
- [Selecionar um intérprete para um projeto](selecting-a-python-environment-for-a-project.md)
- [Usando requirements.txt para dependências](managing-required-packages-with-requirements-txt.md) 
- [Caminhos de pesquisa](search-paths.md)
