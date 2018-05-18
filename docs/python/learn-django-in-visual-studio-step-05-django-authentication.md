---
title: Tutorial – Saiba mais sobre Django no Visual Studio, etapa 5
description: Um passo a passo dos conceitos básicos do Django no contexto dos projetos do Visual Studio, especificamente os recursos de autenticação fornecidos pelos modelos Projeto Web do Django.
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
ms.openlocfilehash: 87d123e4da3d27d9b8c3ac1db5c3d02fe4b5ac44
ms.sourcegitcommit: 928885ace538bef5b25961358d4f166d648f196a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/27/2018
---
# <a name="tutorial-step-5-authenticate-users-in-django"></a>Etapa 5 do tutorial: autenticar usuários em Django

**Etapa anterior: [Usar o modelo Projeto Web completo do Django](learn-django-in-visual-studio-step-04-full-django-project-template.md)**

Como a autenticação é uma necessidade comum dos aplicativos Web, o modelo "Projeto Web do Django" inclui um fluxo de autenticação básico. (O modelo "Pesquisa Projeto Web do Django" abordado na etapa 6 deste tutorial também inclui o mesmo fluxo.) Ao usar qualquer um dos modelos de projeto do Django, o Visual Studio inclui todos os módulos necessários para a autenticação em `settings.py` no projeto do Django.

Nesta etapa, você aprenderá:

> [!div class="checklist"]
> - Como usar o fluxo de autenticação fornecido em modelos do Visual Studio (etapa 5 – 1)

## <a name="step-5-1-use-the-authentication-flow"></a>Etapa 5-1: Usar o fluxo de autenticação

As etapas a seguir acionam o fluxo de autenticação e descrevem as partes envolvidas do projeto:

1. Se você ainda não seguiu as instruções no arquivo `readme.html` na raiz do projeto para criar uma conta de superusuário (administrador), faça isso agora.

1. Execute o aplicativo do Visual Studio usando **Depurar** > **Iniciar Depuração** (F5). Quando o aplicativo aparecer no navegador, observe que a opção **Login** aparecerá no canto superior direito da barra de navegação.

    ![Controle de logon na página do aplicativo do Projeto Web do Django](media/django/step05-login-control.png)

1. Abra o `templates/app/layout.html` e observe que o elemento `<div class="navbar ...>` contém a marca `{% include app/loginpartial.html %}`. A marca `{% include %}` instrui o sistema de modelos do Django a efetuar pull do conteúdo do arquivo incluído neste momento no modelo que o contém.

1. Abra `templates/app/loginpartial.html` e observe como ele usa a marca `{% if user.is_authenticated %}` condicional juntamente com uma marca `{% else %}` para renderizar diferentes elementos da interface do usuário, dependendo se o usuário realizou a autenticação ou não:

    ```html
    {% if user.is_authenticated %}
    <form id="logoutForm" action="/logout" method="post" class="navbar-right">
        {% csrf_token %}
        <ul class="nav navbar-nav navbar-right">
            <li><span class="navbar-brand">Hello {{ user.username }}!</span></li>
            <li><a href="javascript:document.getElementById('logoutForm').submit()">Log off</a></li>
        </ul>
    </form>

    {% else %}

    <ul class="nav navbar-nav navbar-right">
        <li><a href="{% url 'login' %}">Log in</a></li>
    </ul>

    {% endif %}
    ```

1. Como nenhum usuário é autenticado quando você inicia o aplicativo pela primeira vez, esse código de modelo renderiza apenas o link "Fazer logon" para o caminho relativo "logon". Conforme especificado em `urls.py` e exibido na seção anterior, essa rota é mapeada para o modo de exibição `django.contrib.auth.views.login` que recebe os seguintes dados:

    ```python
    {
        'template_name': 'app/login.html',
        'authentication_form': app.forms.BootstrapAuthenticationForm,
        'extra_context':
        {
            'title': 'Log in',
            'year': datetime.now().year,
        }
    }
    ```

    Aqui, `template_name` identifica o modelo da página de logon, nesse caso `templates/app/login.html`. A propriedade `extra_context` é adicionada aos dados de contexto padrão fornecidos para o modelo. Por fim, `authentication_form` especifica uma classe de formulário para usar com o logon no modelo, ele será exibido como o objeto `form`. O valor padrão é `AuthenticationForm` (de `django.contrib.auth.views`). Em vez disso, o modelo de projeto do Visual Studio usa o formulário definido no arquivo `forms.py` do aplicativo:

    ```python
    from django import forms
    from django.contrib.auth.forms import AuthenticationForm
    from django.utils.translation import ugettext_lazy as _

    class BootstrapAuthenticationForm(AuthenticationForm):
        """Authentication form which uses boostrap CSS."""
        username = forms.CharField(max_length=254,
                                   widget=forms.TextInput({
                                       'class': 'form-control',
                                       'placeholder': 'User name'}))
        password = forms.CharField(label=_("Password"),
                                   widget=forms.PasswordInput({
                                       'class': 'form-control',
                                       'placeholder':'Password'}))
    ```

    Como você pode ver, essa classe de formulário deriva de `AuthenticationForm` e, especificamente, substitui os campos de nome de usuário e senha para adicionar texto de espaço reservado. O modelo do Visual Studio inclui esse código explícito supondo que você provavelmente desejará personalizar o formulário, como, por exemplo, adicionando validação de força de senha.

