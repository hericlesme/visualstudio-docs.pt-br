---
title: Trabalhando com o Tutorial do Python, etapa 5, instalar pacotes
description: Etapa 5 de um passo a passo básico das funcionalidades do Python no Visual Studio, demonstrando os recursos do Visual Studio para gerenciar pacotes em um ambiente Python.
ms.date: 03/05/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: tutorial
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- python
- data-science
ms.openlocfilehash: 205af005071c86b7e86dcc465918fccc7243690c
ms.sourcegitcommit: 928885ace538bef5b25961358d4f166d648f196a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/27/2018
---
# <a name="step-5-installing-packages-in-your-python-environment"></a>Etapa 5: instalando pacotes no ambiente do Python

**Etapa anterior: [executando o código no depurador](tutorial-working-with-python-in-visual-studio-step-04-debugging.md)**

A comunidade de desenvolvedores do Python produziu milhares de pacotes úteis que você pode incorporar em seus próprios projetos. O Visual Studio oferece uma interface do usuário para gerenciar pacotes em seus ambientes do Python.

1. Selecione o comando de menu **Exibir > Outras Janelas > Ambientes do Python**. A janela **Ambientes do Python** será aberta como um par com o Gerenciador de Soluções e mostrará os diferentes ambientes disponíveis para você. A lista inclui os ambientes em que você instalou usando o instalador do Visual Studio e os que você instalou separadamente. O ambiente em negrito é o ambiente padrão, que é usado para novos projetos.

  ![Janela Ambientes do Python](media/environments-default-view-blue.png)

1. A guia **Visão geral** proporciona acesso rápido a uma janela interativa do ambiente, junto com a pasta de instalação e os interpretadores desse ambiente. Por exemplo, selecione **Abrir janela interativa** e uma janela interativa desse ambiente específico será exibida no Visual Studio.

1. Selecione a guia **Pacotes** e você verá uma lista dos pacotes que estão atualmente instalados no ambiente.

  ![Pacotes instalados em um ambiente](media/environments-installed-packages-blue.png)

1. Para instalar o `matplotlib`, digite seu nome no campo de pesquisa e, em seguida, selecione o `pip install`

  ![Instalação do matplotlib no ambiente](media/environments-add-matplotlib1.png)

1. Dê permissão para a elevação, se for solicitado.

1. Depois de instalar o pacote, ele aparecerá na janela Ambientes do Python. O **X** à direita do pacote serve para desinstalá-lo.

  ![Conclusão da instalação do matplotlib no ambiente](media/environments-add-matplotlib2.png)

  A pequena barra de progresso sob o ambiente indica que o Visual Studio está compilando o banco de dados do IntelliSense para o pacote recém-instalado. A guia **IntelliSense** também mostra mais informações detalhadas. Observe que, até que o banco de dados seja concluído, os recursos do IntelliSense, como preenchimento automático e verificação de sintaxe, não estarão ativos no editor para esse pacote.

  Observe que o **Visual Studio 2017 versão 15.6** e posterior usa um método diferente e mais rápido para trabalhar com o IntelliSense e exibe uma mensagem para esse efeito na guia **IntelliSense**.

1. Crie um novo projeto com **Arquivo > Novo > Projeto**, selecionando o modelo de "Aplicativo do Python". No arquivo de código que é exibido, cole o código a seguir, que cria uma curva de cosseno como nas etapas anteriores do tutorial, só que plotada graficamente desta vez:

    ```python
    from math import radians
    import numpy as np     # installed with matplotlib
    import matplotlib.pyplot as plt

    def main():
        x = np.arange(0, radians(1800), radians(12))
        plt.plot(x, np.cos(x), 'b')
        plt.show()

    main()
    ```

1. Execute o programa com (F5) ou sem o depurador (CTRL + F5) para ver a saída:

  ![Saída de exemplo de matplotlib](media/environments-add-matplotlib3.png)

## <a name="next-step"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Trabalhando com Git](tutorial-working-with-python-in-visual-studio-step-06-working-with-git.md)

### <a name="going-deeper"></a>Aprofundando-se

- [Ambientes do Python](managing-python-environments-in-visual-studio.md)
