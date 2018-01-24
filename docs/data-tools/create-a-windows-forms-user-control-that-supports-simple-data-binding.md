---
title: "Criar um controle de usuário que suporta vinculação de dados simples | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- custom controls [Visual Studio], Data Sources Window
- Data Sources Window, controls
ms.assetid: b1488366-6dfb-454e-9751-f42fd3f3ddfb
caps.latest.revision: "14"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.workload: data-storage
ms.openlocfilehash: 63df502f17a5c85e51e658854d2ab7dec312fcc5
ms.sourcegitcommit: 49aa031cbebdd9c7ec070c713afb1a97d1ecb701
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2018
---
# <a name="create-a-windows-forms-user-control-that-supports-simple-data-binding"></a>Criar um controle de usuário do Windows Forms que dá suporte à associação de dados simples
Ao exibir dados em formulários em aplicativos do Windows, você pode escolher os controles existentes da **caixa de ferramentas**, ou você pode criar controles personalizados se seu aplicativo requer uma funcionalidade que não está disponível nos controles padrão. Este passo a passo mostra como criar um controle que implementa o <xref:System.ComponentModel.DefaultBindingPropertyAttribute>. Os controles que implementam o <xref:System.ComponentModel.DefaultBindingPropertyAttribute> contêm uma propriedade que pode ser associada a dados. Tais controles são semelhantes a um <xref:System.Windows.Forms.TextBox> ou <xref:System.Windows.Forms.CheckBox>.  
  
 Para obter mais informações sobre criação de controle, consulte [desenvolvendo controles dos Windows Forms em tempo de Design](/dotnet/framework/winforms/controls/developing-windows-forms-controls-at-design-time).  
  
 Ao criar controles para uso em cenários de associação de dados, você deve implementar um dos seguintes atributos de associação de dados:  
  
|Uso do atributo de associação de dados|  
|-----------------------------------|  
|Implemente o <xref:System.ComponentModel.DefaultBindingPropertyAttribute> em controles simples, como um <xref:System.Windows.Forms.TextBox>, que exibe uma única coluna (ou propriedade) de dados. (Esse processo é descrito nesta página de passo a passo.)|  
|Implemente o <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> nos controles, como um <xref:System.Windows.Forms.DataGridView> que exibe listas (ou tabelas) de dados. Para obter mais informações, consulte [criar um controle de usuário do Windows Forms que dá suporte à associação de dados complexos](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md).|  
|Implemente o <xref:System.ComponentModel.LookupBindingPropertiesAttribute> nos controles, como um <xref:System.Windows.Forms.ComboBox>que exibe listas (ou tabelas) de dados, mas também precisa apresentar uma única coluna ou propriedade. Para obter mais informações, consulte [criar um controle de usuário do Windows Forms que dá suporte à associação de dados de pesquisa](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md).|  
  
 Este passo a passo cria um controle simples que exibe dados de uma única coluna em uma tabela. Este exemplo usa a coluna `Phone` da tabela `Customers` do banco de dados de exemplo Northwind. O controle de usuário simples exibirá números de telefone de clientes em um formato de número de telefone padrão, usando um <xref:System.Windows.Forms.MaskedTextBox> e definindo a máscara para um número de telefone.  
  
 Durante este passo a passo, você aprenderá a:  
  
-   Criar um novo **aplicativo do Windows Forms**.  
  
-   Adicionar um novo **controle de usuário** ao seu projeto.  
  
-   Projetar visualmente o controle do usuário.  
  
-   Implementar o atributo `DefaultBindingProperty`.  
  
-   Criar um conjunto de dados com o **configuração da fonte de dados** assistente.  
  
-   Definir o **Phone** coluna o **fontes de dados** janela para usar o novo controle.  
  
-   Criar um formulário para exibir dados no novo controle.  
  
## <a name="prerequisites"></a>Pré-requisitos  
Este passo a passo usa o SQL Server Express LocalDB e o banco de dados de exemplo Northwind.  
  
1.  Se você não tiver o SQL Server Express LocalDB, instale-o do [página de download do SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express), ou por meio de **instalador do Visual Studio**. No instalador do Visual Studio, o SQL Server Express LocalDB pode ser instalado como parte do **armazenamento de dados e processamento** carga de trabalho, ou como um componente individual.  
  
