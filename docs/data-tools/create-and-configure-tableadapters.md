---
title: Crie e configure os TableAdapters | Microsoft Docs
ms.custom: 
ms.date: 09/01/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- table adapters, creating
- creating TableAdapters
- data [Visual Studio], creating data components
- data [Visual Studio], TableAdapters
- data [Visual Studio], creating table adapters
ms.assetid: 08630d69-0d6c-4e8f-b42d-2922f45f8415
caps.latest.revision: "28"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.workload: data-storage
ms.openlocfilehash: 3c9b501b78a82a94b81b2a29c86fd07a7a0d7f98
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="create-and-configure-tableadapters"></a>Crie e configure os TableAdapters
TableAdapters fornecem comunicação entre seu aplicativo e um banco de dados. Conecte-se ao banco de dados, executadas consultas ou procedimentos armazenados e retorne um novos dados de tabela ou uma existente de preenchimento <xref:System.Data.DataTable> com os dados retornados. TableAdapters também pode enviar dados atualizados do seu aplicativo no banco de dados.  
  
TableAdapters são criados para você quando você executa uma das seguintes ações:  
  
-   Execute o [Assistente de configuração de fonte de dados](../data-tools/media/data-source-configuration-wizard.png) e selecione o **banco de dados** ou **Web Service** tipo de fonte de dados.  
  
-   Arraste os objetos de banco de dados de **Server Explorer** no **Dataset Designer**.  
  
Você também pode criar um novo TableAdapter e configurá-lo com uma fonte de dados arrastando um TableAdapter da caixa de ferramentas para uma área vazia no **Dataset Designer** superfície.  
  
Para obter uma introdução a TableAdapters, consulte [preencher conjuntos de dados usando TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md).  
  
