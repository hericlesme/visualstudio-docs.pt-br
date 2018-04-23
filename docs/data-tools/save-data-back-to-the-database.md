---
title: Salvar dados no banco de dados
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- datasets [Visual Basic], validating data
- data validation, datasets
- data [Visual Studio], saving
- row version
- updating datasets, constraints
- datasets [Visual Basic], about datasets
- datasets [Visual Basic], merging
- updates, constraints in datasets
- saving data, about saving data
- datasets [Visual Basic], constraints
- TableAdapters
ms.assetid: afe6cb8a-dc6a-428b-b07b-903ac02c890b
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 4116a06ff57ae6793c7f80abea2464767b33c3bf
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/19/2018
---
# <a name="save-data-back-to-the-database"></a>Salvar dados no banco de dados
O conjunto de dados é uma cópia na memória dos dados. Se você modificar esses dados, é uma boa prática para salvar as alterações no banco de dados. Você fazer isso em uma das três maneiras:

-   Chamando um dos métodos de atualização de um TableAdapter

-   Chamando um dos métodos DBDirect TableAdapter

-   Chamando o método UpdateAll em TableAdapterManager que o Visual Studio gera para você quando o conjunto de dados contém tabelas que estão relacionadas a outras tabelas no conjunto de dados

Ao vincular dados tabelas do conjunto de dados a controles em uma página de formulário do Windows ou o XAML, a arquitetura de associação de dados faz todo o trabalho para você.

Se você estiver familiarizado com TableAdapters, você pode ir diretamente para um destes tópicos:

|Tópico|Descrição|
|-----------|-----------------|
|[Como inserir novos registros em um banco de dados](../data-tools/insert-new-records-into-a-database.md)|Como executar atualizações e inserções usando objetos de comando ou TableAdapters|
|[Atualizar dados usando um TableAdapter](../data-tools/update-data-by-using-a-tableadapter.md)|Como realizar atualizações com TableAdapters|
|[Atualização hierárquica](../data-tools/hierarchical-update.md)|Como realizar atualizações de um dataset com duas ou mais tabelas relacionadas|
|[Lidar com uma exceção de simultaneidade](../data-tools/handle-a-concurrency-exception.md)|Como manipular exceções quando dois usuários tentam alterar os mesmos dados em um banco de dados ao mesmo tempo|
|[Como: salvar dados usando uma transação](../data-tools/save-data-by-using-a-transaction.md)|Como salvar dados em uma transação usando o namespace System Transactions e um objeto de TransactionScope|
|[Passo a passo: salvar dados em uma transação](../data-tools/save-data-in-a-transaction.md)|Instruções passo a passo que cria um aplicativo do Windows Forms para demonstrar o salvamento de dados para um banco de dados dentro de uma transação|
|[Salvar dados em um banco de dados (várias tabelas)](../data-tools/save-data-to-a-database-multiple-tables.md)|Como editar registros e salvar alterações em várias tabelas no banco de dados|
|[Salvar dados de um objeto em um banco de dados](../data-tools/save-data-from-an-object-to-a-database.md)|Como passar dados de um objeto que não está em um conjunto de dados para um banco de dados usando um método TableAdapter DbDirect|
|[Salvando dados com os métodos DBDirect TableAdapter](../data-tools/save-data-with-the-tableadapter-dbdirect-methods.md)|Como usar o TableAdapter para enviar consultas SQL diretamente para o banco de dados|
|[Salvar um conjunto de dados como XML](../data-tools/save-a-dataset-as-xml.md)|Como salvar um conjunto de dados em um documento XML|

## <a name="two-stage-updates"></a>Atualizações de dois estágios
 Atualizar uma fonte de dados é um processo de duas etapas. A primeira etapa é atualizar o conjunto de dados com novos registros, registros alterados ou registros excluídos. Se seu aplicativo nunca envia essas alterações de volta para a fonte de dados, em seguida, você tiver terminado com a atualização.

 Se você enviar as alterações no banco de dados, uma segunda etapa é necessária. Se você não estiver usando controles associados a dados, você precisa chamar manualmente o método Update do mesmo TableAdapter (ou adaptador de dados) que você usou para preencher o conjunto de dados. No entanto, você também pode usar adaptadores diferentes, por exemplo, para mover dados de uma fonte de dados para outra ou para atualizar várias fontes de dados. Se você não estiver usando a associação de dados e é salvar as alterações para tabelas relacionadas, você precisa instanciar manualmente uma variável da classe TableAdapterManager gerado automaticamente e, em seguida, chame o método UdpateAll.

 ![Atualizações de conjunto de dados do Visual Basic](../data-tools/media/vbdatasetupdates.gif "vbDatasetUpdates") processo e a função do DataRowVersion em uma atualização bem-sucedida de atualização de dois estágios

 Um conjunto de dados contém coleções de tabelas, que contém uma coleção de linhas. Se você pretende atualizar uma fonte de dados mais tarde, você deve usar os métodos na propriedade DataTable.DataRowCollection ao adicionar ou remover linhas. Os métodos de realizar o controle de alterações que é necessário para atualizar a fonte de dados. Se você chamar a coleção RemoveAt na propriedade de linhas, a exclusão não ser comunicada de volta para o banco de dados.

