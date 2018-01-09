---
title: "Início rápido: criar um projeto do Python com base em um modelo do Cookiecutter no Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 09/22/2017
ms.reviewer: 
ms.suite: 
ms.technology: devlang-python
ms.devlang: python
ms.tgt_pltfrm: 
ms.topic: article
caps.latest.revision: "1"
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload: python
ms.openlocfilehash: d0b21c78ab31c093ef48300ac746c3c2fd7d6778
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="quickstart-create-a-project-from-a-cookiecutter-template"></a>Início rápido: criar um projeto por meio de um modelo do Cookiecutter

Depois de [instalar o suporte ao Python no Visual Studio 2017](installation.md), é fácil criar um novo projeto com base em um modelo do Cookiecutter, incluindo os vários modelos que estão publicados no GitHub. O [Cookiecutter](https://cookiecutter.readthedocs.io/en/latest/) fornece uma interface gráfica do usuário para descobrir modelos e opções de modelo de entrada e criar projetos e arquivos. Ele é incluído no Visual Studio 2017 e pode ser instalado separadamente em versões anteriores do Visual Studio.

1. Para este guia de início rápido, primeiro instale a distribuição Anaconda3 do Python, que inclui os pacotes do Python necessários para o modelo do Cookiecutter que será mostrado aqui. Execute o instalador do Visual Studio, selecione **Modificar**, expanda as opções de **Desenvolvimento do Python** no lado direito e selecione "Anaconda3" (32 bits ou 64 bits). Observe que a instalação poderá levar algum tempo, dependendo da velocidade da Internet, mas essa é a maneira mais simples de instalar os pacotes necessários.

1. Inicie o Visual Studio.

1. Selecione **Arquivo > Novo > De Cookiecutter...**. Esse comando abre uma janela no Visual Studio, na qual você pode procurar modelos. 

    ![Novo projeto de modelo do Cookiecutter](media/projects-from-cookiecutter1.png)

1. Selecione o modelo "Microsoft/python-sklearn-classifier-cookiecutter" e, em seguida, selecione **Avançar**. (O processo poderá levar vários minutos na primeira vez que você usar Cookiecutter).

1. Na próxima etapa, defina um local para o novo projeto no campo **Criar Para** e, em seguida, selecione **Criar**.

    ![Segunda etapa usando o Cookiecutter, configurando propriedades do projeto](media/projects-from-cookiecutter2.png)

1. Quando o processo for concluído, você verá a mensagem "Arquivos criados com êxito". Selecione o comando **Abrir no Gerenciador de Soluções** para abrir o projeto.

1. Pressione CTRL + F5 ou selecione **Depurar > Iniciar Sem Depuração** para executar o programa. 

    ![Saída do projeto do modelo python-sklearn-classifier-cookiecutter](media/projects-from-cookiecutter4.png)

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Tutorial: trabalhando com o Python no Visual Studio](vs-tutorial-01-01.md)

## <a name="see-also"></a>Consulte também

- [Usando a extensão Cookiecutter](cookiecutter.md)
- [Criando um ambiente para um interpretador do Python existente](python-environments.md#creating-an-environment-for-an-existing-interpreter).
- [Instalar o suporte do Python no Visual Studio 2015 e anterior](installation.md).
- [Locais de instalação](installation.md#install-locations).
