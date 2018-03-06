---
title: Selecionar um ambiente para um projeto | Microsoft Docs
description: "No Gerenciador de Soluções do Visual Studio, você pode atribuir um interpretador do Python específico (ambiente) a ser usado para qualquer projeto, ignorando o ambiente padrão. Você também pode criar e gerenciar ambientes virtuais."
ms.custom: 
ms.date: 02/20/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.devlang: python
ms.tgt_pltfrm: 
ms.topic: article
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload:
- python
- data-science
ms.openlocfilehash: 6f422cc60638b7eed4a5b42516e7496c4a6f6209
ms.sourcegitcommit: c0a2385a16cc4f47d2e1ff23d35c4da40f5605e0
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/23/2018
---
# <a name="selecting-a-python-interpreter-and-environment-for-use-in-a-project"></a>Selecionar um intérprete e ambiente Python para uso em um projeto

Todo o código em um projeto do Python é executado dentro do contexto de um ambiente específico. O Visual Studio também utiliza esse ambiente para depuração, preenchimentos de importação e membro, verificação de sintaxe e todas as outras tarefas que exigem um ambiente.

Todos os novos projetos do Python no Visual Studio são inicialmente configurados para usar o ambiente padrão global, que aparece sob o nó **Ambientes de Python** no Gerenciador de Soluções:

![O ambiente de Python global padrão mostrado no Gerenciador de Soluções](media/environments-project.png)

Você pode disponibilizar outros ambientes para o projeto, incluindo ambientes virtuais. Só pode haver um ambiente ativado em um determinado momento.

## <a name="using-global-environments"></a>Uso de ambientes globais