2.  Instale o banco de dados de exemplo Northwind seguindo estas etapas:  

    1. No Visual Studio, abra o **Pesquisador de objetos do SQL Server** janela. (Pesquisador de objetos do SQL Server é instalado como parte do **armazenamento de dados e processamento** carga de trabalho em que o instalador do Visual Studio.) Expanda o **do SQL Server** nó. Clique com botão direito em sua instância de LocalDB e selecione **nova consulta...** .  

       Abre uma janela do editor de consultas.  

    2. Copie o [script Transact-SQL Northwind](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) para sua área de transferência. Este script T-SQL cria o banco de dados Northwind desde o início e a preenche com dados.  

    3. Cole o script T-SQL no editor de consultas e, em seguida, escolha o **Execute** botão.  

       Após um curto período de tempo, a consulta termina de ser executado e o banco de dados Northwind é criado.  
  
## <a name="create-a-windows-forms-application"></a>Criar um aplicativo do Windows Forms  
 A primeira etapa é criar um **aplicativo do Windows Forms**.  
  
#### <a name="to-create-the-new-windows-project"></a>Para criar o novo projeto do Windows  
  
1. No Visual Studio, no **arquivo** menu, selecione **novo**, **projeto...** .  
  
2. Expanda **Visual C#** ou **Visual Basic** no painel esquerdo, selecione **área de trabalho clássica do Windows**.  

3. No painel central, selecione a **aplicativo do Windows Forms** tipo de projeto.  

4. Nomeie o projeto **SimpleControlWalkthrough**e, em seguida, escolha **Okey**. 
  
     O **SimpleControlWalkthrough** projeto é criado e adicionado ao **Gerenciador de soluções**.  
  
## <a name="add-a-user-control-to-the-project"></a>Adicionar um controle de usuário ao projeto  
 Este passo a passo cria um controle de ligação de dados simple de uma **controle de usuário**, para adicionar um **controle de usuário** item para o **SimpleControlWalkthrough** projeto.  
  
#### <a name="to-add-a-user-control-to-the-project"></a>Para adicionar um controle de usuário ao projeto  
  
1.  Do **projeto** menu, escolha **adicionar controle de usuário**.  
  
2.  Tipo `PhoneNumberBox` na área de nome e clique em **adicionar**.  
  
     O **PhoneNumberBox** controle for adicionado ao **Solution Explorer**e é aberto no designer.  
  
## <a name="design-the-phonenumberbox-control"></a>Criar o controle PhoneNumberBox  
 Este passo a passo expande o <xref:System.Windows.Forms.MaskedTextBox> existente para criar o controle `PhoneNumberBox`.  
  
#### <a name="to-design-the-phonenumberbox-control"></a>Para projetar o controle PhoneNumberBox  
  
1.  Arraste um <xref:System.Windows.Forms.MaskedTextBox> do **caixa de ferramentas** na superfície de design do controle de usuário.  
  
2.  Selecione a marca inteligente sobre o <xref:System.Windows.Forms.MaskedTextBox> você apenas arrastando e escolha **definir máscara**.  
  
3.  Selecione **número de telefone** no **máscara de entrada** caixa de diálogo e clique em **Okey** para definir a máscara.  
  
## <a name="add-the-required-data-binding-attribute"></a>Adicione o atributo de associação de dados necessário  
 Para controles simples que suportam associação de dados, implemente o <xref:System.ComponentModel.DefaultBindingPropertyAttribute>.  
  
#### <a name="to-implement-the-defaultbindingproperty-attribute"></a>Para implementar o atributo DefaultBindingProperty  
  
1.  Alterne o controle `PhoneNumberBox` para exibição de código. (No **exibição** menu, escolha **código**.)  
  
