---
title: "Regiões de formulário de diretrizes para criação de Outlook | Microsoft Docs"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- form regions [Office development in Visual Studio], guidelines
- icons [Office development in Visual Studio]
ms.assetid: 47ad59d3-5cb7-4d27-a314-9c09937143d7
caps.latest.revision: "29"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 197da04c42b97f274979e46a2ba4691747365362
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="guidelines-for-creating-outlook-form-regions"></a>Diretrizes para criar regiões de formulário do Outlook
  As informações a seguir podem ajudá-lo a otimizar as regiões de formulário e evitar possíveis problemas:  
  
-   [Usando nomes de região de formulário](#UsingFormRegions).  
  
-   [Desabilitando a herança de região de formulário](#DisablingInheritance).  
  
-   [Noções básicas sobre tipos e mensagem de nomes de classe](#ClassNames).  
  
-   [Criando regiões de formulário adjacentes para o painel de leitura](#ReadingPane).  
  
-   [Usando tamanhos de ícones ideal](#UsingOptimal).  
  
 Para obter mais informações sobre regiões de formulário, consulte [criar regiões de formulário do Outlook](../vsto/creating-outlook-form-regions.md).  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
##  <a name="UsingFormRegions"></a>Usando nomes de região de formulário  
 Há vários nomes usados para descrever a região do formulário. É importante compreender a diferença entre esses nomes e como eles afetam a região do formulário. A tabela a seguir descreve cada nome.  
  
|Nome da região de formulário|Descrição|  
|----------------------|-----------------|  
|Nome do item de região de formulário|O nome que você especificar para o **região de formulário do Outlook** item o **Adicionar Novo Item** caixa de diálogo. Este é o nome do arquivo de código de região de formulário que aparece no **Gerenciador de soluções**.|  
|Propriedade <xref:Microsoft.Office.Tools.Outlook.FormRegionManifest.FormRegionName%2A>|Especificar esse nome no **fornecer um texto descritivo e selecione suas preferências de exibição** página do **nova região de formulário do Outlook** assistente. Esse nome é exibido como o **FormRegionName** propriedade o **propriedades** janela.<br /><br /> Use o <xref:Microsoft.Office.Tools.Outlook.FormRegionManifest.FormRegionName%2A> propriedade para especificar o rótulo que identifica a região do formulário na interface de usuário (UI) do Outlook. Para regiões de formulário separado, esse nome é exibido como um botão na faixa de opções do item do Outlook.<br /><br /> Para regiões de formulário adjacentes, esse nome é exibido como texto de cabeçalho acima a região do formulário.|  
|Atributo Microsoft.Office.Tools.Outlook.FormRegionName|Quando você adiciona um **região de formulário do Outlook** item ao projeto, o Visual Studio define essa propriedade como o nome totalmente qualificado da região de formulário. O nome totalmente qualificado do padrão é o nome do suplemento do VSTO conectado com o nome da região do formulário por um ponto — por exemplo, `OutlookAddIn1.FormRegion1`.<br /><br /> Esse nome totalmente qualificado também aparece como um atributo na parte superior da classe de fábrica de região de formulário.<br /><br /> Use o atributo Microsoft.Office.Tools.Outlook.FormRegionName para identificar exclusivamente a região de formulário em todos os Outlook suplementos do VSTO. Você não pode alterar o valor do atributo Microsoft.Office.Tools.Outlook.FormRegionName a renomeação do item de região de formulário ou alterando o <xref:Microsoft.Office.Tools.Outlook.FormRegionManifest.FormRegionName%2A> propriedade. Para alterar esse nome, você deve modificar o atributo Microsoft.Office.Tools.Outlook.FormRegionName no arquivo de código de região de formulário.|  
  
##  <a name="DisablingInheritance"></a>Desabilitando a herança de região de formulário  
 Por padrão, uma classe de mensagem personalizada herda todas as associações de região de formulário da classe de base de mensagem. Por exemplo, uma classe de mensagem denominado `IPM.Task.Contoso` deriva IPM. Tarefa. Portanto, `IPM.Task.Contoso` herda as associações de região de formulário de IPM. Tarefa.  
  
 Se você não quiser que a região de formulário a ser associado a todas as classes derivadas de mensagem, defina o <xref:Microsoft.Office.Tools.Outlook.FormRegionManifest.ExactMessageClass%2A> propriedade da região de formulário para **true**. Por exemplo, se você associar uma região de formulário adjacente IPM. Tarefas e defina o <xref:Microsoft.Office.Tools.Outlook.FormRegionManifest.ExactMessageClass%2A> propriedade **true**, a região de formulário só será acrescentada à parte inferior de um formulário de tarefa padrão. A região de formulário não será anexada à parte inferior de todas as versões personalizadas de um formulário de tarefa padrão.  
  
##  <a name="ClassNames"></a>Noções básicas sobre tipos e nomes de classe de mensagem  
 O nome do tipo de um item do Outlook é diferente do nome da classe de mensagem de um item do Outlook. Por exemplo, o nome do tipo de um item RSS é Microsoft.Office.Interop.Outlook.PostItem. O nome da classe de mensagem de um item RSS é IPM. Post.RSS.  
  
 Use o nome de tipo para fazer referência a um item do Outlook no código. Para obter uma lista de nomes de tipo, consulte [associando uma região de formulário uma classe de mensagem do Outlook](../vsto/associating-a-form-region-with-an-outlook-message-class.md).  
  
 Use o nome de classe de mensagem de itens do Outlook no **nova região de formulário do Outlook** Assistente associar o item com a região do formulário. Para obter uma lista de nomes de classe de mensagem válida, consulte [associando uma região de formulário uma classe de mensagem do Outlook](../vsto/associating-a-form-region-with-an-outlook-message-class.md).  
  
##  <a name="ReadingPane"></a>Criando regiões de formulário adjacentes para o painel de leitura  
 Você pode usar o painel de leitura do Outlook para visualizar um item do Outlook sem abrir o item. O painel de leitura destina-se somente para leitura. Portanto, os controles de entrada que você adicionar a uma região de formulário adjacente, como uma caixa de texto, podem não funcionar conforme o esperado quando a região de formulário e de item são abertos no painel de leitura.  
  
 Por exemplo, se um item que tem uma região de formulário adjacente estiver aberto no painel de leitura, é possível que a seguinte situação:  
  
1.  Selecione o texto em uma caixa de texto que está na região de formulário.  
  
2.  Pressione DELETE.  
  
3.  O item de email inteira é excluído em vez de texto na caixa de texto.  
  
 Se você estiver criando uma região de formulário adjacente que contém os controles de entrada, teste os controles no painel de leitura para garantir que funcionem corretamente. Considere adicionar código personalizado que desabilita os controles que não se comportar conforme o esperado.  
  
 Como alternativa, você pode definir o <xref:Microsoft.Office.Tools.Outlook.FormRegionManifest.ShowInspectorRead%2A> propriedade da região de formulário para **False**. Dessa forma, que a região de formulário não pode ser usada no painel de leitura.  
  
##  <a name="UsingOptimal"></a>Usando tamanhos de ícones ideal  
 Você pode especificar quais ícones que você deseja a região de formulário para exibir, definindo propriedades do ícone no **ícones** grupo de propriedades do **propriedades** janela. Use as diretrizes a seguir para obter a melhor qualidade visual:  
  
-   Para o **página** ícone, use um arquivo de elementos gráficos PNG (Portable Network).  
  
-   **Janela** ícones devem ter 32 pixels por 32 pixels.  
  
-   Todos os outros ícones devem ter 16 pixels por 16 pixels.  
  
 O **página** ícone é exibido na faixa de opções de um Inspetor de itens com separado, substituição ou regiões de formulário de substituir tudo.  
  
 O **janela** ícone é exibido na área de notificação e na caixa de diálogo ALT + TAB para abrir itens que exibem a substituição ou regiões de formulário de substituir tudo.  
  
## <a name="see-also"></a>Consulte também  
 [Acessando uma região de formulário em tempo de execução](../vsto/accessing-a-form-region-at-run-time.md)   
 [Criando regiões de formulário do Outlook](../vsto/creating-outlook-form-regions.md)   
 [Passo a passo: Criando uma região de formulário do Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md)   
 [Como: adicionar uma região de formulário a um projeto de suplemento do Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)   
 [Associando uma região do formulário a uma classe de mensagem do Outlook](../vsto/associating-a-form-region-with-an-outlook-message-class.md)  
  
  