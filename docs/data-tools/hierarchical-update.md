---
title: Atualização hierárquica
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- saving data, changed data
- data [Visual Basic], hierarchical update
- saving updated data
- datasets [Visual Basic], hierarchical update
- hierarchical update
- saving data, hierarchical update
- modified data saving
- updated data saving
- related tables, saving
ms.assetid: 68bae3f6-ec9b-45ee-a33a-69395029f54c
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 442d6cd60597219c25b41f26ad8c2dc2151248ee
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34747463"
---
# <a name="hierarchical-update"></a>Atualização hierárquica
*Atualização hierárquica* refere-se ao processo de salvar dados atualizados (de um dataset com duas ou mais tabelas relacionadas) para um banco de dados, mantendo as regras de integridade referencial. *A integridade referencial* refere-se às regras de consistência fornecido pelas restrições em um banco de dados que controlam o comportamento de inserindo, atualizando e excluindo registros relacionados. Por exemplo, é a integridade referencial que impõe a criação de um registro de cliente antes de permitir pedidos a ser criado para esse cliente.  Para obter mais informações sobre as relações em conjuntos de dados, consulte [relacionamentos em conjuntos de dados](../data-tools/relationships-in-datasets.md)

 O recurso de atualização hierárquica usa um `TableAdapterManager` para gerenciar o `TableAdapter`s em um conjunto de dados tipado. O `TableAdapterManager` componente é um [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]-gerado a classe, portanto, não é parte do [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]. Quando você arrasta uma tabela da janela fontes de dados em um Windows Form ou página WPF, Visual Studio adiciona uma variável de tipo TableAdapterManager ao formulário ou página e vê-lo no designer na bandeja do componente. Para obter informações detalhadas sobre o `TableAdapterManager` de classe, consulte a seção TableAdapterManager Reference do [TableAdapters](../data-tools/create-and-configure-tableadapters.md).

 Por padrão, um conjunto de dados trata tabelas relacionadas como "apenas relações" o que significa que ele não impõe restrições de chave estrangeira. Você pode modificar essa configuração em tempo de design usando o Designer de conjunto de dados. Selecione a linha de relação entre duas tabelas para ativar o **relação** caixa de diálogo. As alterações feitas aqui determinarão como o TableAdapterManager se comporta quando ele enviar as alterações nas tabelas relacionadas no banco de dados.

## <a name="enable-hierarchical-update-in-a-dataset"></a>Habilitar atualização hierárquica em um conjunto de dados
 Por padrão, a atualização hierárquica está habilitada para todos os novos conjuntos de dados que são adicionados ou criados em um projeto. Ativar ou desativar o atualização hierárquica definindo a **atualização hierárquica** propriedade de um conjunto de dados tipado no conjunto de dados para **True** ou **False**:

 ![Configuração de atualização hierárquica](../data-tools/media/hierarchical-update-setting.png)

## <a name="create-a-new-relation-between-tables"></a>Criar uma nova relação entre tabelas
 Para criar uma nova relação entre duas tabelas, no Designer de conjunto de dados, selecione a barra de título de cada tabela, clique com botão direito e selecione **Adicionar relação**.

 ![Menu de relação de adição de atualização hierárquica](../data-tools/media/hierarchical-update-add-relation-menu.png)

## <a name="understand-foreign-key-constraints-cascading-updates-and-deletes"></a>Entender as restrições foreign key, atualizações em cascata e exclusões
 É importante compreender como restrições de chave estrangeira e comportamento em cascata no banco de dados são criados no código gerado do conjunto de dados.

 Por padrão, as tabelas de dados em um conjunto de dados são geradas com relacionamentos (<xref:System.Data.DataRelation>) que coincidem com os relacionamentos no banco de dados. No entanto, a relação no conjunto de dados não é gerada como uma restrição de chave estrangeira. O <xref:System.Data.DataRelation> é configurado como **relação somente** sem <xref:System.Data.ForeignKeyConstraint.UpdateRule%2A> ou <xref:System.Data.ForeignKeyConstraint.DeleteRule%2A> em vigor.

 Por padrão, atualizações em cascata e exclusões em cascata são desativadas mesmo se a relação do banco de dados é definida com atualizações em cascata e/ou exclusões em cascata ativadas. Por exemplo, criar um novo cliente e um novo pedido e, em seguida, tentar salvar os dados podem causar um conflito com as restrições de chave estrangeira são definidas no banco de dados. Para obter mais informações, consulte [desativar restrições ao preencher um conjunto de dados](turn-off-constraints-while-filling-a-dataset.md).