[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
## <a name="use-the-tableadapter-configuration-wizard"></a>Use o Assistente de configuração do TableAdapter  
Execute o **Assistente de configuração TableAdapter** para criar ou editar TableAdapters e seus DataTables associados. Você pode configurar um TableAdapter existente clicando no **Dataset Designer**.  
  
![Assistente de configuração do adaptador de tabela de raddata](../data-tools/media/raddata-table-adapter-configuration-wizard.png "raddata Assistente de configuração do adaptador de tabela")  
  
Se você arrastar um novo TableAdapter da caixa de ferramentas quando o **Dataset Designer** está no foco, o assistente é iniciado e solicita que você especifique quais dados o TableAdapter de origem deve se conectar ao. Na página seguinte, o assistente perguntará que tipo de comandos que ele deve usar para se comunicar com o banco de dados, instruções SQL ou procedimentos armazenados. (Você não verá isso se você estiver configurando um TableAdapter que já está associado uma fonte de dados.)  
  
-   Você tem a opção para criar um novo procedimento armazenado no banco de dados subjacente, se você tiver as permissões corretas para o banco de dados. Se você não tiver essas permissões, isso não será uma opção.  
  
-   Você também pode optar por executar os procedimentos armazenados existentes para o **selecione**, **inserir**, **atualização**, e **excluir** comandos das TableAdapter. O procedimento armazenado que é atribuído para o **atualização** comando, por exemplo, é executado quando o `TableAdapter.Update()` método é chamado.  
  
Mapear parâmetros desde o procedimento armazenado selecionado até as colunas correspondentes na tabela de dados. Por exemplo, se seu procedimento armazenado aceita um parâmetro chamado `@CompanyName` que ele passa para o `CompanyName` conjunto de colunas na tabela, o **coluna de origem** do `@CompanyName` parâmetro `CompanyName`.  
  
> [!NOTE]
>  O procedimento armazenado que é atribuído para o comando SELECT é executado chamando o método do TableAdapter que você nomeia na próxima etapa do assistente. O método padrão é `Fill`, portanto, o código que normalmente é usado para executar o procedimento SELECT é `TableAdapter.Fill(tableName)`. Se você alterar o nome padrão de `Fill`, substitua `Fill` com o nome atribuir e substitua "TableAdapter" com o nome real do TableAdapter (por exemplo, `CustomersTableAdapter`).  
  
-   Selecionando o **criar métodos para enviar atualizações diretamente para o banco de dados** opção é equivalente à configuração de `GenerateDBDirectMethods` propriedade como true. A opção não está disponível quando a instrução SQL original não fornecer informações suficientes ou a consulta não é uma consulta atualizável. Essa situação pode ocorrer, por exemplo, em **INGRESSAR** consultas e consultas que retornam um valor único (escalar).  
  
O **opções avançadas** no assistente permitem que você:  
- Gerar instruções INSERT, UPDATE e DELETE com base na instrução SELECT que é definida no **instruções SQL gerar** página
- Usar simultaneidade otimista
- Especifique se deseja atualizar a tabela de dados após a inserção e instruções de atualização são executadas  
  
## <a name="configure-a-tableadapters-fill-method"></a>Configurar o método Fill do TableAdapter  
Às vezes, você talvez queira alterar o esquema de tabela do TableAdapter. Para fazer isso, você modificar primário do TableAdapter `Fill` método. TableAdapters são criados com um primário `Fill` método que define o esquema da tabela de dados associada. O principal `Fill` método é baseado na consulta ou procedimento armazenado que você inseriu quando configurou originalmente o TableAdapter. É o primeiro método (superior) sob a tabela de dados no Designer de conjunto de dados.  
  
![TableAdapter com várias consultas](../data-tools/media/tableadapter.gif "TableAdapter")  
  
As alterações que fizer no TableAdapter principal do `Fill` método são refletidas no esquema da tabela de dados associada. Por exemplo, remover uma coluna da consulta no principal `Fill` método também remove a coluna da tabela de dados associada. Além disso, remover a coluna do principal `Fill` método remove a coluna de quaisquer consultas adicionais para aquele TableAdapter.  
  
Você pode usar o Assistente de configuração de consulta do TableAdapter para criar e editar consultas adicionais para o TableAdapter. Essas consultas adicionais devem estar de acordo com o esquema da tabela, a menos que elas retornam um valor escalar.  Cada consulta adicional tem um nome que você especificar.  
 
O exemplo a seguir mostra como chamar uma consulta adicional denominada `FillByCity`:  
 
`CustomersTableAdapter.FillByCity(NorthwindDataSet.Customers, "Seattle")`  
  
#### <a name="to-start-the-tableadapter-query-configuration-wizard-with-a-new-query"></a>Para iniciar o Assistente de configuração de consulta do TableAdapter com uma nova consulta  
  
1.  Abra o conjunto de dados de **Dataset Designer**.  
  
2.  Se você estiver criando uma nova consulta, arraste um **consulta** de objeto o **DataSet** guia do **caixa de ferramentas** para um <xref:System.Data.DataTable>, ou selecione **adicionar consulta**no menu de atalho do TableAdapter. Você também pode arrastar uma **consulta** objeto em uma área vazia do **Dataset Designer**, que cria um TableAdapter sem um associado <xref:System.Data.DataTable>. Essas consultas só podem retornar valores únicos de (escalares) ou executar a atualização, inserção, ou excluir comandos no banco de dados.  
  
3.  Sobre o **escolha sua Conexão de dados** tela, selecione ou crie a conexão que a consulta irá utilizar.  
  
    > [!NOTE]
    >  Esta tela é exibida somente quando o designer não pode determinar a conexão apropriada para usar, ou quando nenhuma conexão estiver disponível.  
  
4.  Sobre o **escolher um tipo de comando** tela, selecione os seguintes métodos de busca de dados do banco de dados:  
  
    -   **Usar instruções SQL** permite que você digite uma instrução SQL para selecionar os dados de seu banco de dados.  
  
    -   **Criar novo procedimento armazenado** permite que você tenha o Assistente para cria um novo armazenados procedimento (no banco de dados) com base na instrução SELECT especificada.  
  
    -   **Use os procedimentos armazenados existentes** permite que você execute um procedimento armazenado existente quando executar a consulta.  
  
#### <a name="to-start-the-tableadapter-query-configuration-wizard-on-an-existing-query"></a>Para iniciar o Assistente de configuração de consulta do TableAdapter em uma consulta existente  
  
-   Se você estiver editando uma consulta TableAdapter existente, clique com botão direito a consulta e, em seguida, escolha **configurar** no menu de atalho.  
  
    > [!NOTE]
    >  Clicando duas vezes na consulta principal de um TableAdapter reconfigura o TableAdapter e <xref:System.Data.DataTable> esquema. No entanto, clicando duas vezes uma consulta adicional em um TableAdapter, configura a consulta selecionada. O **Assistente de configuração TableAdapter** reconfigura a definição de TableAdapter, enquanto o Assistente de configuração de consulta do TableAdapter reconfigura a consulta selecionada.  
  
#### <a name="to-add-a-global--query-to-a-tableadapter"></a>Para adicionar uma consulta global a um TableAdapter  
  
-   *Consultas globais* são consultas SQL que retornam um valor único (escalar) ou nenhum valor. Normalmente, funções globais executam operações de banco de dados, como as inserções, atualizações, exclusões. Eles também agregam informações, como uma contagem de clientes em uma tabela ou o total de cobranças para todos os itens em uma ordem específica.  
  
     Adicionar consultas globais arrastando um **consulta** de objeto o **DataSet** guia do **caixa de ferramentas** em uma área vazia do **Dataset Designer**.  
  
-   Fornece uma consulta que realiza a tarefa desejada, por exemplo, `SELECT COUNT(*) AS CustomerCount FROM Customers`.  
  
    > [!NOTE]
    >  Arrastar um **consulta** objeto diretamente para o **Dataset Designer** cria um método que retorna um valor escalar (único). Enquanto a consulta ou procedimento armazenado que você selecionar pode retornar mais de um único valor, o método que é criado pelo assistente só retorna um único valor. Por exemplo, a consulta pode retornar a primeira coluna da primeira linha dos dados retornados.

## <a name="see-also"></a>Consulte também
[Preencher conjuntos de dados usando TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md)