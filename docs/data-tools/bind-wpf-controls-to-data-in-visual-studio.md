---
title: Vincular controles WPF a dados no Visual Studio - parte 1 | Microsoft Docs
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
ms.assetid: e05a1e0c-5082-479d-bbc9-d395b0bc6580
caps.latest.revision: "36"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.workload: data-storage
ms.openlocfilehash: 77c56d70c6fc3dd3dac9a563c146d8bab2c6f699
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="bind-wpf-controls-to-data-in-visual-studio"></a>Vincular controles WPF a dados no Visual Studio
É possível exibir dados para usuários do aplicativo associando-se dados a controles [!INCLUDE[TLA#tla_titlewinclient](../data-tools/includes/tlasharptla_titlewinclient_md.md)]. Para criar esses controles associados a dados, você pode arrastar itens do **fontes de dados** janela para o [!INCLUDE[wpfdesigner_current_short](../data-tools/includes/wpfdesigner_current_short_md.md)] em [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Este tópico descreve algumas das tarefas, ferramentas e classes mais comuns que é possível usar para criar aplicativos [!INCLUDE[TLA#tla_titlewinclient](../data-tools/includes/tlasharptla_titlewinclient_md.md)] de associação de dados.  
  
 Para obter informações gerais sobre como criar controles associados a dados em [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], consulte [associar controles a dados no Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md). Para obter mais informações sobre [!INCLUDE[TLA#tla_titlewinclient](../data-tools/includes/tlasharptla_titlewinclient_md.md)] associação de dados, consulte [visão geral de associação de dados](/dotnet/framework/wpf/data/data-binding-overview).  
  
## <a name="tasks-involved-in-binding-wpf-controls-to-data"></a>Tarefas envolvidas na associando controles WPF a dados  
 A tabela a seguir lista as tarefas que podem ser feitas arrastando itens a partir de **fontes de dados** janela para o [!INCLUDE[wpfdesigner_current_short](../data-tools/includes/wpfdesigner_current_short_md.md)].  
  
|Tarefa|Mais informações|  
|----------|----------------------|  
|Crie novos controles de associação de dados.<br /><br /> Associe controles existentes a dados.|[Associar controles do WPF a um conjunto de dados](../data-tools/bind-wpf-controls-to-a-dataset.md)|  
|Crie controles que exibam dados relacionados em uma relação pai-filho: quando o usuário seleciona um registro de dados pai em um controle, outro controle exibe dados filho relacionados ao registro selecionado.|[Exibir dados relacionados em aplicativos WPF](../data-tools/display-related-data-in-wpf-applications.md)|  
|Criar um *tabela de pesquisa* que exibe informações de uma tabela com base no valor de um campo de chave estrangeira em outra tabela.|[Criar tabelas de pesquisa em aplicativos do WPF](../data-tools/create-lookup-tables-in-wpf-applications.md)|  
|Associe um controle a uma imagem em um banco de dados.|[Associar controles a imagens de um banco de dados](../data-tools/bind-controls-to-pictures-from-a-database.md)|  
  
## <a name="valid-drop-targets"></a>Destinos de soltar válido  
 Você pode arrastar itens no **fontes de dados** janela apenas para destinos de soltar válidas no [!INCLUDE[wpfdesigner_current_short](../data-tools/includes/wpfdesigner_current_short_md.md)]. Existem dois tipos principais de destinos depósitos válidos: contêineres e controles. Um contêiner é um elemento de interface do usuário que normalmente contém controles. Por exemplo, uma grade é um contêiner, assim como uma janela.  
  
## <a name="generated-xaml-and-code"></a>Gerado XAML e código  
 Quando você arrasta um item a partir de **fontes de dados** janela para o [!INCLUDE[wpfdesigner_current_short](../data-tools/includes/wpfdesigner_current_short_md.md)], [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] gera [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] que define um novo controle de associação de dados (ou associa um controle existente para a fonte de dados). Para algumas fontes de dados, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] também gera código no arquivo code-behind que preenche a fonte de dados com dados.  
  
 A seguinte tabela lista o [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] e código que [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] gera para cada tipo de fonte de dados de **fontes de dados** janela.  
  
|Fonte de dados|Gerar XAML que associa um controle à fonte de dados|Gerar código que preenche a fonte de dados com dados|  
|-----------------|-----------------------------------------------------------|--------------------------------------------------------|  
|Conjunto de dados|Sim|Sim|  
|[!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)]|Sim|Sim|  
|Serviço|Sim|Não|  
|Objeto|Sim|Não|  
  
### <a name="datasets"></a>Conjuntos de dados  
 Quando você arrasta uma tabela ou coluna do **fontes de dados** janela para o designer, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] gera [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] que faz o seguinte:  
  
-   Adiciona o conjunto de dados e um novo <xref:System.Windows.Data.CollectionViewSource> aos recursos do contêiner arrastados para o item. O <xref:System.Windows.Data.CollectionViewSource> é um objeto que pode ser usado para navegar e exibir os dados no conjunto de dados.  
  
-   Cria uma associação de dados para um controle. Se você arrastar o item para um controle existente no designer, o XAML associará o controle ao item. Se você arrastar o item para um contêiner, o XAML cria o controle selecionado para o item arrastado e ele vincula o controle para o item. O controle é criado dentro de um novo <xref:System.Windows.Controls.Grid>.  
  
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] também faz as seguintes alterações no arquivo code-behind:  
  
