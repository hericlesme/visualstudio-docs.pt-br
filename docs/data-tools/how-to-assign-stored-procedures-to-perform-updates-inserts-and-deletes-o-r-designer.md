---
title: Procedimentos armazenado de uso para executar a atualização, inserção e exclusão em Linq to SQL Object Relational Designer
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: e88224ab-ff61-4a3a-b6b8-6f3694546cac
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 20e21d801172469d0afe28d0b2aebc42a1eec401
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/19/2018
---
# <a name="how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-or-designer"></a>Como: atribuir procedimentos armazenados para executar atualizações, inserções e exclusões (Object Relational Designer)
Os procedimentos armazenados podem ser adicionados ao Designer Relacional de Objetos e executados como métodos típicos do <xref:System.Data.Linq.DataContext>. Eles também podem ser usados para substituir o padrão [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] comportamento de tempo de execução que executa inserções, atualizações e exclusões quando as alterações são salvas de classes de entidade para um banco de dados (por exemplo, ao chamar o <xref:System.Data.Linq.DataContext.SubmitChanges%2A> método).

> [!NOTE]
>  Se seu procedimento armazenado retornar valores que precisem ser reenviados ao cliente (por exemplo, valores calculados no procedimento armazenado), crie parâmetros de saída em seus procedimentos armazenados. Se você não pode usar parâmetros de saída, escreva uma implementação de método parcial em vez de depender das substituições geradas pelo Designer Relacional de Objetos. Os membros mapeados para os valores gerados por banco de dados precisam ser definidos para valores apropriados após a conclusão com êxito de operações INSERT ou UPDATE. Para obter mais informações, consulte [responsabilidades do desenvolvedor em Substituir padrão comportamento](/dotnet/framework/data/adonet/sql/linq/responsibilities-of-the-developer-in-overriding-default-behavior).

> [!NOTE]
>  O [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] manipula automaticamente os valores gerados por banco de dados para colunas de identidade (incremento automático), rowguidcol (GUID gerado por banco de dados) e carimbo de data/hora. Os valores gerados pelo banco de dados em outros tipos de coluna resultarão inesperadamente em um valor nulo. Para retornar os valores gerados pelo banco de dados, você deve definir manualmente <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> para `true` e <xref:System.Data.Linq.Mapping.ColumnAttribute.AutoSync%2A> para um dos seguintes: <xref:System.Data.Linq.Mapping.AutoSync>, <xref:System.Data.Linq.Mapping.AutoSync>, ou <xref:System.Data.Linq.Mapping.AutoSync>.

## <a name="configuring-the-update-behavior-of-an-entity-class"></a>Configurando o comportamento de atualização de uma classe de entidade
 Por padrão, a lógica para atualizar um banco de dados (inserções, atualizações e exclusões) com as alterações feitas aos dados no [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] classes de entidade é fornecido pelo [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] tempo de execução. O tempo de execução cria padrão comandos INSERT, UPDATE e DELETE com base no esquema da tabela (a coluna e informações de chave primária). Quando o comportamento padrão não for desejado, você pode configurar o comportamento da atualização atribuindo os procedimentos armazenados específicos para executar o necessário inserções, atualizações e exclusões necessárias para manipular os dados em sua tabela. Você também pode fazer isso quando o comportamento padrão não é gerado, por exemplo, quando as classes de entidade mapeiam para as exibições. Finalmente, você pode substituir o comportamento de atualização padrão quando o banco de dados exige o acesso à tabela através de procedimentos armazenados.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

#### <a name="to-assign-stored-procedures-to-override-the-default-behavior-of-an-entity-class"></a>Para atribuir procedimentos armazenados para substituir o comportamento padrão de uma classe de entidade

1.  Abra o **LINQ to SQL** arquivo no designer. (Duas vezes no arquivo dbml **Solution Explorer**.)

2.  Em **Server Explorer**/**Pesquisador de objetos de banco de dados**, expanda **procedimentos armazenados** e localize os procedimentos armazenados que você deseja usar para Insert, Update, e/ou comandos de exclusão da classe da entidade.

3.  Arraste o procedimento armazenado para o Designer Relacional de Objetos.

     O procedimento armazenado é adicionado ao painel de métodos como um método <xref:System.Data.Linq.DataContext>. Para obter mais informações, consulte [métodos DataContext (Object Relational Designer)](../data-tools/datacontext-methods-o-r-designer.md).

4.  Selecione a classe de entidade para a qual você deseja usar o procedimento armazenado para executar atualizações.

5.  No **propriedades** janela, selecione o comando para substituir (**inserir**, **atualização**, ou **excluir**).

6.  Clique nas reticências (...) ao lado das palavras **tempo de execução de uso** para abrir o **configurar comportamento** caixa de diálogo.

7.  Selecione **personalizar**.

8.  Selecione o procedimento armazenado desejado a **personalizar** lista.

9. Inspecione a lista de **argumentos de método** e **propriedades da classe** para verificar se o **argumentos de método** mapa apropriada **propriedades da classe**. Mapeie os argumentos de método original (original _*ArgumentName*) para as propriedades originais (*PropertyName* (Original)) para os comandos Update e Delete.

    > [!NOTE]
    >  Por padrão, os argumentos do método são mapeados para as propriedades de classe quando os nomes coincidem. Se os nomes de propriedade forem modificados, não haverá mais correspondência entre a tabela e a classe de entidade. Talvez seja necessário selecionar a propriedade de classe equivalente para mapeamento se o designer não puder determinar o mapeamento correto.

10. Clique em **Okey** ou **aplicar**.

    > [!NOTE]
    >  Você pode continuar a configurar o comportamento para cada combinação de classe/comportamento enquanto você clica em **aplicar** após cada alteração. Se você alterar a classe ou o comportamento antes de clicar em **aplicar**, uma caixa de diálogo de aviso fornecendo uma oportunidade para aplicar as alterações serão exibidas.

Para voltar a usar a lógica de tempo de execução padrão para atualizações, clique no botão de reticências ao lado de Insert, Update, ou excluir no **propriedades** janela e, em seguida, selecione **usar tempo de execução** no  **Configurar o comportamento de** caixa de diálogo.

## <a name="see-also"></a>Consulte também

- [LINQ to SQL tools no Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Métodos DataContext](../data-tools/datacontext-methods-o-r-designer.md)
- [LINQ to SQL (.NET Framework)](/dotnet/framework/data/adonet/sql/linq/index)
- [Inserir, atualizar e excluir operações (.NET Framework)](/dotnet/framework/data/adonet/sql/linq/insert-update-and-delete-operations)