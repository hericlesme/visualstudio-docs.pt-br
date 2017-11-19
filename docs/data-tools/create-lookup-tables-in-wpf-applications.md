---
title: Criar tabelas de pesquisa em aplicativos WPF | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data [WPF], displaying
- WPF, data binding in Visual Studio
- WPF data binding [Visual Studio]
- displaying data, WPF
- WPF [WPF], data
- WPF Designer, data binding
- data binding, WPF
ms.assetid: 56a1fbff-c7e8-4187-a1c1-ffd17024bc1b
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: 78322512fdc59b4ba661bca0d40d1532ac4c98e2
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/09/2017
---
# <a name="create-lookup-tables-in-wpf-applications"></a>Criar tabelas de pesquisa em aplicativos WPF
O termo *tabela de pesquisa* (às vezes chamado de um *vinculação de pesquisa*) descreve um controle que exibe informações de uma tabela de dados com base no valor de um campo de chave estrangeira em outra tabela. Você pode criar uma tabela de pesquisa, arrastando o nó principal de uma tabela pai ou objeto de **fontes de dados** window para um controle que já está associado a uma coluna ou propriedade em uma tabela filho relacionados.  
  
Por exemplo, considere uma tabela de `Orders` em um banco de dados de venda. Cada registro de `Orders` tabela inclui um `CustomerID` que indica qual cliente fez o pedido. O `CustomerID` é uma chave estrangeira que aponta para um registro de cliente no `Customers` tabela. Quando você exibe uma lista de pedidos do `Orders` tabela, talvez você queira exibir o nome do cliente real em vez do `CustomerID`. Porque o nome do cliente está sendo o `Customers` tabela, você precisa criar uma tabela de pesquisa para exibir o nome do cliente. Os usos da tabela de pesquisa a `CustomerID` valor o `Orders` registro para navegar pelo relacionamento e retornar o nome do cliente.  
  
## <a name="to-create-a-lookup-table"></a>Criar uma tabela de pesquisa  
  
1.  Adicione um dos seguintes tipos de fontes de dados com dados relacionados ao seu projeto:  
  
    -   Conjunto de dados ou modelo de dados de entidade. 
  
    -   WCF Data Service, serviço WCF ou serviço da Web. Para obter mais informações, consulte [como: conectar a dados em um serviço](../data-tools/how-to-connect-to-data-in-a-service.md).  
  
    -   objetos. Para obter mais informações, consulte [vincular a objetos no Visual Studio](bind-objects-in-visual-studio.md).  
  
    > [!NOTE]
    >  Antes de criar uma tabela de pesquisa, duas tabelas relacionadas ou objetos devem existir como uma fonte de dados para o projeto.  
  
2.  Abra o **WPF Designer**e certifique-se de que o designer contém um contêiner que é um destino válido para itens de **fontes de dados** janela.  
  
     Para obter mais informações sobre os destinos de soltar válidas, consulte [WPF associar controles a dados no Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md).  
  
3.  Sobre o **dados** menu, clique em **Mostrar fontes de dados** para abrir o **fontes de dados** janela.  
  
4.  Expanda os nós a **fontes de dados** janela, até que você pode ver a tabela pai ou objeto e a tabela filho relacionada ou objeto.  
  
    > [!NOTE]
    >  A tabela filho relacionada ou o objeto é o nó que aparece como um nó filho expansível na tabela pai ou o objeto.  
  
5.  Clique no menu suspenso do nó filho e selecione **detalhes**.  
  
6.  Expanda o nó filho.  
  
7.  Sob o nó filho, clique no menu suspenso para o item que relaciona os dados pai e filho. (No exemplo anterior, este é o **CustomerID** nó.) Selecione um dos seguintes tipos de controles que oferecem suporte à associação de pesquisa:  
  
    -   **ComboBox**  
  
    -   **ListBox**  
  
    -   **ListView**  
  
        > [!NOTE]
        >  Se o **ListBox** ou **ListView** controle não aparecer na lista, você pode adicionar esses controles à lista. Para obter informações, consulte [definir o controle a ser criado quando arrastado da janela fontes de dados](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).  
  
    -   Controle personalizado que deriva de <xref:System.Windows.Controls.Primitives.Selector>.  
  
        > [!NOTE]
        >  Para obter informações sobre como adicionar personalizado controles à lista de controles que você podem selecionar itens no **fontes de dados** janela, consulte [adicionar controles personalizados à janela fontes de dados](../data-tools/add-custom-controls-to-the-data-sources-window.md).  
  
8.  Arraste o nó filho do **fontes de dados** window para um contêiner no designer do WPF. (No exemplo anterior, o nó filho é o **pedidos** nó.)  
  
     O Visual Studio gera o XAML que cria novos controles de associação de dados para cada um dos itens que você arrasta. O XAML também adiciona um novo <xref:System.Windows.Data.CollectionViewSource> para a tabela filho ou objeto para os recursos de destino de soltar. Para algumas fontes de dados, o Visual Studio também gera código para carregar dados para a tabela ou objeto. Para obter mais informações, consulte [WPF associar controles a dados no Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md).  
  
9. Arraste o nó pai do **fontes de dados** janela para o controle de associação de pesquisa que você criou anteriormente. (No exemplo anterior, o nó pai é o **clientes** nó).  
  
     O Visual Studio define algumas propriedades do controle para configurar a associação de pesquisa. A tabela a seguir lista as propriedades que modifica o Visual Studio. Se necessário, você pode alterar essas propriedades em XAML ou no **propriedades** janela.  
  
    |Propriedade|Explicação da configuração|  
    |--------------|----------------------------|  
    |<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>|Essa propriedade especifica a coleção ou associação que é usada para obter os dados que são exibidos no controle. O Visual Studio define essa propriedade o <xref:System.Windows.Data.CollectionViewSource> para os dados pai arrastado para o controle.|  
    |<xref:System.Windows.Controls.ItemsControl.DisplayMemberPath%2A>|Essa propriedade especifica o caminho do item de dados que é exibido no controle. O Visual Studio define essa propriedade para a primeira coluna ou propriedade de dados pai, após a chave primária, que tem um tipo de dados de cadeia de caracteres.<br /><br /> Se você quiser exibir uma coluna diferente ou a propriedade dos dados pai, altere essa propriedade para o caminho de outra propriedade.|  
    |<xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A>|O Visual Studio associa essa propriedade como a coluna ou a propriedade dos dados filho que você arrastou para o designer. Esta é a chave estrangeira para os dados pai.|  
    |<xref:System.Windows.Controls.Primitives.Selector.SelectedValuePath%2A>|O Visual Studio define essa propriedade ao caminho da coluna ou a propriedade dos dados filho que é a chave estrangeira para os dados pai.|  
  
## <a name="see-also"></a>Consulte também
[Vincular controles WPF a dados no Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)   
[Exibir dados relacionados em aplicativos WPF](../data-tools/display-related-data-in-wpf-applications.md)   
[Passo a passo: exibindo dados relacionados em um aplicativo WPF](../data-tools/display-related-data-in-wpf-applications.md)