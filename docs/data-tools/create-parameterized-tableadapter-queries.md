---
title: Criar consultas TableAdapter parametrizadas
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data [Visual Studio], TableAdapters
- TableAdapters, parameterized queries
- data [Visual Studio], searching data
- queries [Visual Studio], creating
- TableAdapters, searching data
- queries [Visual Studio], TableAdapters
ms.assetid: 104d1d19-b5a9-4071-b81e-1b3af08e9c7b
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: fe77d3622e9c41d98ff89972e522bb25aae58b9d
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/25/2018
ms.locfileid: "36756003"
---
# <a name="create-parameterized-tableadapter-queries"></a>Criar consultas TableAdapter parametrizadas
Uma consulta parametrizada retorna dados que atendem às condições de uma cláusula WHERE dentro da consulta. Por exemplo, você pode parametrizar uma lista de clientes para exibir apenas clientes em uma determinada cidade, adicionando `WHERE City = @City` ao final da instrução SQL que retorna uma lista de clientes.

 Criar consultas TableAdapter parametrizadas na **Dataset Designer**. Você também pode criá-los em um aplicativo do Windows com o **parametrizar fonte de dados** comando as **dados** menu. O **parametrizar fonte de dados** comando cria os controles no formulário onde você pode inserir os valores de parâmetro e executar a consulta.

> [!NOTE]
> Ao construir uma consulta parametrizada, use a notação de parâmetro que é específica para o banco de dados que você está codificando. Por exemplo, acesso e fontes dados OleDb usam o ponto de interrogação '?' para denotar parâmetros, portanto, a cláusula WHERE seria algo como: `WHERE City = ?`.

> [!NOTE]
> As caixas de diálogo e comandos de menu que você vê podem diferir dos descritos na Ajuda, dependendo de suas configurações ativas ou a edição que você está usando. Para alterar suas configurações, vá para o **ferramentas** menu e selecione **Import and Export Settings**. Para obter mais informações, confira [Personalizar o IDE do Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="create-a-parameterized-tableadapter-query"></a>Criar uma consulta TableAdapter parametrizada

#### <a name="to-create-a-parameterized-query-in-the-dataset-designer"></a>Para criar uma consulta parametrizada no Designer de Conjunto de Dados

-   Crie um novo TableAdapter, adicionando uma cláusula WHERE com os parâmetros desejados à instrução SQL. Para obter mais informações, consulte [criar e configurar TableAdapters](../data-tools/create-and-configure-tableadapters.md).

     -ou-

-   Acrescente uma consulta a um TableAdapter existente, adicionando uma cláusula WHERE com os parâmetros desejados à instrução SQL.

#### <a name="to-create-a-parameterized-query-while-designing-a-data-bound-form"></a>Para criar uma consulta parametrizada durante a criação de um formulário com associação de dados

1.  Selecione um controle no seu formulário que já esteja associado a um conjunto de dados. Para obter mais informações, consulte [controles de ligar o Windows Forms a dados no Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md).

2.  Sobre o **dados** menu, selecione **Add Query**.

3.  Conclua o **construtor de critérios de pesquisa** caixa de diálogo, adicionando uma cláusula WHERE com os parâmetros desejados à instrução SQL.

### <a name="to-add-a-query-to-an-existing-data-bound-form"></a>Adicionar uma consulta a um formulário associado a dados existente

1.  Abra o formulário no **Designer de Formulários do Windows**.

2.  Sobre o **dados** menu, selecione **Add Query** ou **marcas inteligentes de dados**.

    > [!NOTE]
    >  Se **Add Query** não está disponível na **dados** menu, selecione um controle no formulário que exibe os fonte de dados você deseja adicionar a parametrização. Por exemplo, se o formulário exibir dados em um controle <xref:System.Windows.Forms.DataGridView>, selecione-o. Se o formulário exibir dados em controles individuais, selecione qualquer controle associado a dados.

3.  No **tabela de fonte de dados selecione** área, selecione a tabela à qual você deseja adicionar a parametrização.

4.  Digite um nome na **nome da nova consulta** caixa se você estiver criando uma nova consulta.

     -ou-

     Selecione uma consulta na **nome da consulta existente** caixa.

5.  No **texto de consulta** , digite uma consulta que usa parâmetros.

6.  Selecione **OK**.

     Um controle para o parâmetro de entrada e um **Load** botão são adicionados ao formulário em um <xref:System.Windows.Forms.ToolStrip> controle.

#### <a name="querying-for-null-values"></a>Consulta de valores nulos
Parâmetros do TableAdapter podem ser atribuídos valores nulos quando você deseja consultar os registros que não têm nenhum valor atual. Por exemplo, considere a consulta a seguir que tem um `ShippedDate` parâmetro no seu `WHERE` cláusula:

 ```sql
SELECT CustomerID, OrderDate, ShippedDate
FROM Orders
WHERE (ShippedDate = @ShippedDate) OR (ShippedDate IS NULL)
```

 Se esta fosse uma consulta em um TableAdapter, você pode consultar todos os pedidos que não foram enviados com o código a seguir:

 [!code-csharp[VbRaddataTableAdapters#8](../data-tools/codesnippet/CSharp/create-parameterized-tableadapter-queries_1.cs)]
 [!code-vb[VbRaddataTableAdapters#8](../data-tools/codesnippet/VisualBasic/create-parameterized-tableadapter-queries_1.vb)]

 Para habilitar uma consulta aceitar valores nulos:

1.  No **Dataset Designer**, selecione a consulta do TableAdapter que precisa aceitar valores de parâmetro nulo.

2.  No **propriedades** janela, selecione **parâmetros**, em seguida, clique no botão de reticências (**...** ) para abrir o **Editor de coleção de parâmetros**.

3.  Selecione o parâmetro que permite valores nulos e defina as **AllowDbNull** propriedade `true`.

## <a name="see-also"></a>Consulte também

- [Preencher conjuntos de dados usando TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md)