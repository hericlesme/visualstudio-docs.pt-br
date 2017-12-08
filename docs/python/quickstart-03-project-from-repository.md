---
title: "Início Rápido: clonar um repositório de código do Python no Visual Studio | Microsoft Docs"
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
ms.openlocfilehash: 3ea3afdaa6a7a29bc85c46b6eff0f15c5c91c046
ms.sourcegitcommit: b7d3b90d0be597c9d01879338dd2678c881087ce
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/01/2017
---
# <a name="quickstart-clone-a-repository-of-python-code-in-visual-studio"></a>Início Rápido: clonar um repositório de código do Python no Visual Studio

Depois de [instalar o suporte ao Python no Visual Studio 2017](installation.md), você poderá facilmente clonar um repositório de código do Python e criar um projeto com base nele.

[!INCLUDE[install-github-extension](includes/install-github-extension.md)]

2. Inicie o Visual Studio.

3. Selecione **Exibir > Team Explorer...** para abrir a janela do **Team Explorer** em que é possível se conectar ao GitHub ou ao Visual Studio Team Services ou clonar um repositório.

    ![Janela do Team Explorer mostrando o Visual Studio Team Services, o GitHub e a clonagem de um repositório](media/team-explorer.png)

4. No campo de URL em **Repositórios Git Locais**, insira `https://github.com/gregmalcolm/python_koans`, insira uma pasta para os arquivos clonados e selecione **Clonar**.

    > [!Tip]
    > A pasta especificada no Team Explorer é a pasta específica para receber os arquivos clonados. Ao contrário do comando `git clone`, criar um clone no Team Explorer não cria automaticamente uma subpasta com o nome do repositório.

5. Quando a clonagem for concluída, clique duas vezes na pasta do repositório na parte inferior do Team Explorer, para navegar até o dashboard do repositório. Em **Soluções**, selecione **Nova...** .

    ![Janela do Team Explorer, criando um novo projeto com base em um clone](media/team-explorer-new-project.png)

6. Na caixa de diálogo **Novo Projeto** que é exibida, selecione "Do código Python Existente", especifique um nome para o projeto, defina **Local** como a mesma pasta que o repositório e selecione **OK**. No assistente que é exibido, selecione **Concluir**.

7. Selecione **Exibir > Gerenciador de Soluções** no menu.

8. No Gerenciador de Soluções, expanda o nó `python3`, clique com botão direito do mouse em `contemplate_koans.py` e selecione **Definir como Arquivo de Inicialização**. Esta etapa informa ao Visual Studio qual arquivo deve ser usado ao executar o projeto.

9. Selecione **Projeto > Propriedades** no menu, selecione a guia **Geral** e defina o **Diretório de Trabalho** como "python3". Isso é necessário porque, por padrão, o Visual Studio define o diretório de trabalho como a raiz do projeto em vez do local do arquivo de inicialização (`python3\contemplate_koans.py`, que você também pode ver nas propriedades do projeto). O código do programa procurará um arquivo `koans.txt` na pasta de trabalho, portanto sem a alteração desse valor, você verá um erro de tempo de execução.

    ![Configurar o diretório de trabalho para um projeto do Python](media/projects-set-working-directory.png)

10. Pressione CTRL + F5 ou selecione **Depurar > Iniciar Sem Depuração** para executar o programa. Se você vir um `FileNotFoundError` para `koans.txt`, verifique novamente a configuração do diretório de trabalho na etapa anterior.

11. Quando o programa é executado com êxito, ele exibe um erro de asserção na linha 17 do `python3/koans/about_asserts.py`. Isso é intencional: o programa foi projetado para ensinar Python, fazendo com que você corrija todos os erros intencionais. (Mais detalhes são encontrados em [Ruby Koans](http://rubykoans.com/), que inspirou os Koans do Python).

    ![Primeira saída do programa koans do Python](media/koans-output.png)

12. Abra `python3/koans/about_asserts.py`, navegando até ele no Gerenciador de Soluções e clique duas vezes no arquivo. Observe que os números de linha não aparecem no editor por padrão. Para alterar isso, selecione **Ferramentas > Opções**, selecione **Mostrar todas as configurações** na parte inferior da caixa de diálogo, navegue até **Editor de Texto > Python > Geral** e selecione **Números de linha**:

    ![Ativando o número de linha para arquivos do Python](media/options-general-line-numbers.png)

13. Corrija o erro, alterando o argumento `False` na linha 17 para `True`. A linha deve ficar assim:

    ```python
    self.assertTrue(True) # This should be True
    ```

14. Execute o programa novamente para ver se a primeira verificação passa e o programa é interrompido no próximo koan. Continue corrigindo os erros e executando novamente o programa se quiser.

> [!Important]
> Neste guia de início rápido, você criou um clone direto do repositório *python_koans* no GitHub. Esse tipo de repositório é protegido pelo autor contra alterações diretas, portanto, a tentativa de confirmar as alterações no repositório falhará. Na prática, os desenvolvedores criam fork desse tipo de repositório em suas próprias contas do GitHub, fazem as alterações ali mesmo e, em seguida, criam solicitações de pull para enviar essas alterações para o repositório original. Essas etapas estão descritas na [Etapa 6 do tutorial – trabalhando com o Git](vs-tutorial-01-06.md).

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Tutorial: trabalhando com o Python no Visual Studio](vs-tutorial-01-01.md)

## <a name="see-also"></a>Consulte também

- [Criando um ambiente para um interpretador do Python existente](python-environments.md#creating-an-environment-for-an-existing-interpreter).
- [Instalar o suporte do Python no Visual Studio 2015 e anterior](installation.md).
- [Locais de instalação](installation.md#install-locations).