---
title: Trabalhar com o Python no Visual Studio, Etapa 6, Trabalhar com o Git | Microsoft Docs
description: "Etapa 6 de um tutorial básico para trabalhar com Python no Visual Studio, abordando os recursos relacionados ao Git do Visual Studio."
ms.custom: 
ms.date: 01/16/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
dev_langs:
- python
ms.tgt_pltfrm: 
ms.topic: tutorial
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload:
- python
- data-science
ms.openlocfilehash: ef143862c56f07edc844874bbf71cd916ac9eabc
ms.sourcegitcommit: 39c525ec200c6c4ea94815567b3fad7ab14fb7b3
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/08/2018
---
# <a name="step-6-working-with-git"></a>Etapa 6: trabalhando com Git

**Etapa anterior: [instalando pacotes e gerenciando o ambiente do Python](tutorial-working-with-python-in-visual-studio-step-05-installing-packages.md)**

O Visual Studio fornece integração direta com repositórios locais do Git, bem como integração com aqueles que residem em serviços como GitHub e Visual Studio Team Services. A integração inclui clonagem de um repositório, confirmação de alterações e gerenciamento de branches.

Este artigo descreve a criação de um repositório local do Git para um projeto existente. Para instruções passo a passo sobre a criação de um projeto de um repositório remoto do Git, consulte [Início Rápido: clonar um repositório de código do Python no Visual Studio](quickstart-03-python-in-visual-studio-project-from-repository.md).

1. Com um projeto aberto no Visual Studio, como o projeto da [etapa anterior](tutorial-working-with-python-in-visual-studio-step-05-installing-packages.md), clique com o botão direito do mouse na solução e selecione **Adicionar Solução ao Controle do Código-Fonte**. O Visual Studio cria um repositório local do Git que contém o código do projeto e controles relacionados com o Git também aparecem na parte inferior da janela do Visual Studio. Os controles mostram confirmações pendentes, alterações, o nome do repositório e o branch. Passe o mouse sobre os controles para ver informações adicionais.

  ![Informações adicionais são exibidas ao passar o mouse sobre um controle de Git na janela do Visual Studio](media/working-with-git-01.png)

1. A janela **Team Explorer** também é exibida com várias opções de Git disponíveis ao selecionar o cabeçalho do repositório. O painel **Sincronizar**, mostrado quando você seleciona o cabeçalho **Push**, fornece opções para publicar em um repositório remoto.

  ![Team Explorer no Visual Studio depois de criar um repositório local](media/working-with-git-02.png)

1. Selecione **Alterações** para examinar as alterações não confirmadas e confirmá-las quando desejado.

  ![Team Explorer no Visual Studio mostrando as alterações não confirmadas](media/working-with-git-03.png)

1. Selecione **Branches** para examinar os branches e executar operações de mesclagem e troca de base:

  ![Team Explorer no Visual Studio mostrando branches](media/working-with-git-04.png)

1. Ao usar um repositório local, as alterações confirmadas vão diretamente para o repositório. Se você estiver conectado a um repositório remoto, selecione o cabeçalho, escolha **Sincronizar** para mudar para a seção **Sincronização** e trabalhar com os comandos apresentados.

## <a name="going-deeper"></a>Aprofundando-se

Para obter um tutorial mais abrangente sobre como trabalhar com Git, consulte [Compartilhar seu código com o Git do Visual Studio 2017 e do VSTS](/vsts/git/share-your-code-in-git-vs-2017)

## <a name="tutorial-review"></a>Análise do tutorial

Parabéns por concluir este tutorial sobre Python no Visual Studio. Neste tutorial, você aprendeu como:

- Criar projetos e exibir o conteúdo do projeto.
- Use o editor de código e executar um projeto.
- Use a janela interativa para desenvolver novo código e copiar facilmente esse código no editor.
- Executar um programa concluído no depurador do Visual Studio.
- Instalar pacotes e gerenciar ambientes do Python
- Trabalhar com o código em um repositório do Git

Agora, explore os conceitos e guias de instruções, incluindo o seguinte:

- [Criando uma extensão do C++ para o Python](working-with-c-cpp-python-in-visual-studio.md)
- [Publicando no Serviço de Aplicativo do Azure](publishing-python-web-applications-to-azure-from-visual-studio.md)
- [Criação de perfil](profiling-python-code-in-visual-studio.md)
- [Teste de unidade](unit-testing-python-in-visual-studio.md)