1. Quando você navega para a página de logon, em seguida, a aplicativo renderiza o modelo `login.html`. As variáveis `{{ form.username }}` e `{{ form.password }}` renderizam os formulários `CharField` de `BootstrapAuthenticationForm`. Há também uma seção interna para mostrar erros de validação e um elemento predefinido para efetuar logons em redes sociais, se você optar por adicionar esses serviços.

    ```html
    {% extends "app/layout.html" %}

    {% block content %}

    <h2>{{ title }}</h2>
    <div class="row">
        <div class="col-md-8">
            <section id="loginForm">
                <form action="." method="post" class="form-horizontal">
                    {% csrf_token %}
                    <h4>Use a local account to log in.</h4>
                    <hr />
                    <div class="form-group">
                        <label for="id_username" class="col-md-2 control-label">User name</label>
                        <div class="col-md-10">
                            {{ form.username }}
                        </div>
                    </div>
                    <div class="form-group">
                        <label for="id_password" class="col-md-2 control-label">Password</label>
                        <div class="col-md-10">
                            {{ form.password }}
                        </div>
                    </div>
                    <div class="form-group">
                        <div class="col-md-offset-2 col-md-10">
                            <input type="hidden" name="next" value="/" />
                            <input type="submit" value="Log in" class="btn btn-default" />
                        </div>
                    </div>
                    {% if form.errors %}
                    <p class="validation-summary-errors">Please enter a correct user name and password.</p>
                    {% endif %}
                </form>
            </section>
        </div>
        <div class="col-md-4">
            <section id="socialLoginForm"></section>
        </div>
    </div>

    {% endblock %}
    ```

1. Quando você enviar o formulário, o Django tentará autenticar as credenciais fornecidas (como as credenciais do superusuário). Se a autenticação falhar, você permanecerá na mesma página, mas `form.errors` será definido como true. Se a autenticação for bem-sucedida, o Django navegará para a URL relativa no campo "avançar", `<input type="hidden" name="next" value="/" />`, que, nesse caso, é a página inicial (`/`).

1. Agora, quando a página inicial for novamente renderizada, a propriedade `user.is_authenticated` será true quando o modelo `loginpartial.html` for renderizado. Como resultado, você verá uma mensagem "Olá (nome de usuário)" e "Fazer logoff". Você pode usar `user.is_authenticated` em outras partes do aplicativo para verificar a autenticação.

    ![Mensagem de Olá e controle de logon na página do aplicativo do Projeto Web do Django](media/django/step05-logoff-control.png)

1. Para verificar se o usuário autenticado está autorizado a acessar recursos específicos, você precisará recuperar permissões específicas do usuário do banco de dados desse usuário. Para obter mais detalhes, confira [Como usar o sistema de autenticação do Django](https://docs.djangoproject.com/en/2.0/topics/auth/default/#permissions-and-authorization) (documentos do Django).

1. O superusuário ou o administrador, em particular, está autorizado a acessar as interfaces de administrador internas do Django usando as URLs relativas "/admin/" e "/admin/doc/". Para habilitar essas interfaces, abra o projeto `urls.py` do Django e remova os comentários das seguintes entradas:

    ```python
    from django.conf.urls import include
    from django.contrib import admin
    admin.autodiscover()

    # ...
    urlpatterns = [
        # ...
        url(r'^admin/doc/', include('django.contrib.admindocs.urls')),
        url(r'^admin/', include(admin.site.urls)),
    ]
    ```

    Quando você reiniciar o aplicativo, navegue até "/admin/" e "/admin/doc/" e execute tarefas, como criar contas de usuário adicionais.

    ![Interface de administrador do Django](media/django/step05-administrator-interface.png)

1. A parte final do fluxo de autenticação é fazer logoff. Como você pode ver em `loginpartial.html`, o link **Fazer logoff** simplesmente faz um POST para a URL relativa "/login", que é tratada pelo modo de exibição interno `django.contrib.auth.views.logout`. Esse modo de exibição não exibe interfaces do usuário e apenas navega para a página inicial (como mostrado em `urls.py` para o padrão "^logout$"). Se você quiser exibir uma página de logoff, primeiro altere o padrão da URL conforme mostrado a seguir para adicionar uma propriedade "template_name" e remover a propriedade "next_page":

    ```python
    url(r'^logout$',
        django.contrib.auth.views.logout,
        {
            'template_name': 'app/loggedoff.html',
            # 'next_page': '/',
        },
        name='logout')
    ```

    Em seguida, crie `templates/app/loggedoff.html` com o seguinte conteúdo (mínimo):

    ```html
    {% extends "app/layout.html" %}
    {% block content %}
    <h3>You have been logged off</h3>
    {% endblock %}
    ```

    O resultado se parece com o seguinte:

    ![Página de logoff adicionada](media/django/step05-logged-off-page.png)

1. Quando terminar, interrompa o servidor e, mais uma vez, confirme suas alterações no controle do código-fonte.

### <a name="question-what-is-the-purpose-of-the--crsftoken--tag-that-appears-in-the-form-elements"></a>Pergunta: Qual é o objetivo da marca {% crsf_token %} exibida nos elementos \<form\>?

Resposta: A marca `{% crsf_token %}` inclui a [proteção interna contra solicitações intersite forjadas (crsf)](https://docs.djangoproject.com/en/2.0/ref/csrf/) do Django (documentos do Django). Geralmente você adiciona essa marca a qualquer elemento que envolva métodos de solicitação POST, PUT ou DELETE, como um formulário, e a função de renderização do modelo (`render`) insere a proteção necessária.

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Usar o modelo Pesquisas Projeto Web do Django](learn-django-in-visual-studio-step-06-polls-django-web-project-template.md)

## <a name="going-deeper"></a>Aprofundando-se

- [Autenticação de usuário no Django](https://docs.djangoproject.com/en/2.0/topics/auth/) (docs.djangoproject.com)
- Código-fonte do tutorial no GitHub: [Microsoft/python-sample-vs-learn-django](https://github.com/Microsoft/python-sample-vs-learn-django)