---
redirect_url: /visualstudio/data-tools/bind-windows-forms-controls-to-data-in-visual-studio
ms.openlocfilehash: 5ba8ada294275a99aab27ff9c249d6c3d8e17da3
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/09/2017
---
título: "controles de formulários do Windows de ligação de dados | Microsoft Docs"Custom:" "MS. Date: Reviewer" 11/04/2016":" "MS. Suite:" "tgt_pltfrm:" "MS. Topic:"artigo"helpviewer_keywords: 
  - "Exibindo dados, controles de formulários do Windows"
  - "Windows Forms, exibição de dados"
  - "fontes de dados, exibindo"
  - "dados [Windows Forms], exibindo" MS. AssetID: 0163a34a-38cb-40b9-8f38-3058a90caf21 caps.latest.revision: 28 autor: author "gewarren": "gewarren" manager: ghogen MS. Technology: "ferramentas de dados vs"
---
# <a name="bind-windows-forms-controls-to-data"></a>Vincular controles de Windows Forms a dados
Você pode vincular fontes de dados a controles, arrastando objetos do **fontes de dados** janela em um formulário do Windows ou em um controle existente em um formulário. Antes de arrastar itens, você pode definir o tipo de controle que você deseja associar. Valores diferentes são exibidos dependendo se você escolher a tabela em si, ou uma coluna individual.  Você também pode definir valores personalizados. Para uma tabela, "Detalhes" significa que cada coluna é associada a um controle separado.  

![Associar a fonte de dados ao DataGridView](../data-tools/media/raddata-bind-data-source-to-datagridview.png "raddata fonte de dados de ligação para DataGridView")  
  
[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
## <a name="bind-to--data-in-a-datagridview-control"></a>Associar dados em um controle DataGridView  
Para DataGridView, a tabela inteira é vinculada ao controle único. Quando você arrasta uma DataGridView do formulário, uma ferramenta da faixa para navegar pelos registros (<xref:System.Windows.Forms.BindingNavigator>) também será exibida. Um [DataSet](../data-tools/dataset-tools-in-visual-studio.md), [TableAdapter](../data-tools/create-and-configure-tableadapters.md), <xref:System.Windows.Forms.BindingSource>, e <xref:System.Windows.Forms.BindingNavigator> aparecem na bandeja do componente. A ilustração a seguir, um TableAdapterManager também é adicionado porque a tabela clientes tem uma relação à tabela Orders. Essas variáveis todos são declaradas no código gerado automaticamente como membros particulares na classe de formulário. O código gerado automaticamente para preencher o DataGridView está localizado no manipulador de eventos form_load. O código para salvar os dados para atualizar o banco de dados está localizado no manipulador de eventos Salvar para BindingNavigator. Você pode mover ou modificar este código conforme necessário.  
  
 ![GridView com BindingNavigator](../data-tools/media/raddata-gridview-with-bindingnavigator.png "raddata GridView com BindingNavigator")  
  
 Você pode personalizar o comportamento de DataGridView e BindingNavigator clicando na marca inteligente no canto superior direito de cada um:  
  
 ![Marcas inteligentes de DataGridView e associação de navegador](../data-tools/media/raddata-datagridview-and-binding-navigator-smart-tags.png "raddata DataGridView e navegador de associação de marcas inteligentes")  
  
 Se os controles de seu aplicativo precisa não estiverem disponível no **fontes de dados** janela, você pode adicionar controles. Para obter mais informações, consulte [adicionar controles personalizados à janela fontes de dados](../data-tools/add-custom-controls-to-the-data-sources-window.md).  
  
 Você também pode arrastar itens do **fontes de dados** window para controles já em um formulário para associar o controle aos dados. Um controle que já está associado a dados tiver seus dados associações redefinidas para o item mais recentemente arrastado para ele. Para destinos válidos para arrastar, controles devem ser capazes de exibir o tipo de dados subjacentes do item arrastado para ele do **fontes de dados** janela. Por exemplo, não é válido arrastar um item que tem um tipo de dados <xref:System.DateTime> para um <xref:System.Windows.Forms.CheckBox>, porque o <xref:System.Windows.Forms.CheckBox> não é capaz de exibir uma data.  
  
## <a name="bind-to--data-in-individual-controls"></a>Associar a dados em controles individuais  
 Quando você associa uma fonte de dados para "Detalhes", cada coluna no conjunto de dados é associada a um controle separado.  
  
 ![Associar a fonte de dados para obter detalhes](../data-tools/media/raddata-bind-data-source-to-details.png "raddata fonte de dados de ligação para obter detalhes")  
  
> [!IMPORTANT]
>  Observe que, na ilustração anterior, você arrasta da propriedade pedidos da tabela Customers, não da tabela Orders. Associando a propriedade Orders, feitos no DataGridView de comandos de navegação são refletidos imediatamente em controles de detalhes. Se você arrastou da tabela Orders, os controles ainda poderá estar associados ao conjunto de dados, mas não eles não poderiam ser sincronizados com o DataGridView.  
  
 A ilustração a seguir mostra o padrão controles associados a dados que são adicionados para o formulário depois que a propriedade de pedidos na tabela Customers é associada a "Detalhes" no **fontes de dados** janela.  
  
 ![Tabela Orders associado aos detalhes](../data-tools/media/raddata-orders-table-bound-to-details.png "raddata pedidos tabela vinculada detalhes")  
  
 Observe também que cada controle tem uma marca inteligente. Essa marca permite que personalizações que se aplicam a esse controle.  
  
## <a name="see-also"></a>Consulte também  
 [Associando controles do Windows Forms a dados no Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)