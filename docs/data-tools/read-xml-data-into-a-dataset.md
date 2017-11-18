---
title: Dados XML de leitura em um conjunto de dados | Microsoft Docs
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
- reading XML
- data access [Visual Studio], XML data
- reading files, XML
- data [Visual Studio], reading from XML files
- reading data, XML files
- XML [Visual Studio], reading
- XML documents, reading
- datasets [Visual Basic], reading XML data
ms.assetid: fae72958-0893-47d6-b3dd-9d42418418e4
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: 31c17df9b8b3e0a0b54d99f95e8a3d5704140cf7
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="read-xml-data-into-a-dataset"></a>Ler dados XML em um conjunto de dados
ADO.NET fornece métodos simples para trabalhar com dados XML. Neste passo a passo, você deve criar um aplicativo do Windows que carrega dados XML em um conjunto de dados. O conjunto de dados é exibido em um <xref:System.Windows.Forms.DataGridView> controle. Por fim, um esquema XML com base no conteúdo do arquivo XML é exibido na caixa de texto.  
  
 Este passo a passo consiste em cinco etapas principais:  
  
1.  Criar um novo projeto  
  
2.  Criando um arquivo XML a ser lido para o conjunto de dados  
  
3.  Criando a interface do usuário  
  
4.  Criando o conjunto de dados, ler o arquivo XML e exibi-los em um <xref:System.Windows.Forms.DataGridView> controle  
  
5.  Adicionando código para exibir o esquema XML com base no arquivo XML em um <xref:System.Windows.Forms.TextBox> controle  
  
