---
title: 'Passo a passo: Recuperando dados de uma pasta de trabalho em um servidor em cache | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- workbooks [Office development in Visual Studio], retrieving data
- datasets [Office development in Visual Studio], accessing on server
- server-side data access [Office development in Visual Studio]
- data [Office development in Visual Studio], accessing on server
- documents [Office development in Visual Studio], server-side data access
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: e259142ce37115196c7bc0dd0390d162020c476d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="walkthrough-retrieving-cached-data-from-a-workbook-on-a-server"></a>Informações passo a passo: recuperando dados armazenados em cache a partir de uma pasta de trabalho em um servidor
  Este passo a passo demonstra como recuperar dados de um conjunto de dados que é armazenado em cache em uma pasta de trabalho do Microsoft Office Excel sem iniciar o Excel usando o <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> classe.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 Esta explicação passo a passo ilustra as seguintes tarefas:  
  
-   Definindo um conjunto de dados que contém dados do banco de dados AdventureWorksLT.  
  
-   Criar instâncias do conjunto de dados em um projeto de pasta de trabalho do Excel e um projeto de aplicativo de console.  
  
-   Criando um <xref:Microsoft.Office.Tools.Excel.ListObject> que é associada ao conjunto de dados na pasta de trabalho e preenchendo a <xref:Microsoft.Office.Tools.Excel.ListObject> com dados quando a pasta de trabalho é aberta.  
  
-   Adicionando o conjunto de dados na pasta de trabalho para o cache de dados.  
  
-   Leitura de dados do conjunto de dados armazenados em cache para o conjunto de dados no aplicativo de console, sem iniciar o Excel.  
  
 Embora este passo a passo pressupõe que você está executando o código no computador de desenvolvimento, o código demonstrado por este passo a passo pode ser usado em um servidor que não tenha o Excel instalado.  
  
> [!NOTE]  
>  Seu computador pode mostrar diferentes nomes ou locais para alguns dos elementos de interface do usuário do Visual Studio nas instruções a seguir. A edição do Visual Studio que você possui e as configurações que você usa determinam esses elementos. Para obter mais informações, confira [Personalizar o IDE do Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="prerequisites"></a>Pré-requisitos  
 Você precisa dos seguintes componentes para concluir esta instrução passo a passo:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] ou [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].  
  