## <a name="merge-datasets"></a>Mesclar conjuntos de dados
 Você pode atualizar o conteúdo de um conjunto de dados por *mesclando* -lo com outro conjunto de dados. Isso envolve copiar o conteúdo de um *fonte* conjunto de dados para o dataset chamado (conhecido como o *destino* conjunto de dados). Ao mesclar conjuntos de dados, os novos registros no conjunto de dados de origem são adicionados ao conjunto de dados de destino. Além disso, colunas extras no conjunto de dados de origem são adicionadas ao conjunto de dados de destino. Mesclar conjuntos de dados é útil quando você tem um conjunto de dados local e obter um segundo conjunto de dados de outro aplicativo. Também é útil quando você obtém um segundo conjunto de dados de um componente como um serviço web XML, ou quando você precisa integrar dados de vários conjuntos de dados.

 Ao mesclar conjuntos de dados, você pode passar um argumento booliano (`preserveChanges`) que informa o <xref:System.Data.DataSet.Merge%2A> método se deseja manter modificações existentes no conjunto de dados de destino. Como conjuntos de dados mantém várias versões de registros, é importante ter em mente que mais de uma versão dos registros está sendo mesclada. A tabela a seguir mostra como um registro em dois conjuntos de dados é mesclado:

|DataRowVersion|Conjunto de dados de destino|Conjunto de dados de origem|
|--------------------|--------------------|--------------------|
|Original|James Wilson|James C. Wilson|
|Atual|Jim Wilson|James C. Wilson|

 Chamando o <xref:System.Data.DataSet.Merge%2A> método na tabela anterior com `preserveChanges=false targetDataset.Merge(sourceDataset)` resulta no seguinte:

|DataRowVersion|Conjunto de dados de destino|Conjunto de dados de origem|
|--------------------|--------------------|--------------------|
|Original|James C. Wilson|James C. Wilson|
|Atual|James C. Wilson|James C. Wilson|

 Chamando o <xref:System.Data.DataSet.Merge%2A> método com `preserveChanges = true targetDataset.Merge(sourceDataset, true)` resulta no seguinte:

|DataRowVersion|Conjunto de dados de destino|Conjunto de dados de origem|
|--------------------|--------------------|--------------------|
|Original|James C. Wilson|James C. Wilson|
|Atual|Jim Wilson|James C. Wilson|

> [!CAUTION]
>  No `preserveChanges = true` cenário, se o <xref:System.Data.DataSet.RejectChanges%2A> método for chamado em um registro no conjunto de dados de destino, em seguida, ele reverterá para os dados originais do *fonte* conjunto de dados. Isso significa que se você tentar atualizar a fonte de dados original com o conjunto de dados de destino, ele não consiga localizar a linha original para atualizar. Você pode impedir que uma violação de concorrência preenchendo outro conjunto de dados com os registros atualizados da fonte de dados e, em seguida, executar uma mesclagem para impedir que uma violação de concorrência. (Uma violação de concorrência ocorre quando outro usuário modifica um registro na fonte de dados depois que o conjunto de dados tenha sido preenchido.)

## <a name="update-constraints"></a>Restrições de atualização
 Para fazer alterações em uma linha de dados existente, adicione ou atualize os dados nas colunas individuais. Se o conjunto de dados contiver restrições (como chaves estrangeiras ou restrições não anuláveis), é possível que o registro pode ser temporariamente em um estado de erro que você atualizá-lo. Ou seja, pode ser em um estado de erro depois de concluir a atualização de uma coluna, mas antes de chegar ao próximo.

 Para evitar violações de restrição, você pode suspender temporariamente as restrições de atualização. Isso serve para duas finalidades:

