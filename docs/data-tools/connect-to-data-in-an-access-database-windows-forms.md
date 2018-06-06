---
title: Conectar a dados em um banco de dados do Access (Windows Forms)
ms.date: 09/15/2017
ms.topic: conceptual
helpviewer_keywords:
- databases, connecting to
- databases, Access
- data [Visual Studio], connecting
- connecting to data, from Access databases
- Access databases, connecting
ms.assetid: 4159e815-d430-4ad0-a234-e4125fcbef18
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 233527e92a6d0d20294769d070e8dc81b33753b4
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34746810"
---
# <a name="connect-to-data-in-an-access-database-windows-forms"></a>Conectar a dados em um banco de dados do Access (Windows Forms)
Você pode se conectar a um banco de dados do Access (um arquivo. mdf ou um arquivo. accdb) usando o Visual Studio. Depois de definir a conexão, os dados aparecem no **fontes de dados** janela. Nela, é possível arrastar tabelas ou exibições para os formulários.

## <a name="prerequisites"></a>Pré-requisitos
 Para usar esses procedimentos, você precisa de um projeto de aplicativo do Windows Forms e um banco de dados (arquivo. accdb) ou um banco de dados do Access 2000-2003 (arquivo. mdb). Siga o procedimento correspondente ao tipo de arquivo.

## <a name="creating-the-dataset-for-an-accdb-file"></a>Criar o conjunto de dados para um arquivo. accdb
 Você pode se conectar a bancos de dados criados por meio do Access 2013, Office 365, Access 2010 ou Access 2007, usando o procedimento a seguir.

#### <a name="to-create-the-dataset"></a>Para criar o conjunto de dados

1.  Abra o aplicativo de formulários do Windows na qual você deseja se conectar a dados.

2.  Sobre o **exibição** menu, selecione **outras janelas** > **fontes de dados**.

     ![Exibir outras fontes de dados do Windows](../data-tools/media/viewdatasources.png)

3.  No **fontes de dados** janela, clique em **adicionar nova fonte de dados**.

     O **Assistente de configuração de fonte de dados** é aberto.

4.  Selecione **banco de dados** no **escolher um tipo de fonte de dados** página e, em seguida, selecione **próximo**.

5.  Selecione **Dataset** no **escolha um modelo de banco de dados** página e, em seguida, selecione **próximo**.

6.  Sobre o **escolha sua Conexão de dados** página, selecione **nova Conexão** para configurar uma nova conexão de dados.

     O **Adicionar Conexão** caixa de diálogo é aberta.

7.  Selecione o **alteração** lado a **fonte de dados** caixa de texto.

     O **fonte de dados de alteração** caixa de diálogo é aberta.

8.  Na lista de fontes de dados, escolha  **\<outros\>**. No **provedor de dados** lista suspensa, selecione **provedor de dados do .NET Framework para OLE DB**, em seguida, escolha **Okey**.