## <a name="set-the-order-to-perform-updates"></a>Definir a ordem para executar atualizações
 Definindo a ordem para executar atualizações define a ordem da pessoa inserções, atualizações e exclusões que é necessários para salvar todos os dados modificados em todas as tabelas de um conjunto de dados. Quando a atualização hierárquica é habilitada, inserções são executadas em primeiro lugar, em seguida, atualiza e exclui. O `TableAdapterManager` fornece um `UpdateOrder` propriedade que pode ser definida para executar atualizações em primeiro lugar, em seguida, inserções e exclusões.

> [!NOTE]
>  É importante entender que a ordem de atualização é exaustiva. Ou seja, quando as atualizações são executadas, inserções e exclusões são executadas para todas as tabelas no conjunto de dados.

 Para definir o `UpdateOrder` propriedade depois arrastando os itens do [janela fontes de dados](add-new-data-sources.md) para um formulário, selecione o `TableAdapterManager` na bandeja do componente e defina o `UpdateOrder` propriedade no **propriedades** janela.

## <a name="create-a-backup-copy-of-a-dataset-before-performing-a-hierarchical-update"></a>Criar uma cópia de backup de um conjunto de dados antes de executar uma atualização hierárquica
 Quando você salva dados (chamando o `TableAdapterManager.UpdateAll()` método), o `TableAdapterManager` tenta atualizar os dados para cada tabela em uma única transação. Se qualquer parte da atualização para qualquer tabela falhar, a transação inteira é revertida. Na maioria das situações, a reversão retorna seu aplicativo para seu estado original.

 No entanto, às vezes, você talvez queira restaurar o conjunto de dados da cópia de backup. Um exemplo disso pode ocorrer quando você está usando valores de incremento automático. Por exemplo, se um salvamento operação não for bem-sucedida, os valores de incremento automático não são redefinidos no conjunto de dados e o conjunto de dados continua a criar valores de incremento automático. Isso deixa uma lacuna na numeração que pode não ser aceitável em seu aplicativo. Em situações em que isso é um problema, o `TableAdapterManager` fornece um `BackupDataSetBeforeUpdate` propriedade que substitui o conjunto de dados existente por uma cópia de backup se a transação falhar.

> [!NOTE]
>  A cópia de backup está apenas na memória enquanto o `TableAdapterManager.UpdateAll` método está em execução. Portanto, não há nenhum acesso programático a este dataset de backup porque ele substitui o conjunto de dados original ou sai do escopo, assim como o `TableAdapterManager.UpdateAll` método termina de ser executado.

## <a name="modify-the-generated-save-code-to-perform-the-hierarchical-update"></a>Modificar gerado salvar código para executar a atualização hierárquica
 Salve as alterações das tabelas relacionadas de dados no conjunto de dados para o banco de dados chamando o método `TableAdapterManager.UpdateAll` e passando no nome do conjunto de dados que contém as tabelas relacionadas. Por exemplo, execute o método `TableAdapterManager.UpdateAll(NorthwindDataset)` para enviar atualizações de todas as tabelas no NorthwindDataset para o banco de dados back-end.

 Depois de remover os itens do **fontes de dados** janela, código é adicionado automaticamente ao `Form_Load` evento para preencher cada tabela (o `TableAdapter.Fill` métodos). Código também é adicionado ao **salvar** eventos de clique de botão de <xref:System.Windows.Forms.BindingNavigator> para salvar os dados do conjunto de dados no banco de dados (o `TableAdapterManager.UpdateAll` método).

 O código salvar gerado também contém uma linha de código que chama o método `CustomersBindingSource.EndEdit`. Mais especificamente, ele chama o <xref:System.Windows.Forms.BindingSource.EndEdit%2A> método do primeiro <xref:System.Windows.Forms.BindingSource>que é adicionado ao formulário. Em outras palavras, esse código é gerado apenas para a primeira tabela que é arrastada do **fontes de dados** janela para o formulário. A chamada <xref:System.Windows.Forms.BindingSource.EndEdit%2A> confirma as alterações que estão em processo em qualquer controle de associação de dados sendo editado no momento. Portanto, se um controle associado a dados ainda tem foco e clique no **salvar** botão, todas as edições pendentes nesse controle são confirmadas antes de salvar (o `TableAdapterManager.UpdateAll` método).

> [!NOTE]
>  O Designer de conjunto de dados adiciona o `BindingSource.EndEdit` código para a primeira tabela que é arrastada para o formulário. Portanto, é necessário adicionar uma linha de código para chamar o método `BindingSource.EndEdit` para cada tabela relacionada no formulário. Para este passo a passo, isso significa que você precisa adicionar uma chamada ao método `OrdersBindingSource.EndEdit`.

#### <a name="to-update-the-code-to-commit-changes-to-the-related-tables-before-saving"></a>Para atualizar o código para confirmar as alterações às tabelas relacionadas antes de salvar

1.  Clique duas vezes o **salvar** botão o <xref:System.Windows.Forms.BindingNavigator> abrir **Form1** no Editor de códigos.

