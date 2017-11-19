---
title: Criar e configurar conjuntos de dados no Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- typed datasets, creating
- datasets [Visual Basic], creating
ms.assetid: 58f33b43-24e1-43b1-b08b-b74329960bd6
caps.latest.revision: "36"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: 5dd27f35bdfd0ee2f576c1a4ac2fe3fde5a357e6
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/09/2017
---
# <a name="create-and-configure-datasets-in-visual-studio"></a>Criar e configurar conjuntos de dados no Visual Studio
Um *dataset* é um conjunto de objetos que armazenam dados de um banco de dados na memória e dar suporte a controle de alterações para permitir criar, ler, atualizar e excluir operações (CRUD) nos dados sem a necessidade de estar sempre conectados ao banco de dados. Conjuntos de dados foram projetados para simples *formulários sobre dados* aplicativos de negócios. Para novos aplicativos, considere o uso do Entity Framework para armazenar e modelo de dados na memória. Para trabalhar com conjuntos de dados, você deve ter um conhecimento básico dos conceitos de banco de dados.  
  
 Você cria um tipo <xref:System.Data.DataSet> classe no Visual Studio em tempo de design usando a **Assistente de configuração de fonte de dados**. Para obter informações sobre como criar conjuntos de dados programaticamente, consulte [criando um conjunto de dados](/dotnet/framework/data/adonet/dataset-datatable-dataview/creating-a-dataset).  
  
## <a name="create-a-new-dataset-by-using-the-data-source-configuration-wizard"></a>Criar um novo conjunto de dados usando o Assistente de configuração de fonte de dados  
  
1.  Sobre o **projeto** menu, clique em **adicionar nova fonte de dados** para iniciar o **Assistente de configuração de fonte de dados**.  
  
2.  Escolha o tipo de fonte de dados que você irá se conectar.  
  
     ![Assistente de configuração da fonte de dados](../data-tools/media/data-source-configuration-wizard.png "Assistente de configuração da fonte de dados")  
  
3.  Para bancos de dados, escolha o banco de dados ou bancos de dados que serão a fonte de dados para o conjunto de dados.  
  
     ![Fonte de dados escolha uma conexão](../data-tools/media/data-source-choose-a-connection.png "fonte de dados escolha uma conexão")  
  
4.  Escolha as tabelas (ou colunas individuais), procedimentos armazenados, funções e exibições do banco de dados que você deseja ser representado no conjunto de dados.  
  
     ![Escolha os objetos de banco de dados](../data-tools/media/raddata-chose-objects.png "raddata escolher objetos")  
  
5.  Clique em **Finalizar**.  
  
6.  O conjunto de dados aparece como um nó em **Solution Explorer**:  
  
     ![Conjunto de dados no Gerenciador de soluções](../data-tools/media/dataset-in-solution-explorer.png "conjunto de dados no Gerenciador de soluções")  
  
     Clicar nesse nó e o conjunto de dados aparece no **DataSet Designer**. Observe que cada tabela no conjunto de dados tem um objeto TableAdapter associado, que é representado na parte inferior. O adaptador de tabela é usado para preencher o conjunto de dados e, opcionalmente, para enviar comandos ao banco de dados.  
  
     ![Designer de conjunto de dados](../data-tools/media/dataset-designer.png "Designer de conjunto de dados")  
  
7.  As linhas de relação que conectam as tabelas representam relações de tabela, conforme definido no banco de dados. Por padrão, as restrições de chave estrangeira em um banco de dados são representadas como uma relação somente, com a atualização e excluir regras definidas como none. Normalmente, que é o que você deseja. No entanto, você pode clicar em linhas para abrir o **relação** caixa de diálogo, onde você pode alterar o comportamento de atualizações hierárquicas. Para obter mais informações, consulte [relacionamentos em conjuntos de dados](../data-tools/relationships-in-datasets.md) e [atualização hierárquica](../data-tools/hierarchical-update.md).  
  
     ![Caixa de diálogo de relação de conjunto de dados](../data-tools/media/raddata-relation-dialog.png "caixa de diálogo de relação raddata")  
  
8.  Clique em uma tabela, o adaptador de tabela ou o nome da coluna em uma tabela para ver suas propriedades no **propriedades** janela. Você pode modificar alguns dos valores aqui. Lembre-se de que você está modificando o conjunto de dados, não o banco de dados de origem.  
  
     ![Propriedades de coluna do conjunto de dados](../data-tools/media/dataset-column-properties.png "propriedades de coluna do conjunto de dados")  
  
9. Você pode adicionar novas tabelas ou adaptadores de tabelas para o conjunto de dados, ou adicionar novas consultas para adaptadores de tabela existente ou especificar novas relações entre tabelas, arrastando os itens do **caixa de ferramentas** guia. Este guia é exibida quando o **DataSet Designer** esteja em foco.  
  
     ![Caixa de ferramentas do conjunto de dados](../data-tools/media/raddata-dataset-toolbox.png "raddata caixa de ferramentas do conjunto de dados")  
  
10. Em seguida, você provavelmente desejará especificar como preencher o conjunto de dados com dados. Para fazer isso, você deve usar o **TableAdapter Assistente de configuração**. Para obter mais informações, consulte [preencher conjuntos de dados usando TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md) .  
  
## <a name="add-a-database-table-or-other-object-to-an-existing-dataset"></a>Adicionar uma tabela de banco de dados ou outro objeto para um conjunto de dados existente  
 Este procedimento mostra como adicionar uma tabela de banco de dados mesmo que você usou para criar primeiro o conjunto de dados.  
  
1.  Clique no nó do conjunto de dados no **Solution Explorer** para trazer o designer de conjunto de dados para o foco.  
  
2.  Clique o **fontes de dados** guia na margem esquerda do Visual Studio, ou insira `Data Sources` na **início rápido**.  
  
3.  Clique com botão direito no nó do conjunto de dados e selecione **configurar fonte de dados com o assistente** .  
  
     ![Menu de contexto de fonte de dados](../data-tools/media/data-source-context-menu.png "menu de contexto de fonte de dados")  
  
4.  Use o Assistente para especificar quais tabelas adicionais, ou procedimentos armazenados ou outro objeto de banco de dados, para adicionar ao conjunto de dados.  
  
## <a name="add-a-stand-alone-data-table-to-a-dataset"></a>Adicionar uma tabela de dados independente a um conjunto de dados  
  
1.  Abra o conjunto de dados de **Dataset Designer**.  
  
2.  Arraste um <xref:System.Data.DataTable> classe o **conjunto de dados** guia do **caixa de ferramentas** até o **Dataset Designer**.  
  
3.  Adicione colunas para definir a tabela de dados. Com o botão direito na tabela e escolha **Adicionar > coluna**. Use o **propriedades** janela para definir o tipo de dados da coluna e uma chave, se necessário.  
  
4.  Tabelas autônomas precisam implementar `Fill` lógica em tabelas autônomas para que você pode preenchê-los com dados. Para obter informações sobre preenchimento de tabelas de dados autônoma, consulte [preenchendo um DataSet de um DataAdapter](/dotnet/framework/data/adonet/populating-a-dataset-from-a-dataadapter).

## <a name="see-also"></a>Consulte também
[Ferramentas de conjunto de dados no Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)