> [!NOTE]
>  As caixas de diálogo e comandos de menu encontrados podem diferir daqueles descritos na Ajuda, dependendo de suas configurações ativas ou a edição que você está usando. Para alterar as configurações, no **ferramentas** menu, selecione **importar e exportar configurações**. Para obter mais informações, confira [Personalizar o IDE do Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="create-a-new-project"></a>Criar um novo projeto  
 Nesta etapa, você deve criar um projeto Visual Basic ou Visual c# que contém este passo a passo.  
  
#### <a name="to-create-the-new-windows-project"></a>Para criar o novo projeto do Windows  
  
1. No Visual Studio, no **arquivo** menu, selecione **novo**, **projeto...** .  
  
2. Expanda **Visual C#** ou **Visual Basic** no painel esquerdo, selecione **área de trabalho clássica do Windows**.  

3. No painel central, selecione a **aplicativo do Windows Forms** tipo de projeto.  

4. Nomeie o projeto **ReadingXML**e, em seguida, escolha **Okey**. 
  
     O **ReadingXML** projeto é criado e adicionado ao **Gerenciador de soluções**.  
  
## <a name="generate-the-xml-file-to-be-read-into-the-dataset"></a>Gerar o arquivo XML a ser lido para o conjunto de dados  
 Como este passo a passo se concentra na leitura dos dados XML em um conjunto de dados, o conteúdo de um arquivo XML é fornecido.  
  
#### <a name="to-create-the-xml-file-that-will-be-read-into-the-dataset"></a>Para criar o arquivo XML que será lido para o conjunto de dados  
  
1.  Sobre o **projeto** menu, selecione **Adicionar Novo Item**.  
  
2.  Selecione **arquivo XML**, nomeie o arquivo `authors.xml`e, em seguida, selecione **adicionar**.  
  
     O arquivo XML carrega no designer e está pronto para edição.  
  
3.  Cole o seguinte código no editor abaixo da declaração XML:  
  
    ```xml  
    <Authors_Table>  
      <authors>  
        <au_id>172-32-1176</au_id>  
        <au_lname>White</au_lname>  
        <au_fname>Johnson</au_fname>  
        <phone>408 496-7223</phone>  
        <address>10932 Bigge Rd.</address>  
        <city>Menlo Park</city>  
        <state>CA</state>  
        <zip>94025</zip>  
        <contract>true</contract>  
      </authors>  
      <authors>  
        <au_id>213-46-8915</au_id>  
        <au_lname>Green</au_lname>  
        <au_fname>Margie</au_fname>  
        <phone>415 986-7020</phone>  
        <address>309 63rd St. #411</address>  
        <city>Oakland</city>  
        <state>CA</state>  
        <zip>94618</zip>  
        <contract>true</contract>  
      </authors>  
      <authors>  
        <au_id>238-95-7766</au_id>  
        <au_lname>Carson</au_lname>  
        <au_fname>Cheryl</au_fname>  
        <phone>415 548-7723</phone>  
        <address>589 Darwin Ln.</address>  
        <city>Berkeley</city>  
        <state>CA</state>  
        <zip>94705</zip>  
        <contract>true</contract>  
      </authors>  
      <authors>  
        <au_id>267-41-2394</au_id>  
        <au_lname>Hunter</au_lname>  
        <au_fname>Anne</au_fname>  
        <phone>408 286-2428</phone>  
        <address>22 Cleveland Av. #14</address>  
        <city>San Jose</city>  
        <state>CA</state>  
        <zip>95128</zip>  
        <contract>true</contract>  
      </authors>  
      <authors>  
        <au_id>274-80-9391</au_id>  
        <au_lname>Straight</au_lname>  
        <au_fname>Dean</au_fname>  
        <phone>415 834-2919</phone>  
        <address>5420 College Av.</address>  
        <city>Oakland</city>  
        <state>CA</state>  
        <zip>94609</zip>  
        <contract>true</contract>  
      </authors>  
    </Authors_Table>  
    ```  
  
4.  Sobre o **arquivo** menu, selecione **salvar Authors**.  
  
## <a name="create-the-user-interface"></a>Criar a interface do usuário  
 A interface do usuário para esse aplicativo consiste no seguinte:  
  
-   Um <xref:System.Windows.Forms.DataGridView> controle que exibe o conteúdo do arquivo XML como dados.  
  
-   Um <xref:System.Windows.Forms.TextBox> controle que exibe o esquema XML para o arquivo XML.  
  
-   Dois <xref:System.Windows.Forms.Button> controles.  
  
    -   Lê o arquivo XML para o conjunto de dados e o exibe em um botão de <xref:System.Windows.Forms.DataGridView> controle.  
  
    -   Um segundo botão extrai o esquema do conjunto de dados e por meio de um <xref:System.IO.StringWriter> exibe-o no <xref:System.Windows.Forms.TextBox> controle.  
  
#### <a name="to-add-controls-to-the-form"></a>Para adicionar controles ao formulário  
  
1.  Abra `Form1` no modo de design.  
  
2.  Do **caixa de ferramentas**, arraste os seguintes controles ao formulário:  
  
    -   Um <xref:System.Windows.Forms.DataGridView> controle  
  
    -   Um <xref:System.Windows.Forms.TextBox> controle  
  
    -   Dois <xref:System.Windows.Forms.Button> controles  
  
3.  Defina as seguintes propriedades:  
  
    |Controle|Propriedade|Configuração|  
    |-------------|--------------|-------------|  
    |`TextBox1`|**Multilinha**|`true`|  
    ||**ScrollBars**|**Vertical**|  
    |`Button1`|**Nome**|`ReadXmlButton`|  
    ||**Texto**|`Read XML`|  
    |`Button2`|**Nome**|`ShowSchemaButton`|  
    ||**Texto**|`Show Schema`|  
  
## <a name="create-the-dataset-that-receives-the-xml-data"></a>Criar o conjunto de dados que recebe os dados XML  
 Nesta etapa, você cria um novo conjunto de dados chamado `authors`. Para obter mais informações sobre conjuntos de dados, consulte [ferramentas do conjunto de dados no Visual Studio](../data-tools/dataset-tools-in-visual-studio.md).  
  
#### <a name="to-create-a-new-dataset-that-receives-the-xml-data"></a>Para criar um novo conjunto de dados que recebe os dados XML  
  
1.  Em **Solution Explorer**, selecione o arquivo de origem **Form1**e, em seguida, selecione o **Designer de exibição** botão o **Gerenciador de soluções** barra de ferramentas.  
  
2.  Do [caixa de ferramentas, guia dados](../ide/reference/toolbox-data-tab.md), arraste um **DataSet** para **Form1**.  
  
3.  No **Adicionar conjunto de dados** caixa de diálogo, selecione **dataset não tipado**e, em seguida, selecione **Okey**.  
  
     **DataSet1** é adicionado à bandeja do componente.  
  
4.  No **propriedades** janela, defina o **nome** e <xref:System.Data.DataSet.DataSetName%2A> propriedades`AuthorsDataSet`.  
  
## <a name="create-the-event-handler-to-read-the-xml-file-into-the-dataset"></a>Criar o manipulador de eventos para ler o arquivo XML para o conjunto de dados  
 O **Read XML** botão lê o arquivo XML para o conjunto de dados. Em seguida, ele define as propriedades no <xref:System.Windows.Forms.DataGridView> controle associá-lo ao conjunto de dados.  
  
#### <a name="to-add-code-to-the-readxmlbuttonclick-event-handler"></a>Para adicionar código ao manipulador de eventos ReadXmlButton_Click  
  
1.  Em **Solution Explorer**, selecione **Form1**e, em seguida, selecione o **Designer de exibição** botão o **Solution Explorer** barra de ferramentas.  
  
2.  Selecione o **Read XML** botão.  
  
     O **Editor de códigos** é aberto no `ReadXmlButton_Click` manipulador de eventos.  
  
3.  Digite o seguinte código para o `ReadXmlButton_Click` manipulador de eventos:  
  
     [!code-csharp[VbRaddataFillingAndExecuting#2](../data-tools/codesnippet/CSharp/read-xml-data-into-a-dataset_1.cs)]
     [!code-vb[VbRaddataFillingAndExecuting#2](../data-tools/codesnippet/VisualBasic/read-xml-data-into-a-dataset_1.vb)]  
  
4.  No `ReadXMLButton_Click` código de manipulador de eventos de alteração de `filepath =` entrada para o caminho correto.  
  
## <a name="create-the-event-handler-to-display-the-schema-in-the-textbox"></a>Criar o manipulador de eventos para exibir o esquema na caixa de texto  
 O **Show Schema** botão cria um <xref:System.IO.StringWriter> objeto que é preenchido com o esquema e é exibido no <xref:System.Windows.Forms.TextBox>controle.  
  
#### <a name="to-add-code-to-the-showschemabuttonclick-event-handler"></a>Para adicionar código ao manipulador de eventos ShowSchemaButton_Click  
  
1.  Em **Solution Explorer**, selecione **Form1**e, em seguida, selecione o **View Designer** botão.  
  
2.  Selecione o **Show Schema** botão.  
  
     O **Editor de códigos** é aberto no `ShowSchemaButton_Click` manipulador de eventos.  
  
3.  Digite o seguinte código para o `ShowSchemaButton_Click` manipulador de eventos.  
  
     [!code-csharp[VbRaddataFillingAndExecuting#3](../data-tools/codesnippet/CSharp/read-xml-data-into-a-dataset_2.cs)]
     [!code-vb[VbRaddataFillingAndExecuting#3](../data-tools/codesnippet/VisualBasic/read-xml-data-into-a-dataset_2.vb)]  
  
## <a name="test-the-form"></a>Testar o formulário  
 Agora, é possível testar o formulário para garantir que ele se comporta da forma esperada.  
  
#### <a name="to-test-the-form"></a>Para testar o formulário  
  
1.  Selecione **F5** para executar o aplicativo.  
  
2.  Selecione o **Read XML** botão.  
  
     O DataGridView exibe o conteúdo do arquivo XML.  
  
3.  Selecione o **Show Schema** botão.  
  
     A caixa de texto exibe o esquema XML para o arquivo XML.  
  
## <a name="next-steps"></a>Próximas etapas  
 Este passo a passo mostra as Noções básicas de ler um arquivo XML em um conjunto de dados, bem como criar um esquema com base no conteúdo do arquivo XML. Aqui estão algumas tarefas que você pode fazer em seguida:  
  
-   Edite os dados no dataset e grave-os de volta como XML. Para obter mais informações, consulte <xref:System.Data.DataSet.WriteXml%2A>.  
  
-   Edite os dados no conjunto de dados e grave-os em um banco de dados. Para obter mais informações, consulte [salvando dados](../data-tools/saving-data.md).  
  
## <a name="see-also"></a>Consulte também  
 [Accessing data in Visual Studio](../data-tools/accessing-data-in-visual-studio.md)      (Acessando dados no Visual Studio)  
 [Ferramentas XML no Visual Studio](../xml-tools/xml-tools-in-visual-studio.md)