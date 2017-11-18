---
title: "Adicionar controles personalizados à janela fontes de dados | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.datasource.howtoaddcustomcontrol
helpviewer_keywords:
- Data Sources Window, adding controls
- controls [Visual Studio], adding to Data Sources Window
- DefaultBindingPropertyAttribute class, using
- LookupBindingPropertiesAttribute class, using
- ComplexBindingPropertiesAttribute class, using
- Data Sources Window, selecting controls
ms.assetid: 8c43e7d2-ba94-4d9b-96de-3aa971955afd
caps.latest.revision: "42"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: d1efd7051d9119c4d0e6643c1d42e78d9cdde7cf
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="add-custom-controls-to-the-data-sources-window"></a>Adicionar controles personalizados à janela fontes de dados
Quando você arrasta um item a partir de **fontes de dados** janela para uma superfície de design para criar um controle associado a dados, você pode selecionar o tipo de controle que você criar. Cada item na janela tem uma lista suspensa que exibe os controles que você pode escolher. O conjunto de controles associados a cada item é determinado pelo tipo de dados do item. Se o controle que você deseja criar não aparecer na lista, você pode seguir as instruções neste tópico para adicionar o controle à lista.  
  
 Para obter mais informações sobre como selecionar controles associados a dados para criar para itens de **fontes de dados** janela, consulte [definir o controle a ser criado quando arrastado da janela fontes de dados](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).  
  
> [!NOTE]
>  As caixas de diálogo e os comandos do menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da edição ou das configurações ativas. Para alterar as configurações, no **ferramentas** menu, selecione **importar e exportar configurações**. Para obter mais informações, confira [Personalizar o IDE do Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
##  <a name="customizinglist"></a>Personalizar a lista de controles ligáveis para um tipo de dados  
 Para adicionar ou remover controles da lista de controles disponíveis para itens de **fontes de dados** janela que têm um tipo de dados específico, execute as seguintes etapas.  
  
#### <a name="to-select-the-controls-to-be-listed-for-a-data-type"></a>Para selecionar os controles a serem listados para um tipo de dados  
  
1.  Certifique-se de que o Designer do WPF ou o Designer de formulários do Windows está aberto.  
  
2.  No **fontes de dados** janela, clique em um item que faz parte de uma fonte de dados que você adicionou à janela e clique no menu suspenso para o item.  
  
3.  No menu suspenso, clique em **personalizar**. Uma das seguintes caixas de diálogo é aberta:  
  
    -   Se o Windows Forms Designer é aberto, o **personalização da interface do usuário de dados** página do **opções** caixa de diálogo é aberta.  
  
    -   Se o WPF Designer estiver aberto, o **personalizar associação de controle** caixa de diálogo é aberta.  
  
4.  Na caixa de diálogo, selecione um tipo de dados de **tipo de dados** lista suspensa.  
  
    -   Para personalizar a lista de controles para uma tabela ou objeto, selecione **[lista]**.  
  
    -   Para personalizar a lista de controles para uma coluna de uma tabela ou uma propriedade de um objeto, selecione o tipo de dados da coluna ou propriedade no armazenamento de dados subjacente.  
  
    -   Para personalizar a lista de controles para exibir os objetos de dados que têm formas definidas pelo usuário, selecione **[Other]**. Por exemplo, selecione **[Other]** se seu aplicativo tiver um controle personalizado que exibe dados de mais de uma propriedade de um objeto específico.  
  
5.  No **associados a controles** caixa, selecione cada controle que você deseja estar disponíveis para o tipo de dados selecionado ou desmarque a seleção de qualquer controle que você deseja remover da lista.  
  
    > [!NOTE]
    >  Se o controle que você deseja selecionar não aparecerá no **associados a controles** caixa, você deve adicionar o controle à lista. Para obter mais informações, consulte [adicionando controles a lista de controles de associados para um tipo de dados](#addingcontrols).  
  
6.  Clique em **OK**.  
  
7.  No **fontes de dados** janela, clique em um item de dados que você associou a apenas um ou mais controles de tipo e clique no menu suspenso para o item.  
  
     Os controles que você selecionou no **associados a controles** caixa agora aparecem no menu suspenso para o item.  
  
##  <a name="addingcontrols"></a>Adicionar controles à lista de controles associados para um tipo de dados  
 Se você deseja associar um controle com um tipo de dados, mas o controle não aparecer no **associados a controles** caixa, você deve adicionar o controle à lista. O controle deve estar localizado na solução atual ou em um assembly referenciado. Ele também deve estar disponível no **caixa de ferramentas**, e ter um atributo que especifica o comportamento de associação de dados do controle.  
  
#### <a name="to-add-controls-to-the-list-of-associated-controls"></a>Para adicionar controles à lista de controles associados  
  
1.  Adicione o controle desejado para o **caixa de ferramentas** clicando com o **caixa de ferramentas** e selecionando **escolher itens**.  
  
     O controle deve ter um dos atributos a seguir.  
  
    |Atributo|Descrição|  
    |---------------|-----------------|  
    |<xref:System.ComponentModel.DefaultBindingPropertyAttribute>|Implemente esse atributo em controles simples que exibem uma única coluna (ou propriedade) de dados, como um <xref:System.Windows.Forms.TextBox>.|  
    |<xref:System.ComponentModel.ComplexBindingPropertiesAttribute>|Implementar este atributo em controles que exibem listas (ou tabelas) de dados, como um <xref:System.Windows.Forms.DataGridView>.|  
    |<xref:System.ComponentModel.LookupBindingPropertiesAttribute>|Implementar este atributo em controles que exibem listas (ou tabelas) de dados, mas também precisa apresentar uma única coluna ou propriedade, como um <xref:System.Windows.Forms.ComboBox>.|  
  
2.  Para formulários do Windows, no **opções** caixa de diálogo, abra o **personalização da interface do usuário de dados** página. Ou, para WPF, abra o **personalizar associação de controle** caixa de diálogo. Para obter mais informações, consulte [personalizar a lista de controles ligáveis para um tipo de dados](#customizinglist).  
  
3.  No **associados a controles** caixa, o controle que você acabou de adicionar para o **caixa de ferramentas** agora deve aparecer.  
  
    > [!NOTE]
    >  Somente controles que estão localizados na solução atual ou em um assembly referenciado podem ser adicionados à lista de controles associados. (Os controles também devem implementar um dos atributos de associação de dados na tabela anterior.) Para associar dados a um controle personalizado que não está disponível na **fontes de dados** janela, arraste o controle do **caixa de ferramentas** para a superfície de design e, em seguida, arraste o item para vincular a partir de **dados Fontes** janela para o controle.  
  
## <a name="see-also"></a>Consulte também  
 [Associar controles a dados no Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)