-   Ela impede que um erro que está sendo gerada depois de terminar de atualizar uma coluna, mas ainda não iniciou a atualização de outro.

-   Isso impede determinada atualização eventos sejam invocados (eventos que são geralmente usados para validação).

> [!NOTE]
>  No Windows Forms, a arquitetura de associação de dados é construída dentro do datagrid suspende a restrição de verificação até que o foco é movido para fora de uma linha, e você não precisa chamar explicitamente o <xref:System.Data.DataRow.BeginEdit%2A>, <xref:System.Data.DataRow.EndEdit%2A>, ou <xref:System.Data.DataRow.CancelEdit%2A> métodos.

 As restrições são automaticamente desativado quando o <xref:System.Data.DataSet.Merge%2A> método é chamado em um conjunto de dados. Quando a mesclagem for concluída, se houver quaisquer restrições no conjunto de dados que não pode ser habilitado, um <xref:System.Data.ConstraintException> é gerada. Nessa situação, o <xref:System.Data.DataSet.EnforceConstraints%2A> está definida como `false,` e todas as violações de restrição devem ser resolvidas antes de redefinir o <xref:System.Data.DataSet.EnforceConstraints%2A> propriedade `true`.

 Depois de concluir uma atualização, você pode reabilitar restrição de verificação, que também habilita novamente os eventos de atualização e os aumenta.

 Para obter mais informações sobre eventos de suspensão, consulte [desativar restrições ao preencher um conjunto de dados](../data-tools/turn-off-constraints-while-filling-a-dataset.md).

## <a name="dataset-update-errors"></a>Erros de atualização de conjunto de dados
 Quando você atualiza um registro em um conjunto de dados, há a possibilidade de um erro. Por exemplo, você pode inadvertidamente gravar dados do tipo errado em uma coluna, ou dados que é muito longos ou dados que tem algum outro problema de integridade. Ou você pode ter verificações de validação específicas do aplicativo que podem gerar erros personalizados durante qualquer estágio de um evento de atualização. Para obter mais informações, consulte [validar dados em conjuntos de dados](../data-tools/validate-data-in-datasets.md).

## <a name="maintaining-information-about-changes"></a>Manter informações sobre as alterações
 Informações sobre as alterações em um conjunto de dados são mantidas de duas maneiras: por sinalizar linhas que indicam que foram alteradas (<xref:System.Data.DataRow.RowState%2A>) e mantendo várias cópias de um registro (<xref:System.Data.DataRowVersion>). Usando essas informações, processos podem determinar o que mudou no conjunto de dados e podem enviar atualizações apropriadas para a fonte de dados.

### <a name="rowstate-property"></a>Propriedade RowState
 O <xref:System.Data.DataRow.RowState%2A> propriedade de um <xref:System.Data.DataRow> objeto é um valor que fornece informações sobre o status de uma linha específica de dados.

 A tabela a seguir detalha os possíveis valores a <xref:System.Data.DataRowState> enumeração:

|Valor de DataRowState|Descrição|
|------------------------|-----------------|
|<xref:System.Data.DataRowState.Added>|A linha foi adicionada como um item para um <xref:System.Data.DataRowCollection>. (Uma linha nesse estado não tem uma versão original correspondente desde que ela não existia quando a última <xref:System.Data.DataRow.AcceptChanges%2A> método foi chamado).|
|<xref:System.Data.DataRowState.Deleted>|A linha foi excluída usando o <xref:System.Data.DataRow.Delete%2A> de um <xref:System.Data.DataRow> objeto.|
|<xref:System.Data.DataRowState.Detached>|A linha foi criada, mas não faz parte de nenhum <xref:System.Data.DataRowCollection>. Um <xref:System.Data.DataRow> objeto está nesse estado imediatamente após ele ter sido criado antes ele foi adicionado a uma coleção e depois que ele foi removido de uma coleção.|
|<xref:System.Data.DataRowState.Modified>|Um valor de coluna na linha foi alterado de alguma forma.|
|<xref:System.Data.DataRowState.Unchanged>|A linha não foi alterada desde a última chamada a <xref:System.Data.DataRow.AcceptChanges%2A>.|

