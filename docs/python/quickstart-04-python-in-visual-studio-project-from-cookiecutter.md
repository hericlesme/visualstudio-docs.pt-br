---
title: "Início rápido: Criar um projeto Python usando o Cookiecutter no Visual Studio | Microsoft Docs"
description: Comece a utilizar rapidamente o Python usando um modelo de Cookiecutter no Visual Studio.
ms.custom: 
ms.date: 09/22/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
dev_langs:
- python
ms.tgt_pltfrm: 
ms.topic: quickstart
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload:
- python
- data-science
ms.openlocfilehash: 4b9b7a51436eeeb67634714216f9a583de679a07
ms.sourcegitcommit: c0a2385a16cc4f47d2e1ff23d35c4da40f5605e0
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/23/2018
---
# <a name="quickstart-create-a-project-from-a-cookiecutter-template"></a>Início rápido: criar um projeto por meio de um modelo do Cookiecutter

Depois de [instalar o suporte ao Python no Visual Studio 2017](installing-python-support-in-visual-studio.md), é fácil criar um novo projeto com base em um modelo do Cookiecutter, incluindo os vários modelos que estão publicados no GitHub. O [Cookiecutter](https://cookiecutter.readthedocs.io/en/latest/) fornece uma interface gráfica do usuário para descobrir modelos e opções de modelo de entrada e criar projetos e arquivos. Ele é incluído no Visual Studio 2017 e pode ser instalado separadamente em versões anteriores do Visual Studio.

1. Para este guia de início rápido, primeiro instale a distribuição Anaconda3 do Python, que inclui os pacotes do Python necessários para o modelo do Cookiecutter que será mostrado aqui. Execute o instalador do Visual Studio, selecione **Modificar**, expanda as opções de **Desenvolvimento do Python** no lado direito e selecione "Anaconda3" (32 bits ou 64 bits). Observe que a instalação poderá levar algum tempo, dependendo da velocidade da Internet, mas essa é a maneira mais simples de instalar os pacotes necessários.

1. Inicie o Visual Studio.

1. Selecione **Arquivo > Novo > De Cookiecutter...**. Esse comando abre uma janela no Visual Studio, na qual você pode procurar modelos. 

    ![Novo projeto de modelo do Cookiecutter](media/projects-from-cookiecutter1.png)

1. Selecione o modelo "Microsoft/python-sklearn-classifier-cookiecutter" e, em seguida, selecione **Avançar**. (O processo poderá levar vários minutos na primeira vez que você usar Cookiecutter).

1. Na próxima etapa, defina um local para o novo projeto no campo **Criar Para** e, em seguida, selecione **Criar**.

    ![Segunda etapa usando o Cookiecutter, configurando propriedades do projeto](media/projects-from-cookiecutter2.png)

1. Quando o processo for concluído, você verá a mensagem "Arquivos criados com êxito". Selecione o comando **Abrir no Gerenciador de Soluções** para abrir o projeto.

1. Pressione Ctrl+F5 ou selecione **Depurar > Iniciar Sem Depuração** para executar o programa. 

    ![Saída do projeto do modelo python-sklearn-classifier-cookiecutter](media/projects-from-cookiecutter4.png)

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Tutorial: trabalhando com o Python no Visual Studio](tutorial-working-with-python-in-visual-studio-step-01-create-project.md)

## <a name="see-also"></a>Consulte também

- [Usando a extensão Cookiecutter](using-python-cookiecutter-templates.md)
- [Identificar manualmente um interpretador Python existente](managing-python-environments-in-visual-studio.md#manually-identifying-an-existing-environment).
- [Instalar o suporte do Python no Visual Studio 2015 e anterior](installing-python-support-in-visual-studio.md).
- [Locais de instalação](installing-python-support-in-visual-studio.md#install-locations).
