---
ms.topic: include
ms.openlocfilehash: 37079cfaa1204cd8ce7a77e1e2f5aa91ea844ea5
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/19/2018
---
1. Inicie o Visual Studio e selecione **Arquivo > Novo > Projeto**.

1. Na caixa de diálogo **Novo Projeto**, pesquise "Python", selecione o modelo "Do código Python existente", forneça um nome e um local para o projeto e selecione **OK**.

1. No assistente que é exibido, defina o caminho para o código existente, defina um filtro para os tipos de arquivo e especifique os caminhos de pesquisa que seu projeto requer. Em seguida, selecione **Avançar**. Se você não souber o que são caminhos de pesquisa, deixe esse campo em branco.

    ![Novo Projeto com base em um Código Existente, etapa 1](../media/projects-from-existing-1.png)

1. Na próxima caixa de diálogo, escolha o arquivo de inicialização do projeto e selecione **Avançar**. (Se desejar, selecione um ambiente, caso contrário, aceite os padrões.) Observe que a caixa de diálogo mostra somente os arquivos na pasta raiz. Se o arquivo desejado estiver em uma subpasta, deixe o arquivo de inicialização em branco e defina-o mais tarde no Gerenciador de Soluções (descrito abaixo).

    ![Novo Projeto com base em um Código Existente, etapa 2](../media/projects-from-existing-2.png)

1. Selecione o local no qual deseja salvar o arquivo de projeto (que é um arquivo `.pyproj` no disco). Caso se aplique, também será possível incluir a detecção automática de ambientes virtuais e personalizar o projeto para outras estruturas da Web. Se você não tiver certeza sobre essas opções, deixe-as com as configurações padrão.

    ![Novo Projeto com base em um Código Existente, etapa 3](../media/projects-from-existing-3.png)

1. Selecione **Concluir** e o Visual Studio criará o projeto e o abrirá no Gerenciador de Soluções. Se desejar mover o arquivo `.pyproj` para outro lugar, selecione-o no Gerenciador de Soluções e escolha **Arquivo > Salvar Como**. Essa ação atualiza as referências de arquivo no projeto, mas não move nenhum arquivo de código.

1. Para definir um arquivo de inicialização diferente, localize o arquivo no Gerenciador de Soluções, clique com o botão direito do mouse e selecione **Definir como Arquivo de Inicialização**.