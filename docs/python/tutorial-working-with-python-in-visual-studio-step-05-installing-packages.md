---
title: "Trabalhar com o Python no Visual Studio, Etapa 5 – Instalação de pacotes | Microsoft Docs"
description: "Etapa 5 de um tutorial básico para trabalhar com Python no Visual Studio, demonstrando recursos do Visual Studio para gerenciamento de pacotes em um ambiente Python."
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
ms.openlocfilehash: bb0890d5f9433e1f73039e4036b884d7bfcb7933
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/09/2018
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

1. Crie um novo projeto com **Arquivo > Novo > Projeto**, selecionando o modelo de "Aplicativo do Python". No arquivo de código que é exibido, cole o código a seguir, que cria uma curva de cosseno como nas etapas anteriores do tutorial, só que plotada graficamente desta vez:

    ```python
    import numpy as np     # installed with matplotlib
    import matplotlib.pyplot as plt
    from math import radians

    def main():
        x = np.arange(0, radians(1800), radians(12))
        plt.plot(x, np.cos(x), 'b')
        plt.show()

    main()
    ```

1. Execute o programa com (F5) ou sem o depurador (CTRL + F5) para ver a saída:

  ![Saída de exemplo de matplotlib](media/environments-add-matplotlib3.png)

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Trabalhando com Git](tutorial-working-with-python-in-visual-studio-step-06-working-with-git.md)

### <a name="going-deeper"></a>Aprofundando-se

- [Ambientes do Python](managing-python-environments-in-visual-studio.md)