-   Cria um manipulador de eventos <xref:System.Windows.FrameworkElement.Loaded> para o elemento [!INCLUDE[TLA2#tla_ui](../data-tools/includes/tla2sharptla_ui_md.md)] que contém o controle. O manipulador de eventos preenche a tabela com dados, recupera o <xref:System.Windows.Data.CollectionViewSource> dos recursos do contêiner e, em seguida, torna o primeiro item dados o item atual. Se um <xref:System.Windows.FrameworkElement.Loaded> já existe um manipulador de eventos, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] adiciona esse código para o manipulador de eventos existente.  
  
### <a name="entity-data-models"></a>Modelos de dados de entidade  
 Quando você arrasta uma entidade ou uma propriedade de entidade do **fontes de dados** janela para o designer, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] gera [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] que faz o seguinte:  
  
-   Adiciona um novo <xref:System.Windows.Data.CollectionViewSource> aos recursos do contêiner arrastados para o item. O <xref:System.Windows.Data.CollectionViewSource> é um objeto que pode ser usado para navegar e exibir os dados na entidade.  
  
-   Cria uma associação de dados para um controle. Se você arrastar o item para um controle existente no designer, o [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] associará o controle ao item. Se você arrastar o item a um contêiner, o [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] cria o controle que foi selecionado para o item arrastado e ele vincula o controle para o item. O controle é criado dentro de um novo <xref:System.Windows.Controls.Grid>.  
  
O Visual Studio também faz as seguintes alterações no arquivo code-behind:  
  
-   Adiciona um novo método que retorna uma consulta para a entidade arrastada para o designer (ou a entidade que contém a propriedade que você arrastou para o designer). O novo método tem o nome Get*EntityName*consulta, onde *EntityName* é o nome da entidade.  
  
-   Cria um manipulador de eventos <xref:System.Windows.FrameworkElement.Loaded> para o elemento [!INCLUDE[TLA2#tla_ui](../data-tools/includes/tla2sharptla_ui_md.md)] que contém o controle. O manipulador de eventos chama Get*EntityName*consultar o método para preencher a entidade com dados, recupera o <xref:System.Windows.Data.CollectionViewSource> de contêiner recursos e, em seguida, torna os primeiros dados de item do item atual. Se um <xref:System.Windows.FrameworkElement.Loaded> já existe um manipulador de eventos, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] adiciona esse código para o manipulador de eventos existente.  
  
### <a name="services"></a>Serviços  
 Quando você arrasta um objeto de serviço ou a propriedade de **fontes de dados** janela para o designer, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] gera [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] que cria um controle associado a dados (ou associa um controle existente para o objeto ou propriedade). No entanto, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] não gera o código que preenche o objeto de serviço do proxy com dados. Você deve gravar esse código sozinho. Para obter um exemplo que demonstra como fazer isso, consulte [WPF associar controles a um WCF data Services](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md).  
  
 O Visual Studio gera XAML, que faz o seguinte:  
  
-   Adiciona um novo <xref:System.Windows.Data.CollectionViewSource> aos recursos do contêiner arrastados para o item. O <xref:System.Windows.Data.CollectionViewSource> é um objeto que pode ser usado para navegar e exibir os dados no objeto retornado pelo serviço.  
  
-   Cria uma associação de dados para um controle. Se você arrastar o item para um controle existente no designer, o [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] associará o controle ao item. Se você arrastar o item a um contêiner, o [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] cria o controle que foi selecionado para o item arrastado e ele vincula o controle para o item. O controle é criado dentro de um novo <xref:System.Windows.Controls.Grid>.  
  
### <a name="objects"></a>Objetos  
 Quando você arrasta um objeto ou propriedade do **fontes de dados** janela para o designer, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] gera [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] que cria um controle associado a dados (ou associa um controle existente para o objeto ou propriedade). No entanto, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] não gera código para preencher o objeto com dados. Você deve gravar esse código sozinho.  
  
> [!NOTE]
>  Classes personalizadas devem ser público e, por padrão, tem um construtor sem parâmetros. Eles classes can'tbe aninhados que tem um "ponto" na sua sintaxe. Para obter mais informações, consulte [XAML e Classes personalizadas para WPF](/dotnet/framework/wpf/advanced/xaml-and-custom-classes-for-wpf).  
  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]gera [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] que faz o seguinte:  
  
-   Adiciona um novo <xref:System.Windows.Data.CollectionViewSource> aos recursos do contêiner arrastados para o item. O <xref:System.Windows.Data.CollectionViewSource> é um objeto que pode ser usado para navegar e exibir os dados no objeto.  
  
-   Cria uma associação de dados para um controle. Se você arrastar o item para um controle existente no designer, o XAML associará o controle ao item. Se você arrastar o item para um contêiner, o XAML cria o controle selecionado para o item arrastado e ele vincula o controle para o item. O controle é criado dentro de um novo <xref:System.Windows.Controls.Grid>.  
  
## <a name="see-also"></a>Consulte também
[Associar controles a dados no Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)
