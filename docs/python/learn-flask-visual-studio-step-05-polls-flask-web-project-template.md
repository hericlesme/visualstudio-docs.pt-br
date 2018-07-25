---
title: Tutorial – Saiba mais sobre o Flask no Visual Studio, etapa 5
description: Um passo a passo das noções básicas do Flask no contexto dos projetos do Visual Studio, especificamente as funcionalidades dos modelos de Pesquisas do Projeto Web do Flask e Pesquisas do Projeto Web do Flask/Jade.
ms.date: 05/25/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: tutorial
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- python
- data-science
ms.openlocfilehash: 3fc6a1dff49c754c13fb8b94e03f956b3081f075
ms.sourcegitcommit: 25a62c2db771f938e3baa658df8b1ae54a960e4f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/24/2018
ms.locfileid: "39232313"
---
# <a name="step-5-use-the-polls-flask-web-project-template"></a>Etapa 5 – Usar o modelo Projeto Web do Flask de pesquisas

**Etapa anterior: [Usar o modelo Projeto Web completo do Flask](learn-flask-visual-studio-step-04-full-flask-project-template.md)**

Depois de entender o modelo "Projeto Web do Flask" do Visual Studio, agora será possível examinar o terceiro modelo do Flask, "Pesquisas do Projeto Web do Flask", criado sobre a mesma base de código.

Nesta etapa, você aprenderá a:

> [!div class="checklist"]
> - Criar um projeto com base no modelo e inicializar o banco de dados (etapa 5-1)
> - Compreender os modelos de dados (etapa 5-2)
> - Compreender os armazenamentos de dados de backup e (etapa 5-3)
> - Compreender os detalhes da votação e as visualizações dos resultados (etapa 5-4)