### <a name="datarowversion-enumeration"></a>Enumeração DataRowVersion
Conjuntos de dados mantêm várias versões de registros. O <xref:System.Data.DataRowVersion> campos podem ser usados quando a recuperação do valor encontrado em uma <xref:System.Data.DataRow> usando o <xref:System.Data.DataRow.Item%2A> propriedade ou o <xref:System.Data.DataRow.GetChildRows%2A> método do <xref:System.Data.DataRow> objeto.

A tabela a seguir detalha os possíveis valores a <xref:System.Data.DataRowVersion> enumeração:

|Valor DataRowVersion|Descrição|
|--------------------------|-----------------|
|<xref:System.Data.DataRowVersion.Current>|A versão atual de um registro contém todas as modificações que foram executadas no registro desde a última vez <xref:System.Data.DataRow.AcceptChanges%2A> foi chamado. Se a linha tiver sido excluída, não há nenhuma versão atual.|
|<xref:System.Data.DataRowVersion.Default>|O valor padrão de um registro, conforme definido pela fonte de dados ou esquema de conjunto de dados.|
|<xref:System.Data.DataRowVersion.Original>|A versão original de um registro é uma cópia do registro, pois que as últimas alterações foram confirmadas no conjunto de dados. Em termos práticos, isso é normalmente a versão de um registro como lida de uma fonte de dados.|
|<xref:System.Data.DataRowVersion.Proposed>|A versão de um registro que está disponível temporariamente enquanto você estiver no meio de uma atualização — ou seja, entre o momento em que você chamou o <xref:System.Data.DataRow.BeginEdit%2A> método e o <xref:System.Data.DataRow.EndEdit%2A> método. Você normalmente acessa a versão de um registro em um manipulador para um evento, como <xref:System.Data.DataTable.RowChanging>. Chamar o <xref:System.Data.DataRow.CancelEdit%2A> método reverte as alterações e exclui a versão de linha de dados.|

 As versões atuais e originais são úteis quando informações de atualização são transmitidas para uma fonte de dados. Normalmente, quando uma atualização é enviada para a fonte de dados, as novas informações para o banco de dados estão na versão atual de um registro. Informações da versão original são usadas para localizar o registro para atualizar.

 Por exemplo, em um caso onde a chave primária de um registro é alterada, você precisa de uma maneira de localizar o registro correto na fonte de dados para atualizar as alterações. Se nenhuma versão original existisse, o registro provavelmente seria anexado à fonte de dados, resultando não apenas em um registro extra indesejado, mas em um registro que está impreciso e desatualizado. As duas versões também são usadas em controle de simultaneidade. Você pode comparar a versão original em relação a um registro na fonte de dados para determinar se o registro foi alterado desde que foi carregado no conjunto de dados.

 A versão proposta é útil quando você precisa executar a validação antes de realmente confirmar as alterações para o conjunto de dados.

 Mesmo se os registros foram alterados, não há sempre versões originais ou atuais dessa linha. Quando você insere uma nova linha na tabela, não há nenhuma versão original, somente a versão atual. Da mesma forma, se você excluir uma linha chamando a tabela `Delete` método, há uma versão original, mas nenhuma versão atual.

 Você pode testar para ver se uma versão específica de um registro existe consultando uma linha de dados <xref:System.Data.DataRow.HasVersion%2A> método. Você pode acessar qualquer versão de um registro, passando um <xref:System.Data.DataRowVersion> valor de enumeração como um argumento opcional quando você solicitar o valor de uma coluna.

## <a name="getting-changed-records"></a>Obter registros alterados
 É uma prática comum não atualize cada registro em um conjunto de dados. Por exemplo, um usuário pode estar trabalhando com um Windows Forms <xref:System.Windows.Forms.DataGridView> controle que exibe o número de registros. No entanto, o usuário pode atualizar apenas alguns registros, exclua uma e inserir um novo. Conjuntos de dados e tabelas de dados fornecem um método (`GetChanges`) para retornar somente as linhas que foram modificadas.

 Você pode criar subconjuntos de registros alterados usando o `GetChanges` método da tabela de dados (<xref:System.Data.DataTable.GetChanges%2A>) ou do conjunto de dados (<xref:System.Data.DataSet.GetChanges%2A>) em si. Se você chamar o método para a tabela de dados, ele retorna uma cópia da tabela com apenas os registros alterados. Da mesma forma, se você chamar o método no conjunto de dados, você receberá um novo conjunto de dados com apenas os registros modificados nele.

 `GetChanges` por si só retorna todos os registros alterados. Em contraste, passando o desejado <xref:System.Data.DataRowState> como um parâmetro para o `GetChanges` método, você pode especificar o subconjunto de registros alterados que você deseja: recentemente registros, registros marcados para exclusão, registros separados, ou registros modificados.

 Obter um subconjunto de registros alterados é útil quando você deseja enviar os registros para outro componente para processamento. Em vez de enviar todo o conjunto de dados, você pode reduzir a sobrecarga de se comunicar com o outro componente por meio somente os registros que o componente precisa.

