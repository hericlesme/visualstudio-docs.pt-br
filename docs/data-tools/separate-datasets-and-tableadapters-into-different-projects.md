---
title: Conjuntos de dados separados e TableAdapters em diferentes projetos
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- TableAdapters, n-tier applications
- n-tier applications, separating Datasets and TableAdapters
ms.assetid: f66a3940-6227-46af-a930-9177f425f4fd
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 691ff9c46e951f32bf8652d83a218f6c1e121382
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/19/2018
---
# <a name="separate-datasets-and-tableadapters-into-different-projects"></a>Conjuntos de dados separados e TableAdapters em diferentes projetos
Conjuntos de dados tipados foram aprimorados para que o [TableAdapters](create-and-configure-tableadapters.md) e classes de conjunto de dados podem ser geradas em projetos separados. Isso permite que você separe as camadas de aplicativo e gerar dados de n camadas aplicativos rapidamente.

O procedimento a seguir descreve o processo de usar o **Dataset Designer** para gerar o código do conjunto de dados em um projeto que é separado do projeto que contém o código gerado do TableAdapter.

## <a name="separate-datasets-and-tableadapters"></a>Conjuntos de dados separados e TableAdapters
Quando você separa o código do conjunto de dados do TableAdapter de código, o projeto que contém o código do conjunto de dados deve estar localizado na solução atual. Se este projeto não está na solução atual, ele não estará disponível no **projeto DataSet** lista o **propriedades** janela.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

#### <a name="to-separate-the-dataset-into-a-different-project"></a>Para separar o conjunto de dados em um projeto diferente

1.  Abra uma solução que contém um conjunto de dados (arquivo. xsd).

    > [!NOTE]
    >  Se a solução não contém o projeto no qual você deseja separar o código do conjunto de dados, criar o projeto, ou adicionar um projeto existente para a solução.

2.  Clique duas vezes em um arquivo de conjunto de dados tipado (um arquivo. xsd) em **Solution Explorer** para abrir o conjunto de dados de **Dataset Designer**.

3.  Selecione uma área vazia do **Dataset Designer**.

4.  No **propriedades** janela, localize a **projeto DataSet** nó.

5.  No **projeto DataSet** lista, selecione o nome do projeto no qual você deseja gerar o código do conjunto de dados.

     Depois de selecionar o projeto no qual você deseja gerar o código do conjunto de dados, o **arquivo de conjunto de dados** propriedade é preenchida com um nome de arquivo padrão. Você pode alterar esse nome, se necessário. Além disso, se você deseja gerar o código do conjunto de dados em um diretório específico, você pode definir o **pasta do projeto** propriedade para o nome de uma pasta.

    > [!NOTE]
    >  Quando você separar conjuntos de dados e TableAdapters (definindo o **projeto DataSet** propriedade), classes parciais dataset existentes no projeto não ser movidas automaticamente. Classes parciais dataset existentes devem ser movidas manualmente para o projeto de conjunto de dados.

6.  Salve o conjunto de dados.

     O código do conjunto de dados é gerado para o projeto selecionado no **projeto DataSet** propriedade e o **TableAdapter** código é gerado para o projeto atual.

Por padrão, após você separar o dataset e TableAdapter o código, o resultado é um arquivo de classe distintas em cada projeto. O projeto original tem um arquivo chamado DatasetName.Designer.vb (ou DatasetName.Designer.cs) que contém o código do TableAdapter. O projeto que é designado no **projeto Dataset** propriedade tem um arquivo chamado DatasetName.DataSet.Designer.vb (ou DatasetName.DataSet.Designer.cs) que contém o código do conjunto de dados.

> [!NOTE]
>  Para exibir o arquivo de classe gerada, selecione o conjunto de dados ou projeto do TableAdapter. Em seguida, em **Solution Explorer**, selecione **Mostrar todos os arquivos**.

## <a name="see-also"></a>Consulte também

- [Visão geral de aplicativos de dados de N camadas](../data-tools/n-tier-data-applications-overview.md)
- [Passo a passo: criando um aplicativo de dados de N camadas](../data-tools/walkthrough-creating-an-n-tier-data-application.md)
- [Atualização hierárquica](../data-tools/hierarchical-update.md)
- [Acessando dados no Visual Studio](../data-tools/accessing-data-in-visual-studio.md)
- [ADO.NET](/dotnet/framework/data/adonet/index)