2.  Adicione uma linha de código para chamar o método `OrdersBindingSource.EndEdit` após a linha que chama o método `CustomersBindingSource.EndEdit`. O código de **salvar** clique do botão evento deve ser semelhante à seguinte:

     [!code-vb[VSProDataOrcasHierarchicalUpdate#1](../data-tools/codesnippet/VisualBasic/hierarchical-update_1.vb)]
     [!code-csharp[VSProDataOrcasHierarchicalUpdate#1](../data-tools/codesnippet/CSharp/hierarchical-update_1.cs)]

Além de confirmar as alterações em uma tabela filho relacionada antes de salvar dados em um banco de dados, você também pode confirmar registros pais recém-criados antes de adicionar novos registros filhos a um conjunto de dados. Em outras palavras, pode ser necessário adicionar o novo registro pai (Cliente) para o conjunto de dados antes que as restrições de chave estrangeira permitam que novos registros filhos (Pedidos) sejam adicionados ao conjunto de dados. Para realizar isso, você pode usar o evento filho `BindingSource.AddingNew`.

> [!NOTE]
> Se você precisa confirmar novos registros pai depende do tipo de controle que é usado para associar à sua fonte de dados. Neste passo a passo, você pode usar os controles individuais para associar à tabela pai. Isso requer o código adicional para confirmar o novo registro pai. Se os registros pai em vez disso, foram exibidos em um controle complexo de ligação como o <xref:System.Windows.Forms.DataGridView>adicionais nesse <xref:System.Windows.Forms.BindingSource.EndEdit%2A> chamada para o registro pai não seria necessário. Isso porque a funcionalidade subjacente de associação de dados do controle processa a confirmação dos novos registros.

#### <a name="to-add-code-to-commit-parent-records-in-the-dataset-before-adding-new-child-records"></a>Para adicionar código para confirmar registros pais no conjunto de dados antes de adicionar novos registros filhos

1.  Crie um manipulador de eventos para o evento `OrdersBindingSource.AddingNew`.

    -   Abra **Form1** no modo de design, selecione **OrdersBindingSource** na bandeja do componente, selecione **eventos** no **propriedades** janela, e em seguida, clique duas vezes o **AddingNew** eventos.

2.  Adicionar uma linha de código para o manipulador de eventos que chama o `CustomersBindingSource.EndEdit` método. O código no manipulador de eventos `OrdersBindingSource_AddingNew` deve ser semelhante ao seguinte:

     [!code-vb[VSProDataOrcasHierarchicalUpdate#2](../data-tools/codesnippet/VisualBasic/hierarchical-update_2.vb)]
     [!code-csharp[VSProDataOrcasHierarchicalUpdate#2](../data-tools/codesnippet/CSharp/hierarchical-update_2.cs)]

## <a name="tableadaptermanager-reference"></a>Referência de TableAdapterManager
 Por padrão, um `TableAdapterManager` classe é gerada quando você cria um conjunto de dados que contém as tabelas relacionadas. Para impedir que a classe que está sendo gerado, altere o valor da `Hierarchical Update` propriedade do conjunto de dados como false. Quando você arrastar uma tabela que tenha uma relação na superfície de design de um formulário do Windows ou a página do WPF, o Visual Studio declara uma variável de membro da classe. Se você não usa associação de dados, você deve manualmente declarar a variável.

 O `TableAdapterManager` a classe não é parte do [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]. Portanto, você não pode procurar por ele na documentação. Ele é criado em tempo de design como parte do processo de criação de conjunto de dados.

 A seguir estão os métodos usados frequentemente e propriedades do `TableAdapterManager` classe:

|Membro|Descrição|
|------------|-----------------|
|Método `UpdateAll`|Salva todos os dados de todas as tabelas de dados.|
|Propriedade `BackUpDataSetBeforeUpdate`|Determina se é necessário criar uma cópia de backup do conjunto de dados antes de executar o `TableAdapterManager.UpdateAll` método. Valor booliano.|
|*tableName* `TableAdapter` propriedade|Representa um `TableAdapter`. Gerado `TableAdapterManager` contém uma propriedade para cada `TableAdapter` ele gerencia. Por exemplo, um conjunto de dados com uma tabela clientes e pedidos é gerado com um `TableAdapterManager` que contém `CustomersTableAdapter` e `OrdersTableAdapter` propriedades.|
|Propriedade `UpdateOrder`|Controla a ordem dos comandos delete, insert individual e atualização. Defina isso para um dos valores a `TableAdapterManager.UpdateOrderOption` enumeração.<br /><br /> Por padrão, o `UpdateOrder` é definido como **InsertUpdateDelete**. Isso significa que insere, em seguida, atualiza e exclui, em seguida, são executadas para todas as tabelas no conjunto de dados.|

## <a name="see-also"></a>Consulte também

- [Salvar dados de volta no banco de dados](../data-tools/save-data-back-to-the-database.md)