## <a name="committing-changes-in-the-dataset"></a>Confirmar as alterações no conjunto de dados
 Como as alterações são feitas no conjunto de dados, o <xref:System.Data.DataRow.RowState%2A> propriedade das linhas alteradas é definida. As versões atuais e originais de registros são estabelecidas, a manutenção e disponibilizadas para você pelo <xref:System.Data.DataRowView.RowVersion%2A> propriedade. Os metadados são armazenados nas propriedades dessas linhas alteradas são necessários para enviar as atualizações corretas para a fonte de dados.

 Se as alterações refletem o estado atual da fonte de dados, você não precisa manter essas informações. Normalmente, há duas vezes quando o conjunto de dados e sua origem são sincronizados:

-   Imediatamente após você ter carregado informações no conjunto de dados, como ao ler dados da origem.

-   Depois de enviar as alterações do conjunto de dados para a fonte de dados (mas não antes, porque você pode perder as informações necessárias para enviar alterações para o banco de dados).

Você pode confirmar as alterações pendentes para o conjunto de dados chamando o <xref:System.Data.DataSet.AcceptChanges%2A> método. Normalmente, <xref:System.Data.DataSet.AcceptChanges%2A> é chamado nos seguintes momentos:

-   Depois que você carregar o conjunto de dados. Se você carregar um conjunto de dados chamando um TableAdapter `Fill` método, então o adaptador confirma automaticamente as alterações para você. No entanto, se você carregar um conjunto de dados, mesclando outro dataset para ele, em seguida, você precisa confirmar as alterações manualmente.

    > [!NOTE]
    >  Você pode impedir que o adaptador confirme automaticamente as alterações ao chamar o `Fill` método definindo o `AcceptChangesDuringFill` propriedades do adaptador de `false`. Se for definido como `false`, em seguida, o <xref:System.Data.DataRow.RowState%2A> de cada linha inserida durante o preenchimento é definido como <xref:System.Data.DataRowState.Added>.

-   Depois que você enviar alterações de conjunto de dados para outro processo, como um serviço Web XML.

    > [!CAUTION]
    >  Confirmar a alteração dessa maneira apaga qualquer informação de alteração. Não as alterações sejam confirmadas até depois que você concluir a execução das operações que exigem o seu aplicativo para saber quais alterações foram feitas no conjunto de dados.

Esse método realiza o seguinte:

-   Grava o <xref:System.Data.DataRowVersion.Current> versão de um registro em seu <xref:System.Data.DataRowVersion.Original> versão e substituirá a versão original.

-   Remove qualquer linha onde o <xref:System.Data.DataRow.RowState%2A> está definida como <xref:System.Data.DataRowState.Deleted>.

-   Conjuntos de <xref:System.Data.DataRow.RowState%2A> propriedade de um registro para <xref:System.Data.DataRowState.Unchanged>.

O <xref:System.Data.DataSet.AcceptChanges%2A> método está disponível em três níveis. Você pode chamá-lo em um <xref:System.Data.DataRow> alterações do objeto para confirmações apenas naquela linha. Você também pode chamá-lo em um <xref:System.Data.DataTable> objeto para confirmar todas as linhas em uma tabela. Por fim, você pode chamá-lo no <xref:System.Data.DataSet> objeto para confirmar todas as alterações pendentes em todos os registros de todas as tabelas do conjunto de dados.

A tabela a seguir descreve quais alterações são confirmadas com base em qual objeto que o método é chamado em.

|Método|Resultado|
|------------|------------|
|<xref:System.Data.DataRow.AcceptChanges%2A?displayProperty=fullName>|As alterações são confirmadas somente sobre a linha específica.|
|<xref:System.Data.DataTable.AcceptChanges%2A?displayProperty=fullName>|As alterações são confirmadas em todas as linhas na tabela específica.|
|<xref:System.Data.DataSet.AcceptChanges%2A?displayProperty=fullName>|As alterações são confirmadas em todas as linhas em todas as tabelas do conjunto de dados.|

