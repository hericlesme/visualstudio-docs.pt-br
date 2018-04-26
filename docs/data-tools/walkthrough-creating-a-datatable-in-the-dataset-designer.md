---
title: 'Instruções passo a passo: criando um DataTable no Designer de Conjunto de Dados'
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- DataTable objects, creating
- Dataset Designer, creating data tables
- tables [Visual Studio], creating
- data [Visual Studio], Dataset Designer
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 163cf07c482f5f3342eb34abdab6c43fefa44735
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="walkthrough-creating-a-datatable-in-the-dataset-designer"></a>Instruções passo a passo: criando um DataTable no Designer de Conjunto de Dados

Este passo a passo explica como criar um <xref:System.Data.DataTable> (sem um TableAdapter) usando o **Dataset Designer**. Para obter informações sobre como criar tabelas de dados que incluem TableAdapters, consulte [criar e configurar TableAdapters](../data-tools/create-and-configure-tableadapters.md).

As tarefas ilustradas neste passo a passo incluem:

-   Criar um novo projeto de aplicativo do Windows Forms

-   Adicionando um novo conjunto de dados para o aplicativo

-   Adicionar uma nova tabela de dados para o conjunto de dados

-   Adicionando colunas à tabela de dados

-   Definindo a chave primária da tabela

## <a name="creating-a-new-windows-forms-application"></a>Criar um novo aplicativo Windows Forms

### <a name="to-create-a-new-windows-forms-application-project"></a>Para criar um novo projeto de aplicativo do Windows Forms

1. No Visual Studio, no **arquivo** menu, selecione **novo**, **projeto...** .

2. Expanda **Visual C#** ou **Visual Basic** no painel esquerdo, selecione **área de trabalho clássica do Windows**.

3. No painel central, selecione a **aplicativo do Windows Forms** tipo de projeto.

4. Nomeie o projeto **DataTableWalkthrough**e, em seguida, escolha **Okey**.

     O **DataTableWalkthrough** projeto é criado e adicionado ao **Gerenciador de soluções**.

## <a name="adding-a-new-dataset-to-the-application"></a>Adicionando um novo conjunto de dados para o aplicativo

### <a name="to-add-a-new-dataset-item-to-the-project"></a>Para adicionar um novo item de conjunto de dados ao projeto

1.  Sobre o **projeto** menu, selecione **Adicionar Novo Item...** .

     A caixa de diálogo Adicionar Novo Item é exibida.

2.  No painel esquerdo, selecione **dados**, em seguida, selecione **conjunto de dados** no painel central.

3.  Escolha **Adicionar**.

     O Visual Studio adiciona um arquivo chamado **dataSet1** ao projeto e abre-na **Dataset Designer**.

## <a name="adding-a-new-datatable-to-the-dataset"></a>Adicionando uma nova DataTable para o conjunto de dados

### <a name="to-add-a-new-data-table-to-the-dataset"></a>Para adicionar uma nova tabela de dados para o conjunto de dados

1.  Arraste um **DataTable** do **conjunto de dados** guia do **caixa de ferramentas** até o **Dataset Designer**.

     Uma tabela denominada **DataTable1** é adicionado ao conjunto de dados.

2.  Clique na barra de título do **DataTable1** e renomeie- `Music`.

## <a name="adding-columns-to-the-datatable"></a>Adicionando colunas à tabela de dados

### <a name="to-add-columns-to-the-datatable"></a>Para adicionar colunas à tabela de dados

1.  Clique com botão direito do **música** tabela. Aponte para **adicionar**e, em seguida, clique em **coluna**.

2.  Nome da coluna `SongID`.

3.  No **propriedades** janela, defina o <xref:System.Data.DataColumn.DataType%2A> propriedade <xref:System.Int16?displayProperty=fullName>.

4.  Repita este processo e adicione as seguintes colunas:

     `SongTitle`: <xref:System.String?displayProperty=fullName>

     `Artist`: <xref:System.String?displayProperty=fullName>

     `Genre`: <xref:System.String?displayProperty=fullName>

## <a name="setting-the-primary-key-for-the-table"></a>Definindo a chave primária da tabela

Todas as tabelas de dados devem ter uma chave primária. Uma chave primária identifica exclusivamente um registro específico em uma tabela de dados.

### <a name="to-set-the-primary-key-of-the-data-table"></a>Para definir a chave primária da tabela de dados

-   Clique com botão direito do **SongID** coluna e clique **definir chave primária**.

     Um ícone de chave aparece ao lado de **SongID** coluna.

## <a name="saving-your-project"></a>Salvando seu projeto

### <a name="to-save-the-datatablewalkthrough-project"></a>Para salvar o projeto DataTableWalkthrough

-   Sobre o **arquivo** menu, clique em **Salvar tudo**.

## <a name="see-also"></a>Consulte também

- [Criar e configurar conjuntos de dados no Visual Studio](../data-tools/create-and-configure-datasets-in-visual-studio.md)
- [Associar controles a dados no Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)
- [Validando dados](../data-tools/validate-data-in-datasets.md)
- [Salvando dados](../data-tools/saving-data.md)