-   Acesso ao executar uma instância do Microsoft SQL Server ou Microsoft SQL Server Express que tem o banco de dados de exemplo AdventureWorksLT anexado a ele. Você pode baixar o banco de dados AdventureWorksLT o [site da CodePlex](http://go.microsoft.com/fwlink/?linkid=87843). Para obter mais informações sobre como anexar um banco de dados, consulte os tópicos a seguir:  
  
    -   Para anexar um banco de dados usando o SQL Server Management Studio ou o SQL Server Management Studio Express, consulte [como: anexar um banco de dados (SQL Server Management Studio)](http://msdn.microsoft.com/en-us/b4efb0ae-cfe6-4d81-a4b4-6e4916885caa).  
  
    -   Para anexar um banco de dados usando a linha de comando, consulte [como: anexar um arquivo de banco de dados SQL Server Express](http://msdn.microsoft.com/en-us/0f8e42b5-7a8c-4c30-8c98-7d2bdc8dcc68).  
  
## <a name="creating-a-class-library-project-that-defines-a-dataset"></a>Criando um projeto de biblioteca de classe que define um conjunto de dados  
 Para usar o mesmo conjunto de dados em um projeto de pasta de trabalho do Excel e um aplicativo de console, você deve definir o conjunto de dados em um assembly separado que é referenciado por ambos esses projetos. Para este passo a passo, defina o conjunto de dados em um projeto de biblioteca de classe.  
  
#### <a name="to-create-the-class-library-project"></a>Para criar o projeto de biblioteca de classe  
  
1.  Inicie o [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  No menu **Arquivo**, aponte para **Novo** e clique em **Projeto**.  
  
3.  No painel de modelos, expanda **Visual C#** ou **Visual Basic**e, em seguida, clique em **Windows**.  
  
4.  Na lista de modelos de projeto, selecione **biblioteca de classes**.  
  
5.  No **nome** , digite **AdventureWorksDataSet**.  
  
6.  Clique em **procurar**, navegue até seu %UserProfile%\My documentos (para Windows XP e anterior) ou a pasta %UserProfile%\Documents (para Windows Vista) e, em seguida, clique em **Selecionar pasta**.  
  
7.  No **novo projeto** caixa de diálogo caixa, certifique-se de que o **criar diretório para solução** caixa de seleção não estiver selecionada.  
  
8.  Clique em **OK**.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Adiciona o **AdventureWorksDataSet** projeto **Gerenciador de soluções** e abre o **Class1.cs** ou **Class1** arquivo de código.  
  
9. Em **Solution Explorer**, clique com botão direito **Class1.cs** ou **Class1**e, em seguida, clique em **excluir**. Esse arquivo não é necessário para este passo a passo.  
  
## <a name="defining-a-dataset-in-the-class-library-project"></a>Definindo um conjunto de dados no projeto de biblioteca de classe  
 Defina um conjunto de dados tipado que contém dados do banco de dados AdventureWorksLT para o SQL Server 2005. Posteriormente neste passo a passo, você irá referenciar este conjunto de dados de um projeto de pasta de trabalho do Excel e um projeto de aplicativo de console.  
  
 O conjunto de dados é um *digitado dataset* que representa os dados na tabela de produto do banco de dados AdventureWorksLT. Para obter mais informações sobre conjuntos de dados tipados, consulte [ferramentas do conjunto de dados no Visual Studio](/visualstudio/data-tools/dataset-tools-in-visual-studio).  
  
#### <a name="to-define-a-typed-dataset-in-the-class-library-project"></a>Para definir um conjunto de dados tipado no projeto de biblioteca de classe  
  
1.  Em **Solution Explorer**, clique no **AdventureWorksDataSet** projeto.  
  
2.  Se o **fontes de dados** janela não estiver visível, exibir, na barra de menus, escolhendo **exibição**, **outras janelas**, **fontes de dados**.  
  
3.  Escolha **adicionar nova fonte de dados** para iniciar o **Assistente de configuração de fonte de dados**.  
  
4.  Clique em **banco de dados**e, em seguida, clique em **próximo**.  
  
5.  Se você tiver uma conexão existente no banco de dados AdventureWorksLT, escolha essa conexão e clique em **próximo**.  
  
     Caso contrário, clique em **nova Conexão**e usar o **Adicionar Conexão** caixa de diálogo para criar a nova conexão. Para obter mais informações, consulte [adicionar novas conexões](../data-tools/add-new-connections.md).  
  
6.  No **salvar a cadeia de Conexão no arquivo de configuração do aplicativo** , clique em **próximo**.  
  
7.  No **escolher seus objetos de banco de dados** página, expanda **tabelas** e selecione **produto (SalesLT)**.  
  
8.  Clique em **Finalizar**.  
  
     O arquivo AdventureWorksLTDataSet.xsd é adicionado para o **AdventureWorksDataSet** projeto. Esse arquivo define os seguintes itens:  
  
    -   Um conjunto de dados tipado chamado `AdventureWorksLTDataSet`. Este conjunto de dados representa o conteúdo da tabela Produtos no banco de dados AdventureWorksLT.  
  
    -   Um TableAdapter chamado `ProductTableAdapter`. Este TableAdapter pode ser usado para ler e gravar dados no `AdventureWorksLTDataSet`. Para obter mais informações, consulte [visão geral de TableAdapter](../data-tools/fill-datasets-by-using-tableadapters.md#tableadapter-overview).  
  
     Você usará esses objetos posteriormente neste passo a passo.  
  
9. Em **Solution Explorer**, clique com botão direito **AdventureWorksDataSet** e clique em **criar**.  
  
     Verifique se o projeto é compilado sem erros.  
  
## <a name="creating-an-excel-workbook-project"></a>Criando um projeto de pasta de trabalho do Excel  
 Crie um projeto de pasta de trabalho do Excel para a interface para os dados. Posteriormente neste passo a passo, você criará um <xref:Microsoft.Office.Tools.Excel.ListObject> que exibe os dados, e você irá adicionar uma instância do conjunto de dados para o cache de dados na pasta de trabalho.  
  
#### <a name="to-create-the-excel-workbook-project"></a>Para criar o projeto de pasta de trabalho do Excel  
  
1.  Em **Solution Explorer**, com o botão direito do **AdventureWorksDataSet** solução, aponte para **adicionar**e, em seguida, clique em **novo projeto**.  
  
2.  No painel de modelos, expanda **Visual C#** ou **Visual Basic**e, em seguida, expanda **Office/SharePoint**.  
  
3.  Em expandidos **Office/SharePoint** nó, selecione o **suplementos do Office** nó.  
  
4.  Na lista de modelos de projeto, selecione o **pasta de trabalho do Excel 2010** ou **pasta de trabalho do Excel 2013** projeto.  
  
5.  No **nome** , digite **AdventureWorksReport**. Não modifique o local.  
  
6.  Clique em **OK**.  
  
     O **Visual Studio Tools para Office Project Wizard** é aberto.  
  
7.  Certifique-se de que **criar um novo documento** está selecionado e clique em **Okey**.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Abre o **AdventureWorksReport** pasta de trabalho no designer e adiciona o **AdventureWorksReport** projeto **Gerenciador de soluções**.  
  
## <a name="adding-the-dataset-to-data-sources-in-the-excel-workbook-project"></a>Adicionando o conjunto de dados para fontes de dados no projeto de pasta de trabalho do Excel  
 Antes de você poder exibir o conjunto de dados na pasta de trabalho do Excel, adicione primeiro o conjunto de dados para fontes de dados no projeto de pasta de trabalho do Excel.  
  
#### <a name="to-add-the-dataset-to-the-data-sources-in-the-excel-workbook-project"></a>Para adicionar o conjunto de dados para as fontes de dados no projeto de pasta de trabalho do Excel  
  
1.  Em **Solution Explorer**, clique duas vezes em **Sheet1.cs** ou **Sheet1.vb** sob o **AdventureWorksReport** projeto.  
  
     A pasta de trabalho é aberto no designer.  
  
2.  Sobre o **dados** menu, clique em **adicionar nova fonte de dados**.  
  
     O **Assistente de configuração de fonte de dados** é aberto.  
  
3.  Clique em **objeto**e, em seguida, clique em **próximo**.  
  
4.  No **selecionar o objeto que deseja vincular** à página, clique em **adicionar referência**.  
  
5.  Sobre o **projetos** , clique em **AdventureWorksDataSet** e, em seguida, clique em **Okey**.  
  
6.  Sob o **AdventureWorksDataSet** namespace do **AdventureWorksDataSet** assembly, clique em **AdventureWorksLTDataSet** e, em seguida, clique em **concluir** .  
  
     O **fontes de dados** janela é aberta, e **AdventureWorksLTDataSet** é adicionado à lista de fontes de dados.  
  
## <a name="creating-a-listobject-that-is-bound-to-an-instance-of-the-dataset"></a>Criando um ListObject que está associado a uma instância do conjunto de dados  
 Para exibir o conjunto de dados na pasta de trabalho, crie um <xref:Microsoft.Office.Tools.Excel.ListObject> que está associado a uma instância do conjunto de dados. Para obter mais informações sobre controles de associação de dados, consulte [ligar dados a controles em soluções do Office](../vsto/binding-data-to-controls-in-office-solutions.md).  
  
#### <a name="to-create-a-listobject-that-is-bound-to-an-instance-of-the-dataset"></a>Para criar um ListObject que está associado a uma instância do conjunto de dados  
  
1.  No **fontes de dados** janela, expanda o **AdventureWorksLTDataSet** nó **AdventureWorksDataSet**.  
  
2.  Selecione o **produto** nó, clique na seta suspensa que aparece e, em seguida, selecione **ListObject** na lista suspensa.  
  
     Se a seta suspensa não aparecer, confirme que a pasta de trabalho está aberta no designer.  
  
3.  Arraste o **produto** tabela para a célula A1.  
  
     Um <xref:Microsoft.Office.Tools.Excel.ListObject> controle chamado `productListObject` é criado na planilha, iniciando na célula A1. Ao mesmo tempo, um objeto de conjunto de dados chamado `adventureWorksLTDataSet` e um <xref:System.Windows.Forms.BindingSource> chamado `productBindingSource` são adicionados ao projeto. O <xref:Microsoft.Office.Tools.Excel.ListObject> está associada ao <xref:System.Windows.Forms.BindingSource>, que por sua vez é associado ao objeto de conjunto de dados.  
  
## <a name="adding-the-dataset-to-the-data-cache"></a>Adicionando o conjunto de dados para o Cache de dados  
 Para habilitar o código fora do projeto de pasta de trabalho do Excel para acessar o conjunto de dados na pasta de trabalho, você deve adicionar o conjunto de dados para o cache de dados. Para obter mais informações sobre o cache de dados, consulte [dados armazenados em cache em personalizações no nível do documento](../vsto/cached-data-in-document-level-customizations.md) e [Caching Data](../vsto/caching-data.md).  
  
#### <a name="to-add-the-dataset-to-the-data-cache"></a>Para adicionar o conjunto de dados para o cache de dados  
  
1.  No designer, clique em **adventureWorksLTDataSet**.  
  
2.  No **propriedades** janela, defina o **modificadores** propriedade **público**.  
  
3.  Definir o **CacheInDocument** propriedade **True**.  
  
## <a name="initializing-the-dataset-in-the-workbook"></a>Inicializando o conjunto de dados na pasta de trabalho  
 Antes de você pode recuperar os dados do conjunto de dados em cache usando o aplicativo de console, você deve primeiro preencher o conjunto de dados armazenados em cache com dados.  
  
#### <a name="to-initialize-the-dataset-in-the-workbook"></a>Para inicializar o conjunto de dados na pasta de trabalho  
  
1.  Em **Solution Explorer**, com o botão direito do **Sheet1.cs** ou **Sheet1.vb** de arquivo e clique em **Exibir código**.  
  
2.  Substitua o `Sheet1_Startup` manipulador de eventos com o código a seguir. Esse código usa uma instância do `ProductTableAdapter` classe definida no **AdventureWorksDataSet** projeto para preencher o conjunto de dados armazenados em cache com dados, se ela está vazia.  
  
     [!code-csharp[Trin_CachedDataWalkthroughs#8](../vsto/codesnippet/CSharp/AdventureWorksDataSet/AdventureWorksReport/Sheet1.cs#8)]
     [!code-vb[Trin_CachedDataWalkthroughs#8](../vsto/codesnippet/VisualBasic/AdventureWorksDataSet/AdventureWorksReport/Sheet1.vb#8)]  
  
## <a name="checkpoint"></a>Ponto de verificação  
 Compilar e executar o projeto de pasta de trabalho do Excel para garantir que compila e executa sem erros. Essa operação também preenche o conjunto de dados armazenados em cache e salva os dados na pasta de trabalho.  
  
#### <a name="to-build-and-run-the-project"></a>Para compilar e executar o projeto  
  
1.  Em **Solution Explorer**, com o botão direito do **AdventureWorksReport** de projeto, escolha **depurar**e, em seguida, clique em **iniciar nova instância**.  
  
     O projeto é compilado e abre a pasta de trabalho no Excel. Verifique o seguinte:  
  
    -   O <xref:Microsoft.Office.Tools.Excel.ListObject> preenche com dados.  
  
    -   O valor de **ListPrice** coluna para a primeira linha do <xref:Microsoft.Office.Tools.Excel.ListObject> é 1431.5. Posteriormente neste passo a passo, você usará um aplicativo de console para modificar os valores de **ListPrice** coluna.  
  
2.  Salve a pasta de trabalho. Não modifique o nome do arquivo ou o local da pasta de trabalho.  
  
3.  Feche o Excel.  
  
## <a name="creating-a-console-application-project"></a>Criando um projeto de aplicativo de Console  
 Crie um projeto de aplicativo do console a ser usado para modificar os dados no conjunto de dados armazenados em cache na pasta de trabalho.  
  
#### <a name="to-create-the-console-application-project"></a>Para criar o projeto de aplicativo de console  
  
1.  Em **Solution Explorer**, com o botão direito do **AdventureWorksDataSet** solução, aponte para **adicionar**e, em seguida, clique em **novo projeto**.  
  
2.  No **tipos de projeto** painel, expanda **Visual C#** ou **Visual Basic**e, em seguida, clique em **Windows**.  
  
3.  No **modelos** painel, selecione **aplicativo de Console**.  
  
4.  No **nome** , digite **DataReader**. Não modifique o local.  
  
5.  Clique em **OK**.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Adiciona o **DataReader** projeto **Solution Explorer** e abre o **Program.cs** ou **Module1. vb** arquivo de código.  
  
## <a name="retrieving-data-from-the-cached-dataset-by-using-the-console-application"></a>Recuperando dados do conjunto de dados em cache usando o aplicativo de Console  
 Use o <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> classe no aplicativo de console para ler os dados em um local `AdventureWorksLTDataSet` objeto. Para confirmar que o conjunto de dados local foi inicializado com dados do conjunto de dados armazenados em cache, o aplicativo exibe o número de linhas no conjunto de dados local.  
  
#### <a name="to-retrieve-data-from-the-cached-dataset"></a>Para recuperar dados do conjunto de dados armazenados em cache  
  
1.  Em **Solution Explorer**, com o botão direito do **DataReader** do projeto e clique em **adicionar referência**.  
  
2.  Sobre o **.NET** , selecione Microsoft.VisualStudio.Tools.Applications.ServerDocument.  
  
3.  Clique em **OK**.  
  
4.  Em **Solution Explorer**, com o botão direito do **DataReader** do projeto e clique em **adicionar referência**.  
  
5.  Sobre o **projetos** guia, selecione **AdventureWorksDataSet**e clique em **Okey**.  
  
6.  Abra o arquivo Program.cs ou Module1. vb no Editor de códigos.  
  
7.  Adicione o seguinte **usando** (para c#) ou **Imports** (para Visual Basic) à parte superior do arquivo de código.  
  
     [!code-csharp[Trin_CachedDataWalkthroughs#1](../vsto/codesnippet/CSharp/AdventureWorksDataSet/DataWriter/Program.cs#1)]
     [!code-vb[Trin_CachedDataWalkthroughs#1](../vsto/codesnippet/VisualBasic/AdventureWorksDataSet/DataWriter/Module1.vb#1)]  
  
8.  Adicione o seguinte código ao método de `Main` . Esse código declara os seguintes objetos:  
  
    -   Uma instância do `AdventureWorksLTDataSet` tipo que é definido no **AdventureWorksDataSet** projeto.  
  
    -   O caminho para a pasta de trabalho na pasta de compilação de AdventureWorksReport o **AdventureWorksReport** projeto.  
  
    -   Um <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> objeto a ser usado para acessar o cache de dados na pasta de trabalho.  
  
        > [!NOTE]  
        >  O código a seguir supõe que a pasta de trabalho é salvo usando a extensão. xlsx. Se a pasta de trabalho em seu projeto tem uma extensão diferente, modifique o caminho conforme necessário.  
  
     [!code-csharp[Trin_CachedDataWalkthroughs#10](../vsto/codesnippet/CSharp/AdventureWorksDataSet/DataWriter/Program.cs#10)]
     [!code-vb[Trin_CachedDataWalkthroughs#10](../vsto/codesnippet/VisualBasic/AdventureWorksDataSet/DataWriter/Module1.vb#10)]  
  
9. Adicione o seguinte código para o `Main` método após o código que você adicionou na etapa anterior. Esse código executa as seguintes tarefas:  
  
    -   Ele usa o <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A> propriedade o <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> classe para acessar o conjunto de dados armazenados em cache na pasta de trabalho.  
  
    -   Ele lê os dados do conjunto de dados armazenados em cache no conjunto de dados local.  
  
    -   Ele exibe o número de linhas no conjunto de dados local para confirmar que ela tem dados.  
  
     [!code-csharp[Trin_CachedDataWalkthroughs#11](../vsto/codesnippet/CSharp/AdventureWorksDataSet/DataWriter/Program.cs#11)]
     [!code-vb[Trin_CachedDataWalkthroughs#11](../vsto/codesnippet/VisualBasic/AdventureWorksDataSet/DataWriter/Module1.vb#11)]  
  
10. No **criar** menu, clique em **criar DataReader**.  
  
## <a name="testing-the-project"></a>O projeto de teste  
 Quando você executa o aplicativo de console, ele exibe o número de linhas no conjunto de dados local.  
  
#### <a name="to-test-the-workbook"></a>Para testar a pasta de trabalho  
  
1.  Em **Solution Explorer**, com o botão direito do **DataReader** de projeto, aponte para **depurar**e, em seguida, clique em **iniciar nova instância**.  
  
     Verifique se que o aplicativo relata que o conjunto de dados local tem 295 linhas.  
  
2.  Pressione ENTER para fechar o aplicativo.  
  
## <a name="next-steps"></a>Próximas etapas  
 Você pode aprender mais sobre como trabalhar com dados armazenados em cache com estes tópicos:  
  
-   Alterar os dados de um conjunto de dados armazenados em cache sem iniciar o Excel. Para obter mais informações, consulte [passo a passo: alterando dados armazenados em cache em uma pasta de trabalho em um servidor](../vsto/walkthrough-changing-cached-data-in-a-workbook-on-a-server.md).  
  
## <a name="see-also"></a>Consulte também  
 [Passo a passo: Inserindo dados em uma pasta de trabalho em um servidor](../vsto/walkthrough-inserting-data-into-a-workbook-on-a-server.md)   
 [Passo a passo: Alterando dados armazenados em cache em uma pasta de trabalho em um servidor](../vsto/walkthrough-changing-cached-data-in-a-workbook-on-a-server.md)   
 [Conectando-se a dados em aplicativos do Windows Forms](/visualstudio/data-tools/connecting-to-data-in-windows-forms-applications)  
  
  