> [!NOTE]
>  Se você carregar um conjunto de dados chamando um TableAdapter `Fill` método, você não tem que explicitamente aceitar alterações. Por padrão, o `Fill` chamadas de método de `AcceptChanges` método depois de terminar de preencher a tabela de dados.

 Um método relacionado, <xref:System.Data.DataSet.RejectChanges%2A>, desfaz o efeito das alterações copiando o <xref:System.Data.DataRowVersion.Original> versão volta para o <xref:System.Data.DataRowVersion.Current> versão dos registros. Ele também define o <xref:System.Data.DataRow.RowState%2A> de cada registro de volta para <xref:System.Data.DataRowState.Unchanged>.

## <a name="data-validation"></a>Validação de dados
 Para verificar se os dados em seu aplicativo atendem aos requisitos dos processos que é passado para, geralmente você precisa adicionar validação. Isso pode envolver verificação que uma entrada do usuário em um formulário está correta, validação de dados que são enviados para seu aplicativo por outro aplicativo ou mesmo verificar que informações calculadas no seu componente esteja dentro das restrições de sua fonte de dados e os requisitos do aplicativo.

 Você pode validar dados de várias maneiras:

-   Na camada de negócios, adicionando o código ao seu aplicativo para validar dados. O conjunto de dados é um local que você pode fazer isso. O conjunto de dados fornece algumas das vantagens de validação de back-end, como a capacidade de validar alterações como a alteração de valores de coluna e linha. Para obter mais informações, consulte [validar dados em conjuntos de dados](../data-tools/validate-data-in-datasets.md).

-   Na camada de apresentação, adicionando validação a formulários. Para obter mais informações, consulte [validação de entrada do usuário no Windows Forms](/dotnet/framework/winforms/user-input-validation-in-windows-forms).

-   Nos dados de back-end, enviando dados para a fonte de dados — por exemplo, o banco de dados — e permitindo que ele aceite ou rejeite os dados. Se você estiver trabalhando com um banco de dados que tem recursos sofisticados para validação de dados e fornecer informações de erro, isso pode ser uma abordagem prática porque você pode validar os dados, independentemente de onde vêm. No entanto, essa abordagem não pode acomodar requisitos de validação específicas do aplicativo. Além disso, com a fonte de dados a validar os dados pode resultar em várias viagens à fonte de dados, dependendo de como seu aplicativo facilita a resolução de erros de validação gerado pelo back-end.

    > [!IMPORTANT]
    >  Ao usar comandos de dados com um <xref:System.Data.SqlClient.SqlCommand.CommandType%2A> propriedade é definida como <xref:System.Data.CommandType.Text>, cuidadosamente verifique informações que são enviadas de um cliente antes de passá-la para seu banco de dados. Usuários mal-intencionados podem tentar enviar (inserir) instruções SQL modificadas ou adicionais em um esforço para obter acesso não autorizado ou danificar o banco de dados. Antes de transferir a entrada do usuário para um banco de dados, sempre verifique se que as informações são válidas. É uma prática recomendada sempre usar consultas parametrizadas ou procedimentos armazenados quando possível.

## <a name="transmitting-updates-to-the-data-source"></a>Atualizações de transmissão à fonte de dados
Depois que as alterações foram feitas em um conjunto de dados, você pode transmitir as alterações para uma fonte de dados. Mais comumente, faça isso chamando o `Update` método de um TableAdapter (ou adaptador de dados). O método loops a cada registro em uma tabela de dados, determina que tipo de atualização é necessária (atualizar, inserir ou excluir), se houver, e, em seguida, executa o comando apropriado.

 Como uma ilustração de como as atualizações são feitas, suponha que seu aplicativo usa um conjunto de dados que contém uma única tabela de dados. O aplicativo busca duas linhas do banco de dados. Após a recuperação, a tabela de dados na memória tem esta aparência:

```
(RowState)     CustomerID   Name             Status
(Unchanged)    c200         Robert Lyon      Good
(Unchanged)    c400         Nancy Buchanan    Pending
```

 Seu aplicativo altera o status de Nancy Buchanan como "Preferencial". Como resultado desta alteração, o valor da <xref:System.Data.DataRow.RowState%2A> propriedade para aquela linha muda de <xref:System.Data.DataRowState.Unchanged> para <xref:System.Data.DataRowState.Modified>. O valor de <xref:System.Data.DataRow.RowState%2A> propriedade para a primeira linha permanece <xref:System.Data.DataRowState.Unchanged>. A tabela de dados agora tem esta aparência:

