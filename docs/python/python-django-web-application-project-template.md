---
title: Modelo de projeto Web do Django para Python
description: Uma visão geral dos modelos do Visual Studio para aplicativos Web escritos em Python usando a estrutura Django.
ms.date: 04/17/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- python
- data-science
ms.openlocfilehash: 077619b7d47441bb4a02dbe87e7cf714b634beff
ms.sourcegitcommit: 928885ace538bef5b25961358d4f166d648f196a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/27/2018
ms.locfileid: "32031342"
---
# <a name="django-web-project-template"></a>Modelo de projeto Web Django

O [Django](https://www.djangoproject.com/) é uma estrutura do Python de alto nível projetada para um desenvolvimento da Web rápido, seguro e escalonável. O suporte do Python no Visual Studio fornece vários modelos de projeto para configurar a estrutura de um aplicativo Web baseado em Django. Para usar um modelo no Visual Studio, selecione **Arquivo** > **Novo** > **Projeto**, pesquise "Django" e selecione dentre os modelos "Projeto Web do Django em branco", "Projeto Web do Django" e "Pesquisas Projeto Web do Django". Consulte o [Tutorial de aprendizagem do Django](learn-django-in-visual-studio-step-01-project-and-solution.md) para obter um passo a passo de todos os modelos.

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

- **Coletar Estáticos**: executa `manage.py collectstatic --noinput` para copiar todos os arquivos estáticos para o caminho especificado por `STATIC_ROOT` em `settings.py`. Ao [publicar no Serviço de Aplicativo do Azure](publishing-python-web-applications-to-azure-from-visual-studio.md), os arquivos estáticos são coletados automaticamente como parte da operação de publicação.

    ![Console](media/template-django-console-collect-static.png)

- **Validar**: executa `manage.py validate`, que relata os erros de validação nos modelos instalados especificados por `INSTALLED_APPS` em `settings.py`:

    ![Console](media/template-django-console-validate.png)

## <a name="see-also"></a>Consulte também

- [Tutorial de aprendizagem do Django](learn-django-in-visual-studio-step-01-project-and-solution.md)