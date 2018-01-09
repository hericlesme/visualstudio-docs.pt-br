---
title: "Início rápido: criar um projeto do Python com base em um modelo no Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 09/25/2017
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
ms.openlocfilehash: ee329df0bda8869215969941024deba6d94743fe
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="quickstart-create-a-python-project-from-a-template-in-visual-studio"></a>Início rápido: criar um projeto do Python com base em um modelo no Visual Studio

Depois de [instalar o suporte ao Python no Visual Studio 2017](installation.md), é fácil criar um novo projeto do Python usando uma variedade de modelos.

1. Inicie o Visual Studio.

1. Selecione **Arquivo > Novo > Projeto** (CTRL + SHIFT + N). Na caixa de diálogo **Novo Projeto**, pesquise por "Python" e selecione o modelo desejado. Observe que a seleção de um modelo exibe uma breve descrição do que o modelo fornece. (Consulte também [Projetos do Python](python-projects.md#project-templates).)

    ![Caixa de diálogo de Novo Projeto com modelo do Python do VS2017](media/projects-new-project-dialog2.png)

1. Para este guia de início rápido, selecione o modelo "Aplicativo do Python", defina um local e um nome para o projeto (por exemplo, "MakePI") e selecione **OK**. 

1. O Visual Studio cria o arquivo de projeto (um arquivo `.pyproj` no disco) juntamente com outros arquivos, conforme descrito pelo modelo. Com o modelo "Aplicativo do Python", o projeto contém apenas um arquivo vazio com o mesmo nome que seu projeto. O arquivo é aberto no editor do Visual Studio, por padrão.

    ![Projeto resultante ao usar o modelo de aplicativo do Python](media/projects-new-structure.png)

1. Adicione código ao arquivo aberto, como o código abaixo que calcula e exibe 1.000 dígitos do PI:

    ```python
    """ Print digits of PI; code adapted from the second, shorter solution
    at http://www.codecodex.com/wiki/Calculate_digits_of_pi#Python
    """

    from time import perf_counter

    def pi_digits_Python(digits):
        scale = 10000
        maxarr = int((digits / 4) * 14)
        arrinit = 2000
        carry = 0
        arr = [arrinit] * (maxarr + 1)
        output = ""

        for i in range(maxarr, 1, -14):
            total = 0
            for j in range(i, 0, -1):
                total = (total * j) + (scale * arr[j])
                arr[j] = total % ((j * 2) - 1)
                total = total / ((j * 2) - 1)

            output += "%04d" % (carry + (total / scale))
            carry = total % scale

        return output;

    def test_py():
        digits = 1000;

        start = perf_counter()
        output = pi_digits_Python(digits);
        elapsed = perf_counter() - start;

        print("PI to " + str(digits) + " digits in " + str(int(elapsed * 10000)/10000) + " seconds:")

        ## replace inserts the decimal point
        print(output.replace("3", "3.", 1))

    if __name__ == "__main__":
        test_py();
    ```

1. Execute o programa pressionando CTRL + F5 ou selecionando **Depurar > Iniciar Sem Depuração** no menu. Os resultados são exibidos em uma janela do console.

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Tutorial: trabalhando com o Python no Visual Studio](vs-tutorial-01-01.md)

## <a name="see-also"></a>Consulte também

- [Criando um ambiente para um interpretador do Python existente](python-environments.md#creating-an-environment-for-an-existing-interpreter).
- [Instalar o suporte do Python no Visual Studio 2015 e anterior](installation.md).
- [Locais de instalação](installation.md#install-locations).