Para disponibilizar ambientes globais específicos para o projeto (incluindo ambientes conda [identificados manualmente](managing-python-environments-in-visual-studio.md#manually-identifying-an-existing-environment)), clique com o botão direito do mouse no nó **Ambientes do Python** e selecione **Adicionar/Remover Ambientes de Python...**. Na lista exibida, selecione os ambientes desejados:

![Caixa de diálogo Adicionar/Remover Ambientes do Python](media/environments-add-remove.png)

Depois de selecionar **OK**, todos os ambientes selecionados aparecem no nó **Ambientes de Python**. O ambiente ativado no momento aparece em negrito:

![Vários ambiente de Python mostrados no Gerenciador de Soluções](media/environments-project-multiple.png)

Para ativar outro ambiente, clique com o botão direito do mouse no nome desse ambiente e selecione **Ativar Ambiente**. Sua escolha é salva com o projeto e esse ambiente é ativado sempre que você abrir o projeto futuramente.

Se você desmarcar todas as opções na caixa de diálogo **Adicionar/Remover Ambientes de Python** , o Visual Studio ativa o ambiente padrão global.

## <a name="using-virtual-environments"></a>Usar ambientes virtuais

Um ambiente virtual é uma combinação exclusiva de um intérprete Python específico e um conjunto específico de bibliotecas diferente de outros ambientes conda e globais. Geralmente, você usa um ambiente virtual quando tiver necessidades específicas em um projeto e não quiser modificar outros ambientes para atender a essas necessidades.

Depois que um ambiente virtual é adicionado ao projeto, ele é exibido na janela **Ambientes do Python** e é possível ativá-lo como qualquer outro ambiente, além de gerenciar seus pacotes.

Observe que uma desvantagem dos ambientes virtuais é que eles contêm caminhos de arquivo embutidos em código e, portanto, não podem ser facilmente compartilhados nem transportados para outras máquinas de desenvolvimento. Felizmente, você pode usar o arquivo `requirements.txt` para permitir que os destinatários de seu projeto restaurem facilmente o ambiente. Para saber mais, veja [Gerenciar pacotes necessários com requirements.txt](managing-required-packages-with-requirements-txt.md).

### <a name="activating-an-existing-virtual-environment"></a>Ativar um ambiente virtual existente

Se você já tiver criado um ambiente virtual em outro lugar, você poderá ativá-lo para um projeto da seguinte maneira:

1. Clique com o botão direito do mouse em **Ambientes do Python** no Gerenciador de Soluções e selecione **Adicionar Ambiente Virtual Existente...**.

1. Na caixa de diálogo **Procurar** que aparece, navegue até a pasta que contém o ambiente virtual, selecione-a e selecione **OK**. Se o Visual Studio detectar um arquivo `requirements.txt` nesse ambiente, ele perguntará se deve instalar esses pacotes.

1. Após alguns instantes, o ambiente virtual aparece sob o nó **Ambientes de Python** no Gerenciador de Soluções. O ambiente virtual não está ativado por padrão, então clique duas vezes e selecione **Ativar Ambiente**.

### <a name="creating-a-virtual-environment"></a>Criando um ambiente virtual

Você pode criar um novo ambiente virtual diretamente do Visual Studio da seguinte maneira:

1. Clique com o botão direito do mouse em **Ambientes do Python** no Gerenciador de Soluções e selecione **Adicionar Ambiente Virtual...**, que abre a seguinte caixa de diálogo:

    ![Criando um ambiente virtual](media/environments-add-virtual-1.png)

1. No **local do ambiente virtual**, especifique um caminho para o ambiente virtual. Se você especificar apenas um nome, o ambiente virtual será criado dentro do projeto atual em uma subpasta com o mesmo nome.

1. Selecione um ambiente como o interpretador base e selecione **Criar**. O Visual Studio exibe uma barra de progresso enquanto configura o ambiente, e baixa todos os pacotes necessários. Neste ponto, o ambiente virtual aparece na janela **Ambientes de Python** para o projeto que o contém.

1. O ambiente virtual não está ativado por padrão. Para ativá-lo para o projeto, clique com o botão direito e selecione **Ativar Ambiente**.

> [!Note]
> Se o caminho do local identificar um ambiente virtual existente, o Visual Studio detectará automaticamente o interpretador base (usando o arquivo `orig-prefix.txt` no diretório `lib` do ambiente) e altera o botão Criar para **Adicionar**.
>
> Se existir um arquivo `requirements.txt` ao adicionar um ambiente virtual, a caixa de diálogo **Adicionar Ambiente Virtual** exibirá uma opção para instalar os pacotes automaticamente, facilitando a recriação de um ambiente em outra máquina:
>
> ![Criar um ambiente virtual com requirements.txt](media/environments-requirements-txt.png)
>
> De qualquer forma, o resultado será como se você tivesse usado o comando **Adicionar Ambiente Virtual Existente...**.

### <a name="remove-a-virtual-environment"></a>Remover um ambiente virtual

1. No Gerenciador de Soluções, clique com o botão direito do mouse no ambiente virtual e selecione **Remover**.

1. O Visual Studio pergunta se você quer remover ou excluir o ambiente virtual. Selecionar **Remover** o torna indisponível ao projeto, mas o deixa no sistema de arquivos. Selecionar **Excluir** remove o ambiente do projeto e o exclui do sistema de arquivos. O interpretador de base não é afetado.

## <a name="viewing-installed-packages"></a>Ver os pacotes instalados

No Gerenciador de Soluções, expanda qualquer nó de um ambiente específico para exibir rapidamente os pacotes instalados nesse ambiente (ou seja, você não pode importar e usar esses pacotes em seu código quando o ambiente estiver ativo):

![Pacotes do Python para um ambiente no Gerenciador de Soluções](media/environments-installed-packages.png)

Para instalar novos pacotes, clique com o botão direito no ambiente e selecione **Instalar Pacote da Python...** para alternar para a guia **Pacotes** na janela **Ambientes de Python**. Insira uma termo de pesquisa (geralmente o nome do pacote) e o Visual Studio exibirá os pacotes correspondentes.

No Visual Studio, os pacotes (e as dependências) são baixados no [PyPI (Índice do Pacote do Python)](https://pypi.python.org/pypi), no qual você também pode pesquisar os pacotes disponíveis. A barra de status e a janela de saída do Visual Studio mostram informações sobre a instalação. Para desinstalar um pacote, clique com o botão direito do mouse nele e selecione **Remover**.

Saiba que as entradas exibidas podem não ser precisas e a instalação e desinstalação podem não ser confiáveis nem estar disponíveis. O Visual Studio usa o gerenciador de pacotes do PIP, se disponível, e o baixa e o instala quando necessário. O Visual Studio também pode usar o gerenciador de pacotes easy_install. Os pacotes instalados usando `pip` ou `easy_install` por meio da linha de comando também são exibidos.

Observe também que o Visual Studio não oferece suporte no momento ao uso de `conda` para instalar os pacotes em um ambiente conda. Use `conda` na linha de comando.

> [!Tip]
> Uma situação comum em que o PIP não conseguirá instalar um pacote é quando o pacote inclui o código-fonte para componentes nativos em arquivos `*.pyd`. Sem a versão necessária do Visual Studio instalada, o PIP não pode compilar esses componentes. A mensagem de erro exibida nessa situação é `error: Unable to find vcvarsall.bat`. O `easy_install` consegue baixar os binários pré-compilados e é possível baixar um compilador adequado para versões mais antigas do Python em [http://aka.ms/VCPython27](http://aka.ms/VCPython27). Para obter mais detalhes, consulte [Como lidar com o problema “Não é possível localizar vcvarsallbat”](https://blogs.msdn.microsoft.com/pythonengineering/2016/04/11/unable-to-find-vcvarsall-bat/) no blog da equipe das Ferramentas Python.

## <a name="see-also"></a>Consulte também

- [Gerenciando ambientes do Python no Visual Studio](managing-python-environments-in-visual-studio.md)
- [Usando requirements.txt para dependências](managing-required-packages-with-requirements-txt.md)
- [Caminhos de pesquisa](search-paths.md)
- [Referência à janela Ambientes do Python](python-environments-window-tab-reference.md)