O Visual Studio também projeta o modelo "Pesquisas do Projeto Web do Flask/Jade" que produz um aplicativo idêntico, mas usa a extensão do Jade para o mecanismo de modelagem do Jinja. Para obter detalhes, confira [Etapa 4 – Modelo Projeto Web do Flask/Jade](learn-flask-visual-studio-step-04-full-flask-project-template.md#the-flaskjade-web-project-template).

## <a name="step-5-1-create-the-project"></a>Etapa 5-1: Criar o projeto

1. No Visual Studio, acesse **Gerenciador de Soluções**, clique com o botão direito do mouse na solução "LearningFlask" criada anteriormente neste tutorial e selecione **Adicionar** > **Novo Projeto**. (Como alternativa, se você quiser usar uma nova solução, selecione **Arquivo** > **Novo** > **Projeto**).

1. Na caixa de diálogo Novo Projeto, procure e selecione o modelo "Pesquisas do Projeto Web do Flask", nomeie o projeto "FlaskPolls" e selecione **OK**.

1. Como os outros modelos de projeto no Visual Studio, o modelo "Pesquisas do Projeto Web do Flask" inclui um arquivo `requirements.txt`, os prompts do Visual Studio perguntam onde instalar essas dependências. Escolha a opção **Instalar em um ambiente virtual** e, na caixa de diálogo **Adicionar Ambiente Virtual**, selecione **Criar** para aceitar os padrões. (Esse modelo requer o Flask, bem como os pacotes azure-storage e pymongo; o "Pesquisas do Projeto Web do Flask/Jade" também requerem pyjade.)

1. Defina o projeto "FlaskPolls" para ser o padrão para a solução do Visual Studio clicando com o botão direito do mouse nesse projeto em **Gerenciador de Soluções** e selecionando **Definir como Projeto de Inicialização**. O projeto de inicialização, mostrado em negrito, é o que é executado quando você inicia o depurador.

1. Escolha **Depurar > Iniciar Depuração** (F5) ou usar o **Servidor Web** na barra de ferramentas para executar o servidor:

    ![Executar o botão da barra de ferramentas do servidor Web no Visual Studio](media/django/run-web-server-toolbar-button.png)

1. O aplicativo criado pelo modelo tem três páginas, Página inicial, Sobre e Contato, que você navega usando a barra de navegação superior. Leve alguns minutos para examinar as diferentes partes do aplicativo (as páginas Sobre e Contato são muito semelhantes ao "Projeto Web do Flask" e não serão mais discutidas).

    ![Exibição completa do aplicativo Pesquisas do Projeto Web do Flask](media/flask/step06-full-app-view.png)

1. Na home page, o botão **Criar Votações de Exemplo** inicializa o armazenamento de dados do aplicativo com três votações diferentes descritas na página `models/samples.json`. Por padrão, o aplicativo usa um banco de dados na memória (conforme mostrado na página Sobre), que é redefinido cada vez que o aplicativo é reiniciado. O aplicativo também contém código para trabalhar com o Armazenamento do Azure e com o MongoDB, conforme será ainda descrito neste artigo.

1. Depois que você tiver inicializado o armazenamento de dados, poderá votar nas diferentes votações conforme mostrado na home page (a barra de navegação e o rodapé são omitidos para fins de brevidade):

    ![Exibição do aplicativo Votações depois que o armazenamento de dados é inicializado](media/flask/step06-polls-initialized.png)

1. Selecionar uma votação exibe opções específicas:

    ![Interface para votar em uma votação](media/flask/step06-polls-voting-interface.png)

1. Depois de votar, o aplicativo mostrará uma página de resultados e permitirá que você vote novamente:

    ![Visualização dos resultados após a votação](media/flask/step06-polls-results.png)

1. Você pode deixar o aplicativo em execução para as seções a seguir.

    Se quiser parar o aplicativo e [confirmar as alterações para o controle de origem](learn-flask-visual-studio-step-02-create-app.md#commit-to-source-control), primeiro abra a página **Alterações** no **Team Explorer**, clicando com o botão direito na pasta para o ambiente virtual (provavelmente `env`) e selecione **Ignorar esses itens locais**.

### <a name="examine-the-project-contents"></a>Examine o conteúdo do projeto

Conforme observado anteriormente, quase tudo o que está em um projeto criado com base no modelo "Pesquisas do Projeto Web do Flask" (e o modelo do "Pesquisas do Projeto Web do Flask/Jade) deverá ser conhecido se você tiver explorado os outros modelos de projeto no Visual Studio. As etapas adicionais neste artigo resumem as mais alterações e adições mais significativas, ou seja, modelos de dados e modos de exibição adicionais.

## <a name="step-5-2-understand-the-data-models"></a>Etapa 5-2: Compreender os modelos de dados

Os modelos de dados do aplicativo são classes do Python nomeadas Votação e Opção, definidas em `models/__init__.py`. Uma Votação representa uma pergunta, para a qual uma coleção de instâncias de Opção representam as respostas disponíveis. Uma Votação também mantém o número total de votos (para qualquer opção) e um método para calcular as estatísticas usadas para gerar exibições:

```python
class Poll(object):
    """A poll object for use in the application views and repository."""
    def __init__(self, key=u'', text=u''):
        """Initializes the poll."""
        self.key = key
        self.text = text
        self.choices = []
        self.total_votes = None

    def calculate_stats(self):
        """Calculates some statistics for use in the application views."""
        total = 0
        for choice in self.choices:
            total += choice.votes
        for choice in self.choices:
            choice.votes_percentage = choice.votes / float(total) * 100 \
                if total > 0 else 0
        self.total_votes = total

class Choice(object):
    """A poll choice object for use in the application views and repository."""
    def __init__(self, key=u'', text=u'', votes=0):
        """Initializes the poll choice."""
        self.key = key
        self.text = text
        self.votes = votes
        self.votes_percentage = None
```

Esses modelos de dados são abstrações genéricas que permitem que os modos de exibição do aplicativo trabalhar em diferentes tipos de backup de armazenamentos de dados, que serão descritos na próxima etapa.

## <a name="step-5-3-understand-the-backing-data-stores"></a>Etapa 5-3: Compreender os armazenamentos de dados de backup

O aplicativo criado pelo modelo "Pesquisas do Projeto Web do Flask" pode ser executado em um armazenamento de dados na memória, no Armazenamento de Tabelas do Azure ou em um banco de dados MongoDB.

O mecanismo de armazenamento de dados funciona da seguinte maneira:

1. O tipo de repositório é especificado por meio da variável de ambiente `REPOSITORY_NAME`, que pode ser definida como "memory", "azuretablestore" ou "mongodb". Um trecho de código em `settings.py` recupera o nome usando "memória" como o padrão. Se desejar alterar o repositório de backup, será necessário definir a variável de ambiente e reiniciar o aplicativo.

    ```python
    from os import environ
    REPOSITORY_NAME = environ.get('REPOSITORY_NAME', 'memory')
    ```

1. O `settings.py` código inicializa um objeto `REPOSITORY_SETTINGS`. Se desejar usar o repositório de tabelas do Azure ou o MongoDB, será necessário inicializar primeiro os armazenamentos de dados em outro lugar e então definir as variáveis de ambiente necessárias que informarão ao aplicativo como se conectar ao armazenamento:

    ```python
    if REPOSITORY_NAME == 'azuretablestorage':
        REPOSITORY_SETTINGS = {
            'STORAGE_NAME': environ.get('STORAGE_NAME', ''),
            'STORAGE_KEY': environ.get('STORAGE_KEY', ''),
            'STORAGE_TABLE_POLL': environ.get('STORAGE_TABLE_POLL', 'polls'),
            'STORAGE_TABLE_CHOICE': environ.get('STORAGE_TABLE_CHOICE', 'choices'),
        }
    elif REPOSITORY_NAME == 'mongodb':
        REPOSITORY_SETTINGS = {
            'MONGODB_HOST': environ.get('MONGODB_HOST', None),
            'MONGODB_DATABASE': environ.get('MONGODB_DATABASE', 'polls'),
            'MONGODB_COLLECTION': environ.get('MONGODB_COLLECTION', 'polls'),
        }
    elif REPOSITORY_NAME == 'memory':
        REPOSITORY_SETTINGS = {}
    else:
        raise ValueError('Unknown repository.')
    ```

1. Em `views.py`, o aplicativo chama um método de fábrica para inicializar um objeto `Repository` usando o nome e as configurações do armazenamento de dados:

    ```python
    from FlaskPolls.models import PollNotFound
    from FlaskPolls.models.factory import create_repository
    from FlaskPolls.settings import REPOSITORY_NAME, REPOSITORY_SETTINGS

    repository = create_repository(REPOSITORY_NAME, REPOSITORY_SETTINGS)
    ```

1. O método `factory.create_repository` é encontrado em `models\factory.py`, que simplesmente importa o módulo de repositório adequado e cria uma instância `Repository`:

    ```python
    def create_repository(name, settings):
        """Creates a repository from its name and settings. The settings
        is a dictionary where the keys are different for every type of repository.
        See each repository for details on the required settings."""
        if name == 'azuretablestorage':
            from .azuretablestorage import Repository
        elif name == 'mongodb':
            from .mongodb import Repository
        elif name == 'memory':
            from .memory import Repository
        else:
            raise ValueError('Unknown repository.')

        return Repository(settings)
    ```

1. As implementações da classe `Repository` específicas para cada armazenamento de dados podem ser encontradas em `models\azuretablestorage.py`, `models\mongodb.py` e `models\memory.py`. A implementação de Armazenamento do Azure usa o pacote azure-storage; a implementação do banco de dados Mongo usa o pacote pymongo. Conforme observado na etapa 5-1, ambos os pacotes são incluídos no arquivo `requirements.txt` do modelo de projeto. Explorar os detalhes é um exercício para o leitor.

Em resumo, a classe `Repository` resume as especificidades do armazenamento de dados, e o aplicativo usa variáveis de ambiente em tempo de execução para selecionar e configurar quais das três implementações usar.

As etapas a seguir adicionam suporte a um armazenamento de dados diferente dos três fornecidos pelo modelo de projeto se desejado:

1. Copie `memory.py` para um novo arquivo para ter a interface básica para a classe `Repository`.
1. Modifique a implementação da classe conforme seja adequado para o armazenamento de dados que você está usando.
1. Modifique `factory.py` para adicionar outro caso `elif` que reconheça o nome de seu armazenamento de dados adicionado e importe o módulo apropriado.
1. Modifique `settings.py` para reconhecer outro nome na variável de ambiente `REPOSITORY_NAME` e inicializar `REPOSITORY_SETTINGS` adequadamente.

### <a name="seed-the-data-store-from-samplesjson"></a>Propagar o armazenamento de dados de samples.json

Inicialmente, qualquer armazenamento de dados escolhido não contém nenhuma votação, então a home page do aplicativo exibe a mensagem "Nenhuma votação disponível" com o botão **Criar Votações de Exemplo**. No entanto, depois de selecionar o botão, o modo de exibição é alterado para exibir as votações disponíveis. Esta opção ocorre por meio de marcas condicionais em `templates\index.html` (algumas linhas em branco foram omitidas para fins de brevidade):

```html
{% extends "layout.html" %}
{% block content %}
<h2>{{title}}.</h2>

{% if polls %}
<table class="table table-hover">
    <tbody>
        {% for poll in polls %}
        <tr>
            <td>
                <a href="/poll/{{poll.key}}">{{poll.text}}</a>
            </td>
        </tr>
        {% endfor %}
    </tbody>
</table>
{% else %}
<p>No polls available.</p>
<br />
<form action="/seed" method="post">
    <button class="btn btn-primary" type="submit">Create Sample Polls</button>
</form>
{% endif %}
{% endblock %}
```

A variável `polls` no modelo vem de uma chamada a `repository.get_polls`, que não retorna nada até que o armazenamento de dados seja inicializado.

Selecionar o botão **Criar Votações de Exemplo** navega até a URL /seed. O manipulador para essa rota é definido em `views.py`:

```python
@app.route('/seed', methods=['POST'])
def seed():
    """Seeds the database with sample polls."""
    repository.add_sample_polls()
    return redirect('/')
```

A chamada a `repository.add_sample_polls()` termina em uma das implementações `Repository` específicas para seu armazenamento de dados escolhido. Cada implementação chama o método `_load_samples_json` encontrado no `models\__init__.py` para carregar o arquivo `models\samples.json` na memória. Em seguida, itera por meio desses dados para criar os objetos `Poll` e `Choice` necessários no armazenamento de dados.

Após a conclusão desse processo, a instrução `redirect('/')` no método `seed` navega de volta para a home page. Como agora `repository.get_polls` retorna um objeto de dados, as marcas condicionais em `templates\index.html` agora renderizam uma tabela que contém as votações.

### <a name="question-how-does-one-add-new-polls-to-the-app"></a>Pergunta: como adicionar novas votações ao aplicativo?

Resposta: o aplicativo, conforme fornecido por meio do modelo de projeto, não inclui uma facilidade para adicionar ou editar votações. É possível modificar `models\samples.json` para criar novos dados de inicialização, mas fazer isso significaria redefinir o armazenamento de dados. Para implementar funcionalidades de edição, é necessário estender a interface de classe `Repository` com métodos para criar as instâncias `Choice` e `Poll` necessárias. Em seguida, implemente uma interface do usuário em outras páginas que usam esses métodos.

## <a name="step-5-4-understand-the-poll-detail-and-results-views"></a>Etapa 5-4: Compreender os detalhes da votação e as visualizações dos resultados

A maioria dos modos de exibição gerados pelos modelos "Pesquisas do Projeto Web do Flask" e "Pesquisas do Projeto Web do Flask/Jade", como os modos de exibição para as páginas Sobre e Contato, é muito semelhantes aos modos de exibição criados pelo modelo "Projeto Web do Flask" (ou "Projeto Web do Flask/Jade") com o qual você trabalhou anteriormente neste tutorial. Na seção anterior você também aprendeu como a home page é implementada para mostrar o botão de inicialização ou a lista de votações.

O que sobra aqui é examinar os votos (detalhes) e a visualização dos resultados de uma votação individual.

Quando você seleciona uma votação na home page, o aplicativo navega até a URL /poll/\<chave\>, em que *chave* é o identificador exclusivo de uma votação. Em `views.py`, é possível ver que a função `details` é atribuída para lidar com esse roteamento de URL para GET e solicitações. Também é possível ver que usar `<key>` na rota de URL mapeia qualquer rota desse formulário para a mesma função e gera um argumento para a função do mesmo nome:

```python
@app.route('/poll/<key>', methods=['GET', 'POST'])
def details(key):
    """Renders the poll details page."""
    error_message = ''
    if request.method == 'POST':
        try:
            choice_key = request.form['choice']
            repository.increment_vote(key, choice_key)
            return redirect('/results/{0}'.format(key))
        except KeyError:
            error_message = 'Please make a selection.'

    return render_template(
        'details.html',
        title='Poll',
        year=datetime.now().year,
        poll=repository.get_poll(key),
        error_message=error_message,
    )
```

Para mostrar uma votação (solicitações GET), essa função simplesmente chama `templates\details.html`, que itera na matriz `choices` da votação, criando um botão de opção para cada uma.

```html
{% extends "layout.html" %}

{% block content %}

<h2>{{poll.text}}</h2>
<br />

{% if error_message %}
<p class="text-danger">{{error_message}}</p>
{% endif %}

<form action="/poll/{{poll.key}}" method="post">
    {% for choice in poll.choices %}
    <div class="radio">
        <label>
            <input type="radio" name="choice" id="choice{{choice.key}}" value="{{choice.key}}" />
            {{ choice.text }}
        </label>
    </div>
    {% endfor %}
    <br />
    <button class="btn btn-primary" type="submit">Vote</button>
</form>

{% endblock %}
```

Como o botão **Votar** tem `type="submit"`, selecioná-lo gera uma solicitação POST de volta para a mesma URL roteada para a função `details` mais uma vez. Desta vez, no entanto, ela extrai a opção dos dados do formulário e redireciona para /results/\<opção\>.

A URL /results/\<chave\> é roteada para a função `results` em `views.py`, que chama o método `calculate_stats` da votação e emprega `templates\results.html` para a renderização:

```python
@app.route('/results/<key>')
def results(key):
    """Renders the results page."""
    poll = repository.get_poll(key)
    poll.calculate_stats()
    return render_template(
        'results.html',
        title='Results',
        year=datetime.now().year,
        poll=poll,
    )
```

O modelo `results.html`, por sua vez, simplesmente itera por meio de opções da votação e gera uma barra de progresso para cada uma:

```html
{% extends "layout.html" %}

{% block content %}

<h2>{{poll.text}}</h2>
<br />

{% for choice in poll.choices %}
<div class="row">
    <div class="col-sm-5">{{choice.text}}</div>
    <div class="col-sm-5">
        <div class="progress">
            <div class="progress-bar" role="progressbar" aria-valuenow="{{choice.votes}}" aria-valuemin="0" aria-valuemax="{{poll.total_votes}}" style="width: {{choice.votes_percentage}}%;">
                {{choice.votes}}
            </div>
        </div>
    </div>
</div>
{% endfor %}

<br />
<a class="btn btn-primary" href="/poll/{{poll.key}}">Vote again?</a>

{% endblock %}
```

## <a name="next-steps"></a>Próximas etapas

> [!Note]
> Se você tiver confirmando sua solução do Visual Studio para controle de origem ao longo deste tutorial, agora será um bom momento para fazer outra confirmação. Sua solução deve corresponder ao código-fonte do tutorial no GitHub: [Microsoft/python-sample-vs-learning-flask](https://github.com/Microsoft/python-sample-vs-learning-flask).

Agora você explorou a totalidade dos modelos "Projeto Web em Branco do Flask", "Projeto Web do Flask[/Jade]" e "Pesquisa Projeto Web de Flask[/Jade]" no Visual Studio. Você conheceu todas as noções básicas do Flask, como usar modos de exibição, modelos e roteamento, e viu como usar armazenamentos de dados de backup. Agora você poderá começar a usar um aplicativo Web por sua conta com os modos de exibição e modelos de que precisar.

A execução de um aplicativo Web no computador de desenvolvimento é apenas uma etapa para disponibilizar o aplicativo para seus clientes. As próximas etapas podem incluir as seguintes tarefas:

- Implante o aplicativo Web em um servidor de produção, como o Serviço de Aplicativo do Azure. Consulte [Publish to Azure App Service](publishing-python-web-applications-to-azure-from-visual-studio.md) (Publicar no Serviço de Aplicativo do Azure), que inclui alterações específicas necessárias para aplicativos do Flask.

- Adicione uma implementação de repositório que usa outro armazenamento de dados em nível de produção como o PostgreSQL, o MySQL e o SQL Server (que podem ser hospedados no Azure). Também é possível usar o [SDK do Azure para Python](azure-sdk-for-python.md) para trabalhar com serviços de armazenamento do Azure como tabelas e blobs, bem como o Cosmos DB.

- Configure um pipeline de integração contínua/implantação contínua em um serviço como o Visual Studio Team Services. Além de trabalhar com o controle de origem (no VSTS, GitHub ou em outro local), você pode fazer o VSTS automaticamente executar os testes de unidade como um pré-requisito para a versão e também configurar o pipeline para implantar em um servidor de teste para testes adicionais antes de implantar em produção. O VSTS, além disso, integra-se com as soluções de monitoramento, como o App Insights e fecha o ciclo de inteiro com ferramentas ágeis de planejamento. Para obter mais informações, consulte:

  - [Criar um pipeline de CI/CD para Python com o projeto do Azure DevOps](/vsts/build-release/apps/cd/azure/azure-devops-project-python?view=vsts)
  - [Desenvolvimento do Python no Azure com o Visual Studio Team Services (vídeo, 11m 21s)](https://azure.microsoft.com/resources/videos/connect-2017-python-development-in-azure-with-visual-studio-team-services/).
