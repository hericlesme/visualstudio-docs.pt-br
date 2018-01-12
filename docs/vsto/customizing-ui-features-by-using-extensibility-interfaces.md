---
title: "Personalizando recursos de interface do usuário usando Interfaces de extensibilidade | Microsoft Docs"
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
- ICustomTaskPaneConsumer interface
- IRibbonExtensibility interface
- UI customizing [Office development in Visual Studio]
- user interfaces [Office development in Visual Studio], customizing
- application-level add-ins [Office development in Visual Studio], extensibility interfaces
- customizing UI features [Office development in Visual Studio]
- FormRegionStartup interface
- add-ins [Office development in Visual Studio], extensibility interfaces
- extensibility interfaces [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 404b54ea189c00b26f43a39274dfaf44ef37773a
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/10/2018
---
# <a name="customizing-ui-features-by-using-extensibility-interfaces"></a>Personalizando Funcionalidades de Interface do Usuário usando interfaces de extensibilidade
  As ferramentas de desenvolvimento do Office no Visual Studio fornecem classes e designers que lidam com muitos detalhes de implementação quando usá-los para criar regiões de formulário do Outlook, personalizações da faixa de opções e painéis de tarefas personalizados em um suplemento do VSTO. No entanto, você também pode implementar o *interface de extensibilidade* para cada recurso mesmo se você tiver requisitos especiais.  
  
 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]  
  
## <a name="overview-of-extensibility-interfaces"></a>Visão geral das Interfaces de extensibilidade  
 Microsoft Office define um conjunto de interfaces de extensibilidade COM VSTO Add-ins podem implementar para personalizar determinados recursos, como a faixa de opções. Essas interfaces fornecem controle total sobre os recursos que eles fornecem acesso ao. No entanto, a implementação dessas interfaces requer algum conhecimento de interoperabilidade COM em código gerenciado. Em alguns casos, o modelo de programação dessas interfaces também não é intuitivo para desenvolvedores que estejam acostumados com o .NET Framework.  
  
 Quando você criar um suplemento do VSTO usando os modelos de projeto do Office no Visual Studio, você não precisa implementar as interfaces de extensibilidade para personalizar recursos, como a faixa de opções. O [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] implementa essas interfaces para você. Em vez disso, você pode usar mais intuitiva classes e designers fornecidos pelo Visual Studio. No entanto, você ainda pode implementar as interfaces de extensibilidade diretamente no seu suplemento do VSTO para.  
  
 Para obter mais informações sobre as classes e designers que o Visual Studio fornece esses recursos, consulte [painéis de tarefas personalizados](../vsto/custom-task-panes.md), [Designer da faixa de opções](../vsto/ribbon-designer.md), e [criando regiões de formulário do Outlook](../vsto/creating-outlook-form-regions.md).  
  
## <a name="extensibility-interfaces-you-can-implement-in-a-vsto-add-in"></a>Interfaces de extensibilidade, que você pode implementar em um suplemento do VSTO  
 A tabela a seguir lista as interfaces de extensibilidade que você pode implementar e os aplicativos que dão suporte a eles.  
  
|Interface|Descrição|Aplicativos|  
|---------------|-----------------|------------------|  
|<xref:Microsoft.Office.Core.IRibbonExtensibility>|Implemente esta interface para personalizar a faixa de opções da interface do usuário. **Observação:** você pode adicionar uma **da faixa de opções (XML)** item a um projeto para gerar um padrão <xref:Microsoft.Office.Core.IRibbonExtensibility> implementação no seu suplemento do VSTO. Para obter mais informações, consulte [XML da faixa de opções](../vsto/ribbon-xml.md).|Excel<br /><br /> [!INCLUDE[InfoPath_15_short](../vsto/includes/infopath-15-short-md.md)]<br /><br /> InfoPath 2010<br /><br /> Outlook<br /><br /> PowerPoint<br /><br /> Projeto<br /><br /> Visio<br /><br /> Palavra|  
|<xref:Microsoft.Office.Core.ICustomTaskPaneConsumer>|Implemente esta interface para criar um painel tarefa personalizada.|Excel<br /><br /> Outlook<br /><br /> PowerPoint<br /><br /> Palavra|  
|<xref:Microsoft.Office.Interop.Outlook.FormRegionStartup>|Implemente esta interface para criar uma região de formulário do Outlook.|Outlook|  
  
 Existem várias outras interfaces de extensibilidade que são definidos pelo Microsoft Office, como <xref:Microsoft.Office.Core.IBlogExtensibility>, <xref:Microsoft.Office.Core.EncryptionProvider>, e <xref:Microsoft.Office.Core.SignatureProvider>. O Visual Studio não dá suporte para a implementação dessas interfaces em um Add-in do VSTO criado usando os modelos de projeto do Office.  
  