2.  Substitua o código no `PhoneNumberBox` pelo seguinte:  
  
     [!code-csharp[VbRaddataDisplaying#3](../data-tools/codesnippet/CSharp/create-a-windows-forms-user-control-that-supports-simple-data-binding_1.cs)]
     [!code-vb[VbRaddataDisplaying#3](../data-tools/codesnippet/VisualBasic/create-a-windows-forms-user-control-that-supports-simple-data-binding_1.vb)]  
  
3.  No menu **Compilação**, escolha **Compilar Solução**.  
  
## <a name="create-a-data-source-from-your-database"></a>Criar uma fonte de dados do banco de dados  
 Esta etapa usa a **configuração da fonte de dados**Assistente para criar uma fonte de dados com base no `Customers` tabela no banco de dados de exemplo Northwind. É preciso ter acesso ao banco de dados de exemplo Northwind para criar a conexão. Para obter informações sobre como configurar o banco de dados de exemplo Northwind, consulte [como: instalar bancos de dados de exemplo](../data-tools/installing-database-systems-tools-and-samples.md).  
  
#### <a name="to-create-the-data-source"></a>Para criar a fonte de dados  
  
1.  Sobre o **dados** menu, clique em **Mostrar fontes de dados**.  
  
2.  No **fontes de dados** janela, selecione **adicionar nova fonte de dados** para iniciar o **configuração da fonte de dados** assistente.  
  
3.  Sobre o **escolher um tipo de fonte de dados** página, selecione **banco de dados**e, em seguida, clique em **próximo**.  
  
4.  Sobre o **escolha sua Conexão de dados** página, faça o seguinte:  
  
    -   Se uma conexão de dados com o banco de dados de exemplo Northwind estiver disponível na lista suspensa, selecione-o.  
  
    -   Selecione **nova Conexão** para iniciar o **Adicionar/Modificar Conexão** caixa de diálogo.  
  
5.  Se seu banco de dados exigir uma senha, selecione a opção para incluir dados confidenciais e, em seguida, clique em **próximo**.  
  
6.  No **salvar a cadeia de caracteres de conexão para o arquivo de configuração de aplicativo** , clique em **próximo**.  
  
7.  Sobre o **escolher seus objetos de banco de dados** página, expanda o **tabelas** nó.  
  
8.  Selecione o `Customers` de tabela e, em seguida, clique em **concluir**.  
  
     O **NorthwindDataSet** é adicionado ao seu projeto e o `Customers` tabela aparece no **fontes de dados** janela.  
  
## <a name="set-the-phone-column-to-use-the-phonenumberbox-control"></a>Definir a coluna de telefone para usar o controle PhoneNumberBox  
 Dentro de **fontes de dados** janela, você pode definir o controle a ser criado antes de arrastar itens para seu formulário.  
  
#### <a name="to-set-the-phone-column-to-bind-to-the-phonenumberbox-control"></a>Para definir a coluna telefone para se associar ao controle PhoneNumberBox  
  
1.  Abra **Form1** no designer.  
  
2.  Expanda o **clientes** nó o **fontes de dados** janela.  
  
3.  Clique na seta suspensa no **clientes** nó e escolha **detalhes** na lista de controle.  
  
4.  Clique na seta suspensa no **Phone** coluna e escolha **personalizar**.  
  
5.  Selecione o **PhoneNumberBox** da lista de **controles associados** no **opções de personalização da interface do usuário de dados** caixa de diálogo.  
  
6.  Clique na seta suspensa no **Phone** coluna e escolha **PhoneNumberBox**.  
  
## <a name="add-controls-to-the-form"></a>Adicionar controles ao formulário  
 Você pode criar os controles associados a dados, arrastando itens a partir de **fontes de dados** janela para o formulário.  
  
#### <a name="to-create-data-bound-controls-on-the-form"></a>Para criar controles de associação de dados no formulário  
  
-   Arraste principal **clientes** nó do **fontes de dados** janela para o formulário e verifique o `PhoneNumberBox` controle é usado para exibir os dados a `Phone` coluna.  
  
     Os controles de associação de dados com rótulos descritivos são exibidos no formulário, juntamente com uma faixa de ferramentas (<xref:System.Windows.Forms.BindingNavigator>) para registros de navegação. Um [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), CustomersTableAdapter, <xref:System.Windows.Forms.BindingSource>, e <xref:System.Windows.Forms.BindingNavigator> aparecem na bandeja do componente.  
  
## <a name="run-the-application"></a>Executar o aplicativo  
  
#### <a name="to-run-the-application"></a>Para executar o aplicativo  
  
-   Pressione F5 para executar o aplicativo.  
  
## <a name="next-steps"></a>Próximas etapas  
 Dependendo dos requisitos do aplicativo, existem várias etapas que você pode realizar após criar um controle com suporte a associação de dados. Algumas etapas seguintes típicas incluem:  
  
-   Colocando os controles personalizados em uma biblioteca de controles para que você possa reutilizá-los em outros aplicativos.  
  
-   Criando controles que suportam cenários de associação de dados mais complexos. Para obter mais informações, consulte [criar um controle de usuário do Windows Forms que dá suporte à associação de dados complexos](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md) e [criar um controle de usuário do Windows Forms que dá suporte à associação de dados de pesquisa](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md).  
  
## <a name="see-also"></a>Consulte também  
 [Associar controles do Windows Forms a dados no Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Definir o controle a ser criado quando arrastado da janela Fontes de Dados](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)
