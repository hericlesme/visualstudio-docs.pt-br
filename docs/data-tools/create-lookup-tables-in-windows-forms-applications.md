---
title: Criar tabelas de pesquisa em aplicativos do Windows Forms
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- lookup tables
- lookup tables, creating
ms.assetid: 0edd5385-c381-4b17-9096-74e2778db9d5
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 315bed179a21ec99a256fcc8cb16f6fc1164f238
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="create-lookup-tables-in-windows-forms-applications"></a>Criar tabelas de pesquisa em aplicativos do Windows Forms
O termo *tabela de pesquisa* descreve controles que são associados a dados relacionados de duas tabelas. Esses controles de pesquisa exibem dados da primeira tabela com base em um valor selecionado na segunda tabela.

 Você pode criar tabelas de pesquisa arrastando o nó principal de uma tabela pai (da [janela fontes de dados](add-new-data-sources.md)) para um controle no formulário que já está associado à coluna na tabela filho relacionados.

 Por exemplo, considere uma tabela de `Orders` em um banco de dados de venda. Cada registro de `Orders` tabela inclui um `CustomerID`, indicando qual cliente fez o pedido. O `CustomerID` é uma chave estrangeira apontando para um registro de cliente no `Customers` tabela. Nesse cenário, você expande o `Orders` tabela o **fontes de dados** janela e definir o nó principal **detalhes**. Em seguida, defina o `CustomerID` coluna para usar um <xref:System.Windows.Forms.ComboBox> (ou qualquer outro controle que dá suporte à vinculação de pesquisa) e arraste o `Orders` até o formulário. Por fim, arraste o `Customers` nó para o controle que está associado à coluna relacionada — nesse caso, o <xref:System.Windows.Forms.ComboBox> associado para o `CustomerID` coluna.

## <a name="to-databind-a-lookup-control"></a>Vincular dados um controle de pesquisa

1.  Abra o **fontes de dados** janela.

    > [!NOTE]
    >  Tabelas de pesquisa requerem que duas tabelas relacionadas ou objetos estão disponíveis no **fontes de dados** janela. Para obter mais informações, consulte [relacionamentos em conjuntos de dados](relationships-in-datasets.md).

2.  Expanda os nós a **fontes de dados** janela até que você pode ver a tabela pai e todas as suas colunas e a tabela filho relacionada e todas as suas colunas.

    > [!NOTE]
    >  O nó da tabela filho é o nó que aparece como um nó filho expansível na tabela pai.

3.  Altere o tipo subjacente da tabela filho para **detalhes** selecionando **detalhes** na lista de controle no nó da tabela filho. Para obter mais informações, consulte [definir o controle a ser criado quando arrastado da janela fontes de dados](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

4.  Localize o nó que relaciona as duas tabelas (o `CustomerID` nó no exemplo anterior). Altere seu tipo subjacente para um <xref:System.Windows.Forms.ComboBox> selecionando **ComboBox** na lista de controle.

5.  Arraste o nó da tabela filho principal do **fontes de dados** window para seu formulário.

     Controles de associação de dados (com rótulos descritivos) e uma ferramenta da faixa (<xref:System.Windows.Forms.BindingNavigator>) aparecem no formulário. Um [DataSet](../data-tools/dataset-tools-in-visual-studio.md), [TableAdapter](../data-tools/create-and-configure-tableadapters.md), <xref:System.Windows.Forms.BindingSource>, e <xref:System.Windows.Forms.BindingNavigator> aparecem na bandeja do componente.

6.  Agora, arraste o nó da tabela pai principal do **fontes de dados** janela diretamente para o controle de pesquisa (o <xref:System.Windows.Forms.ComboBox>).

     As associações de pesquisa agora estão estabelecidas. Consulte a tabela abaixo para as propriedades específicas que foram definidas no controle.

    |Propriedade|Explicação da configuração|
    |--------------|----------------------------|
    |**Fonte de dados**|O Visual Studio define esta propriedade para o <xref:System.Windows.Forms.BindingSource> criado para a tabela que você arrasta para o controle (em oposição ao <xref:System.Windows.Forms.BindingSource> criado quando o controle foi criado).<br /><br /> Se você precisar fazer um ajuste, defina isso o <xref:System.Windows.Forms.BindingSource> da tabela com a coluna que você deseja exibir.|
    |**DisplayMember**|O Visual Studio define essa propriedade para a primeira coluna após a chave primária que tem um tipo de dado de cadeia da tabela que você arrasta para o controle.<br /><br /> Se você precisar fazer um ajuste, em seguida, defina isso para o nome da coluna que deseja exibir.|
    |**ValueMember**|O Visual Studio define essa propriedade para a primeira coluna participante da chave primária, ou a primeira coluna na tabela, se nenhuma chave for definida.<br /><br /> Se você precisar fazer um ajuste, em seguida, defina a chave primária na tabela com a coluna que você deseja exibir.|
    |**SelectedValue**|O Visual Studio define essa propriedade para a coluna original descartada do **fontes de dados** janela.<br /><br /> Se você precisar fazer um ajuste, defina isso para a coluna de chave estrangeira na tabela relacionada.|

## <a name="see-also"></a>Consulte também

- [Associando controles do Windows Forms a dados no Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)