## <a name="using-extensibility-interfaces"></a>Usando Interfaces de extensibilidade  
 Para personalizar um recurso de interface do usuário usando uma interface de extensibilidade, implemente a interface adequada em seu projeto de suplemento do VSTO. Em seguida, substituir o <xref:Microsoft.Office.Tools.AddInBase.RequestService%2A> método para retornar uma instância da classe que implementa a interface.  
  
 Para um aplicativo de exemplo que demonstra como implementar a <xref:Microsoft.Office.Core.IRibbonExtensibility>, <xref:Microsoft.Office.Core.ICustomTaskPaneConsumer>, e <xref:Microsoft.Office.Interop.Outlook.FormRegionStartup> interfaces em um suplemento do VSTO para Outlook, consulte o exemplo de Gerenciador de interface do usuário [amostras de desenvolvimento do Office](../vsto/office-development-samples.md).  
  
### <a name="example-of-implementing-an-extensibility-interface"></a>Exemplo de implementação de uma Interface de extensibilidade  
 O exemplo de código a seguir demonstra uma implementação simples do <xref:Microsoft.Office.Core.ICustomTaskPaneConsumer> interface para criar um painel tarefa personalizada. Este exemplo define duas classes:  
  
-   O `TaskPaneHelper` classe implementa <xref:Microsoft.Office.Core.ICustomTaskPaneConsumer> para criar e exibir um painel tarefa personalizada.  
  
-   O `TaskPaneUI` classe fornece a interface do usuário do painel de tarefas. Os atributos para o `TaskPaneUI` classe tornar a classe visível para COM, que permite que os aplicativos do Microsoft Office descobrir a classe. Neste exemplo, a interface do usuário está vazio <xref:System.Windows.Forms.UserControl>, mas você pode adicionar controles ao modificar o código.  
  
    > [!NOTE]  
    >  Para expor o `TaskPaneUI` classe ao COM, você também deve definir o **registrar para interoperabilidade COM** propriedade para o projeto.  
  
 [!code-vb[Trin_SimpleExtensibilityInterface#1](../vsto/codesnippet/VisualBasic/Trin_SimpleExtensibilityInterface/ThisAddIn.vb#1)]
 [!code-csharp[Trin_SimpleExtensibilityInterface#1](../vsto/codesnippet/CSharp/Trin_SimpleExtensibilityInterface/ThisAddIn.cs#1)]  
  
 Para obter mais informações sobre como implementar <xref:Microsoft.Office.Core.ICustomTaskPaneConsumer>, consulte [criação de painéis de tarefas personalizados no sistema Office 2007](http://msdn.microsoft.com/en-us/256313db-18cc-496c-a961-381ed9ca94be) na documentação do Microsoft Office.  
  
### <a name="example-of-overriding-the-requestservice-method"></a>Exemplo de substituição do método RequestService  
 O exemplo de código a seguir demonstra como substituir o <xref:Microsoft.Office.Tools.AddInBase.RequestService%2A> método para retornar uma instância do `TaskPaneHelper` classe do exemplo de código anterior. Ele verifica o valor da *serviceGuid* parâmetro para determinar qual interface solicitada e, em seguida, retorna um objeto que implementa essa interface.  
  
 [!code-vb[Trin_SimpleExtensibilityInterface#2](../vsto/codesnippet/VisualBasic/Trin_SimpleExtensibilityInterface/ThisAddIn.vb#2)]
 [!code-csharp[Trin_SimpleExtensibilityInterface#2](../vsto/codesnippet/CSharp/Trin_SimpleExtensibilityInterface/ThisAddIn.cs#2)]  
  
## <a name="see-also"></a>Consulte também  
 [Explicações passo a passo e exemplos de desenvolvimento do office](../vsto/office-development-samples-and-walkthroughs.md)   
 [Suplementos de programação para o VSTO](../vsto/programming-vsto-add-ins.md)   
 [Desenvolvendo soluções do Office](../vsto/developing-office-solutions.md)   
 [Chamando código em suplementos do VSTO de outras soluções do Office](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md)   
 [Como: criar projetos do Office no Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Arquitetura de suplementos do VSTO](../vsto/architecture-of-vsto-add-ins.md)  
  
  