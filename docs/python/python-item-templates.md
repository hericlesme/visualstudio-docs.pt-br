---
title: Modelos de item para projetos do Python
description: Uma lista de referência de modelos de item para o projeto do Python que estão disponíveis na caixa de diálogo Adicionar > Novo Item no Visual Studio.
ms.date: 04/25/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: tutorial
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- python
- data-science
ms.openlocfilehash: 9811905e842eeb62399ef3b88558ee0286b05c84
ms.sourcegitcommit: 928885ace538bef5b25961358d4f166d648f196a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/27/2018
ms.locfileid: "32032672"
---
# <a name="python-item-templates"></a>Modelos de item do Python

Os modelos de item estão disponíveis em projetos do Python através do comando de menu **Projeto** > **Adicionar Novo Item** ou do comando **Adicionar** > **Novo Item** no menu de contexto no **Gerenciador de Soluções**.

![Caixa de diálogo Adicionar Novo Item](media/project-item-templates.png)

Se você usar o nome fornecido para o item, o modelo geralmente criará um ou mais arquivos e pastas dentro da pasta que está atualmente marcada no projeto (ao clicar duas vezes com o botão direito do mouse em uma pasta para exibir o menu de contexto, essa pasta será automaticamente marcada). Se você adicionar um item, ele será incluído no projeto do Visual Studio e será exibido no **Gerenciador de Soluções**.

A tabela a seguir explica brevemente o efeito de cada modelo de item em um projeto do Python:

| Modelo | O que o modelo cria |
| --- | --- |
| Arquivo vazio do Python | Um arquivo vazio com a extensão `.py`. |
| Classe Python | Um arquivo `.py` que contém uma única definição de classe vazia do Python. |
| Pacote do Python | Uma pasta que contém um arquivo `__init.py__`. |
| Teste de Unidade do Python | Um arquivo `.py` com um único teste de unidade baseado na estrutura `unittest`, juntamente com uma chamada a `unittest.main()` para executar os testes no arquivo. |
| Página HTML | Um arquivo `.html` com uma estrutura de página simples que consiste em um `<head>` e um elemento `<body>`. |
| JavaScript | Um arquivo `.js` vazio. |
| Folha de Estilos | Um arquivo `.css` que contém um estilo vazio para `body` |
| Arquivo de texto | Um arquivo `.txt` vazio. |
| Aplicativo Django 1.9<br/>Aplicativo Django 1.4 | Uma pasta com o nome do aplicativo que contém os arquivos principais de um aplicativo do Django conforme explicado em [Como aprender Django no Visual Studio, Etapa 2 de 2](learn-django-in-visual-studio-step-02-create-an-app.md#step-2-1-create-an-app-with-a-default-structure) para o Django 1.9. No caso do Django 1.4, a pasta `migrations`, o arquivo `admin.py` e o arquivo `apps.py` não estão incluídos. |
| Janela WPF do IronPython | Uma janela WPF consiste em dois arquivos lado a lado: um arquivo `.xaml` que define um `<Window>` com um elemento `<Grid>` vazio e um arquivo `.py` associado que carrega o arquivo XAML usando a biblioteca do `wpf`. Normalmente usado em um projeto criado usando um dos modelos de projeto do IronPython. Confira [Como gerenciar projetos Python – modelos de projetos](managing-python-projects-in-visual-studio.md#project-templates). |
| Arquivos de Suporte de Função da Web | Uma pasta `bin` na raiz do projeto (independentemente da pasta escolhida no projeto). A pasta contém um script de implantação padrão e um arquivo `web.config` para funções da Web do Serviço de Nuvem do Azure. O modelo também inclui um arquivo `readme.html` que explica os detalhes. |
| Arquivos de suporte à função de trabalho | Uma pasta `bin` na raiz do projeto (independentemente da pasta escolhida no projeto). A pasta contém o script de implantação e lançamento padrão, além de um arquivo `web.config`, para funções de trabalho da Web do Serviço de Nuvem do Azure. O modelo também inclui um arquivo `readme.html` que explica os detalhes. |
| web.config do Azure (FastCGI) | Um arquivo `web.config` que contém entradas para aplicativos que usam um objeto [WSGI](https://wsgi.readthedocs.io/en/latest/) para tratar das conexões de entrada. Normalmente, esse arquivo é implantado na raiz de um servidor Web que executa o IIS, como o Serviço de Aplicativo do Azure. Para saber mais, confira [Como publicar no Serviço de Aplicativo do Azure](publishing-python-web-applications-to-azure-from-visual-studio.md). |
| web.config do Azure (HttpPlatformHandler) | Um arquivo `web.config` que contém entradas para aplicativos que escutam conexões de entrada com um soquete. Normalmente, esse arquivo é implantado na raiz de um servidor Web que executa o IIS, como o Serviço de Aplicativo do Azure. Para saber mais, confira [Como publicar no Serviço de Aplicativo do Azure](publishing-python-web-applications-to-azure-from-visual-studio.md). |
| Arquivos estáticos web.config do Azure | Um arquivo `web.config` normalmente adicionado a uma pasta `static` (ou outra pasta que contém itens estáticos) para desabilitar o processamento do Python para essa pasta. Esse arquivo de configuração funciona em conjunto com um dos arquivos de configuração FastCGI ou HttpPlatformHandler acima. Para saber mais, confira [Como publicar no Serviço de Aplicativo do Azure](publishing-python-web-applications-to-azure-from-visual-studio.md). |
| web.config de depuração remota do Azure | Um arquivo `web.config.debug` que permite a depuração remota via WebSockets, juntamente com o `Microsoft.PythonTools.WebRole.dll` e uma pasta `ptvsd` contendo os módulos que serão implementados no servidor para ativar a depuração remota. Você geralmente cria esse item no mesmo local como o arquivo `web.config`. Para obter mais informações, confira [Depurar o código do Python remotamente no Azure](debugging-remote-python-code-on-azure.md). Também confira a observação acima. |

> [!Note]
> Se você adicionar o modelo `web.config` de depuração ao projeto e pretender usar a depuração remota do Python, precisará publicar o site na configuração "Depuração". Essa configuração é separada da configuração de solução ativa atual e sempre usa como padrão “Versão”. Para alterá-la, abra a guia **Configurações** e use a caixa de combinação **Configuração** no assistente de publicação. (Confira a [documentação do Azure](https://azure.microsoft.com/develop/python/) para obter mais informações sobre como criar e implantar assemblies para os Aplicativos Web do Azure).
>
> ![Alterando a configuração de publicação](media/template-web-publish-config.png)

## <a name="see-also"></a>Consulte também

- [Como gerenciar projetos Python – modelos de projetos](managing-python-projects-in-visual-studio.md#project-templates)
- [Modelos de projeto Web do Python](python-web-application-project-templates.md)
- [Como publicar no Serviço de Aplicativo do Azure](publishing-python-web-applications-to-azure-from-visual-studio.md)