---
title: Vincular controles a dados no Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data, displaying
- data sources, displaying data
- Data Sources window
- dislaying data
ms.assetid: be8b6623-86a6-493e-ab7a-050de4661fd6
caps.latest.revision: "40"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.workload: data-storage
ms.openlocfilehash: d6a1ab26dc402d039a5e858896ec25668be8df9e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="bind-controls-to-data-in-visual-studio"></a>Vincular controles a dados no Visual Studio
Você pode exibir dados para usuários do seu aplicativo pela associação de dados a controles. Você pode criar esses controles associados a dados, arrastando itens a partir de **fontes de dados** window em uma superfície de design ou controles em uma superfície no Visual Studio.  
  
 Este tópico descreve as fontes de dados que você pode usar para criar controles associados a dados. Ele também descreve algumas das tarefas gerais envolvidas na associação de dados. Para obter detalhes mais específicos sobre como criar controles associados a dados, consulte [controla associar Windows Forms a dados no Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md) e [WPF associar controles a dados no Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md).  
  
## <a name="data-sources"></a>Fontes de dados  
 No contexto de associação de dados, uma fonte de dados representa os dados na memória que pode ser vinculado à sua interface de usuário. Em termos práticos, uma fonte de dados pode ser uma classe do Entity Framework, um conjunto de dados, um ponto de extremidade de serviço que é encapsulado em um objeto de proxy do .NET, uma classe LINQ to SQL, ou qualquer objeto .NET ou coleção. Algumas fontes de dados que você possa criar controles associados a dados arrastando itens a partir de **fontes de dados** janela, enquanto outras fontes de dados não. A tabela a seguir mostra quais fontes de dados têm suporte.  
  
|Fonte de dados|Suporte a arrastar e soltar no **Designer de formulários do Windows**|Suporte a arrastar e soltar no **WPF Designer**|Suporte a arrastar e soltar no **o Silverlight Designer**|  
|-----------------|---------------------------------------------------------------|-----------------------------------------------------|-------------------------------------------------------------|  
|Conjunto de dados|Sim|Sim|Não|  
|Modelo de Dados de Entidade|Sim<sup>1</sup>|Sim|Sim|  
|Classes LINQ to SQL|Não<sup>2</sup>|Não<sup>2</sup>|Não<sup>2</sup>|  
|Serviços (incluindo [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)], WCF serviços e serviços da web)|Sim|Sim|Sim|  
|Objeto|Sim|Sim|Sim|  
|SharePoint|Sim|Sim|Sim|  
  
 1. Gerar o modelo usando o **modelo de dados de entidade** assistente, arraste os objetos para o designer.  
  
 2. Classes LINQ to SQL não aparecem no **fontes de dados** janela. No entanto, você pode adicionar uma nova fonte de dados de objeto que é baseada em LINQ para classes SQL e, em seguida, arraste os objetos para o designer para criar controles associados a dados. Para obter mais informações, consulte [passo a passo: Criando Classes LINQ to SQL (O R Designer)](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md).  
  
## <a name="data-sources-window"></a>janela Fontes de Dados  
 Fontes de dados estão disponíveis para o projeto como itens no **fontes de dados** janela. Esta janela está visível ou é acessível a partir de **exibição** menu, quando uma superfície de design do formulário é a janela ativa em seu projeto. Você pode arrastar itens desta janela para criar controles que estão associados aos dados subjacentes, e você também pode configurar as fontes de dados clicando com o.  
  
 ![Janela fontes de dados](../data-tools/media/raddata-data-sources-window.png "raddata janela de fontes de dados")  
  
 Para cada tipo de dados que aparece no **fontes de dados** janela, um controle padrão é criado quando você arrastar o item para o designer. Antes de você arrastar um item a partir de **fontes de dados** janela, você pode alterar o controle que será criado. Para obter mais informações, consulte [definir o controle a ser criado quando arrastado da janela fontes de dados](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).  
  
## <a name="tasks-involved-in-binding-controls-to-data"></a>Tarefas envolvidas na associando controles a dados  
 A tabela a seguir lista algumas das tarefas mais comuns que você pode executar para associar controles a dados.  
  
|Tarefa|Mais informações|  
|----------|----------------------|  
|Abra o **fontes de dados** janela.|Abra uma superfície de design no editor e escolha **exibição** > **fontes de dados**.|  
|Adicione uma fonte de dados ao seu projeto.|[Adicionar novas fontes de dados](../data-tools/add-new-data-sources.md)|  
|Definir o controle que é criado quando você arrasta um item do **fontes de dados** janela no Designer.|[Definir o controle a ser criado quando arrastado da janela Fontes de Dados](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)|  
|Modificar a lista de controles que estão associados a itens de **fontes de dados** janela.|[Adicionar controles personalizados à janela Fontes de Dados](../data-tools/add-custom-controls-to-the-data-sources-window.md)|  
|Crie controles associados a dados.|[Associando controles do Windows Forms a dados no Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)<br /><br /> [Associar controles WPF a dados no Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)|  
|Vincule a um objeto ou coleção.|[Associar objetos no Visual Studio](../data-tools/bind-objects-in-visual-studio.md)|  
|Filtre os dados que aparece na interface do usuário.|[Filtrar e classificar dados em um Aplicativo do Windows Forms](../data-tools/filter-and-sort-data-in-a-windows-forms-application.md)|  
|Personalize legendas para controles.|[Personalizar o modo como o Visual Studio cria legendas para controles associados a dados](../data-tools/customize-how-visual-studio-creates-captions-for-data-bound-controls.md)|  
  
## <a name="see-also"></a>Consulte também  
 [Ferramentas de dados do Visual Studio para .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)   
 [Associação de dados do Windows Forms](/dotnet/framework/winforms/windows-forms-data-binding)