```
(RowState)     CustomerID   Name             Status
(Unchanged)    c200         Robert Lyon      Good
(Modified)     c400         Nancy Buchanan    Preferred
```

 Seu aplicativo agora chama o `Update` método para transmitir o conjunto de dados para o banco de dados. O método verifica se cada linha por sua vez. A primeira linha, o método não transmite instrução SQL no banco de dados que a linha não foi alterado desde que foi originalmente procurada do banco de dados.

 Para a segunda linha, no entanto, o `Update` método automaticamente chama o comando de dados correto e o transmite para o banco de dados. A sintaxe específica da instrução SQL depende do dialeto do SQL que é compatível com o repositório de dados subjacente. Mas as seguintes características gerais da instrução SQL transmitida notáveis:

-   A instrução SQL transmitida é uma instrução UPDATE. O adaptador sabe para usar uma instrução UPDATE porque o valor de <xref:System.Data.DataRow.RowState%2A> é de propriedade <xref:System.Data.DataRowState.Modified>.

-   A instrução SQL transmitida inclui uma cláusula WHERE indicando que o destino da instrução UPDATE é a linha onde `CustomerID = 'c400'`. Esta parte da instrução SELECT distingue a linha de destino de todas as outras porque o `CustomerID` é a chave primária da tabela de destino. As informações para a cláusula WHERE são derivadas da versão original do registro (`DataRowVersion.Original`), no caso dos valores necessários para identificar a linha foram alterados.

-   A instrução SQL transmitida inclui a cláusula SET, para definir os novos valores das colunas modificadas.

    > [!NOTE]
    > Se o TableAdapter `UpdateCommand` propriedade foi definida para o nome de um procedimento armazenado, o adaptador não constrói uma instrução SQL. Em vez disso, ele chama o procedimento armazenado com os parâmetros apropriados passados.

## <a name="passing-parameters"></a>Passando parâmetros
 Você geralmente pode usar parâmetros para passar os valores para os registros que serão atualizadas no banco de dados.  Quando o TableAdapter `Update` método executa uma instrução UPDATE, ele precisa preencher os valores de parâmetro. Ele obtém esses valores do `Parameters` coleta para o comando de dados apropriado — neste caso, o `UpdateCommand` objeto no TableAdapter.

 Se você usou as ferramentas do Visual Studio para gerar um adaptador de dados, o `UpdateCommand` objeto contém uma coleção de parâmetros que corresponde a cada espaço reservado de parâmetro na instrução.

 O <xref:System.Data.SqlClient.SqlParameter.SourceColumn%2A?displayProperty=fullName> propriedade de cada parâmetro aponta para uma coluna na tabela de dados. Por exemplo, o `SourceColumn` propriedade para o `au_id` e `Original_au_id` parâmetros é definida como qualquer coluna na tabela de dados que contém a id do autor. Quando o adaptador `Update` execuções do método, ele lê o autor coluna id do registro que está sendo atualizado e preenche os valores na instrução.

 Em uma instrução UPDATE, você precisa especificar novos valores (aqueles que será gravado no registro), bem como os antigos valores (para que o registro pode ser localizado no banco de dados). Portanto, há dois parâmetros para cada valor: um para a cláusula SET e um diferente para a cláusula WHERE. Ambos os parâmetros leem dados do registro que está sendo atualizado, mas eles obtêm versões diferentes do valor da coluna com base no parâmetro de <xref:System.Data.SqlClient.SqlParameter.SourceVersion> propriedade. O parâmetro para a cláusula SET obtém a versão atual, e o parâmetro para a cláusula WHERE obtém a versão original.

> [!NOTE]
> Você também pode definir valores `Parameters` coleção por conta própria no código, que normalmente você faria em um manipulador de eventos para o adaptador de dados <xref:System.Data.DataTable.RowChanging> eventos.

## <a name="see-also"></a>Consulte também

- [Ferramentas de conjunto de dados no Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)
- [Crie e Configure os TableAdapters](create-and-configure-tableadapters.md)
- [Atualizar dados usando um TableAdapter](../data-tools/update-data-by-using-a-tableadapter.md)
- [Associar controles a dados no Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)
- [Validando dados](validate-data-in-datasets.md)
- [Salvando dados](../data-tools/saving-data.md)