9. Volta o **Adicionar Conexão** caixa de diálogo, selecione **Microsoft Office 12.0 Access Database Engine OLE DB Provider** do **provedor OLE DB** suspensa.

     ![OLE DB Provider do Microsoft Office 12.0 Access](../data-tools/media/dataoledbprovideroffice12access.png)

     > [!NOTE]
     >  Se você não vir **Microsoft Office 12.0 Access Database Engine OLE DB Provider** na lista suspensa de provedor do OLE DB, você talvez precise instalar o [2007 Office System Driver: componentes de conectividade de dados](https://www.microsoft.com/download/confirmation.aspx?id=23734).

9. No **nome do servidor ou arquivo** caixa de texto, especifique o caminho e nome do arquivo. accdb você deseja se conectar e, em seguida, selecione arquivo **Okey**. (Se o arquivo de banco de dados tem um nome de usuário e senha, especificá-los antes de selecionar **Okey**.)

10. Selecione **próximo** no **escolha sua Conexão de dados** página.

     Você pode receber uma caixa de diálogo indicando que o arquivo de dados não está no projeto atual. Selecione **Sim** ou **não**.

11. Selecione **próximo** no **salvar a cadeia de caracteres de conexão para o arquivo de configuração de aplicativo** página.

12. Expanda o **tabelas** nó o **escolher seus objetos de banco de dados** página.

13. Selecione quaisquer tabelas ou exibições que você deseja no conjunto de dados e, em seguida, selecione **concluir**.

     O conjunto de dados é adicionado ao seu projeto e as tabelas e modos de exibição aparecem no **fontes de dados** janela.

## <a name="creating-the-dataset-for-an-mdb-file"></a>Criar o conjunto de dados para um arquivo. mdb
 Criar o conjunto de dados executando o **Assistente de configuração de fonte de dados**.

#### <a name="to-create-the-dataset"></a>Para criar o conjunto de dados

1.  Abra o aplicativo de formulários do Windows na qual você deseja se conectar a dados.

2.  Sobre o **exibição** menu, selecione **outras janelas** > **fontes de dados**.

     ![Exibir outras fontes de dados do Windows](../data-tools/media/viewdatasources.png)

3.  No **fontes de dados** janela, clique em **adicionar nova fonte de dados**.

     O **Assistente de configuração de fonte de dados** é aberto.

4.  Selecione **banco de dados** no **escolher um tipo de fonte de dados** página e, em seguida, selecione **próximo**.

5.  Selecione **Dataset** no **escolha um modelo de banco de dados** página e, em seguida, selecione **próximo**.

6.  Sobre o **escolha sua Conexão de dados** página, selecione **nova Conexão** para configurar uma nova conexão de dados.

7.  Se a fonte de dados não for **arquivo de banco de dados do Microsoft Access (OLE DB)**, selecione **alteração** para abrir o **fonte de dados de alteração** caixa de diálogo e selecione **Microsoft Acessar o arquivo de banco de dados**e, em seguida, selecione **Okey**.

8.  No **nome de arquivo de banco de dados**, especifique o caminho e o nome do arquivo. mdb que você deseja se conectar a e, em seguida, selecione **Okey**.

     ![Adicionar o arquivo de banco de dados de acesso de Conexão](../data-tools/media/dataaddconnectionaccessmdb.png)

9. Selecione **próximo** no **escolha sua Conexão de dados** página.

10. Selecione **próximo** no **salvar a cadeia de caracteres de conexão para o arquivo de configuração de aplicativo** página.

11. Expanda o **tabelas** nó o **escolher seus objetos de banco de dados** página.

12. Selecione quaisquer tabelas ou exibições que você deseja no conjunto de dados e, em seguida, selecione **concluir**.

     O conjunto de dados é adicionado ao seu projeto e as tabelas e modos de exibição aparecem no **fontes de dados** janela.

## <a name="security"></a>Segurança
 O armazenamento das informações confidenciais (como uma senha) pode afetar a segurança do aplicativo. O uso da Autenticação do Windows (também conhecida como segurança integrada) é uma maneira mais segura de controlar o acesso a um banco de dados. Para obter mais informações, consulte [Protegendo informações de conexão](/dotnet/framework/data/adonet/protecting-connection-information).

## <a name="next-steps"></a>Próximas etapas
 O conjunto de dados que você acabou de criar agora está disponível na **fontes de dados** janela. Agora você pode executar qualquer uma das seguintes tarefas:

-   Selecione os itens na **fontes de dados** janela e arraste-os para seu formulário (consulte [controla associar Windows Forms a dados no Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)).

-   Abra a fonte de dados no **Dataset Designer** para adicionar ou editar os objetos que compõem o conjunto de dados.

-   Adicionar a lógica de validação de <xref:System.Data.DataTable.ColumnChanging> ou <xref:System.Data.DataTable.RowChanging> eventos das tabelas de dados no conjunto de dados (consulte [validar dados em conjuntos de dados](../data-tools/validate-data-in-datasets.md)).

## <a name="see-also"></a>Consulte também

- [Adicionar conexões](../data-tools/add-new-connections.md)