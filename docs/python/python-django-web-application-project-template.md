---
title: Modelo de projeto Web do Django para o Python | Microsoft Docs
description: Uma visão geral dos modelos do Visual Studio para aplicativos Web escritos em Python usando a estrutura Django.
ms.custom: ''
ms.date: 07/13/2017
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-python
dev_langs:
- python
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.author: kraigb
manager: ghogen
ms.workload:
- python
- data-science
ms.openlocfilehash: 941ec5191e440be95d66da983508de36cef6d4fd
ms.sourcegitcommit: 29ef88fc7d1511f05e32e9c6e7433e184514330d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/28/2018
---
# <a name="django-web-project-template"></a>Modelo de projeto Web Django

O [Django](https://www.djangoproject.com/) é uma estrutura do Python de alto nível projetada para um desenvolvimento da Web rápido, seguro e escalonável. O suporte do Python no Visual Studio fornece um modelo de projeto para configurar a estrutura de um aplicativo Web baseado em Django. Para usar o modelo no Visual Studio, selecione **Arquivo > Novo > Projeto**, pesquise “Django” e selecione o modelo **Projeto Web do Django**. O projeto resultante inclui um código de texto clichê, bem como um banco de dados SQLite padrão. O modelo **Projeto Web em Branco do Django** é semelhante, mas não inclui o banco de dados.

O Visual Studio fornece o IntelliSense completo para projetos do Django:

- Variáveis de contexto passadas para o modelo:

    ![IntelliSense para variáveis de contexto](media/template-django-intellisense.png)

- Marcação e filtragem para elementos internos e definidos pelo usuário:

    ![IntelliSense para marcas e filtros](media/template-django-intellisense-filter.png)

- Realce de sintaxe para CSS e JavaScript inserido:

    ![CSS IntelliSense](media/template-django-intellisense-css.png)

    ![JavaScript IntelliSense](media/template-django-intellisense-js.png)

O Visual Studio também fornece [suporte de depuração](debugging-python-in-visual-studio.md) completo para projetos do Django: 

![Pontos de interrupção](media/template-django-debugging.png)

É comum para projetos do Django serem gerenciados por meio de seu arquivo `manage.py`, que é uma suposição que o Visual Studio segue. Se você parar de usar esse arquivo como o ponto de entrada, basicamente divide o arquivo de projeto. Nesse caso você precisa [recriar o projeto de arquivos existentes](managing-python-projects-in-visual-studio.md#creating-a-project-from-existing-files) sem marcá-lo como um projeto do Django.

## <a name="django-management-console"></a>Console de gerenciamento do Django

O console de gerenciamento do Django é acessado por meio de vários comandos no menu **Projeto** ou clicando com o botão direito do mouse no projeto, no Gerenciador de Soluções.

- **Abrir o Shell do Django...**: abre um shell no contexto do aplicativo que permite manipular os modelos"

    ![Console](media/template-django-console-shell.png)

- **Banco de Dados de Sincronização do Django**: executa `manage.py syncdb` em uma janela interativa:

    ![Console](media/template-django-console-sync-db.png)

- **Coletar Estáticos**: executa `manage.py collectstatic --noinput` para copiar todos os arquivos estáticos para o caminho especificado por `STATIC_ROOT` em `settings.py`. Observe que ao [publicar no Microsoft Azure](python-web-application-project-templates.md#publishing-to-azure-app-service), os arquivos estáticos são coletados automaticamente como parte da operação de publicação.

    ![Console](media/template-django-console-collect-static.png)

- **Validar**: executa `manage.py validate`, que relata os erros de validação nos modelos instalados especificados por `INSTALLED_APPS` em `settings.py`:

    ![Console](media/template-django-console-validate.png)