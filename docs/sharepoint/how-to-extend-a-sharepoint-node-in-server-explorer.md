---
title: "Como: estender um nó SharePoint no Gerenciador de servidores | Microsoft Docs"
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
- SharePoint Connections [SharePoint development in Visual Studio], extending a node
- SharePoint development in Visual Studio, extending SharePoint Connections node in Server Explorer
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: d6fd079980897085f4e9c17a16dc57279ec586c2
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-extend-a-sharepoint-node-in-server-explorer"></a>Como estender um nó SharePoint no Gerenciador de Servidores
  Você pode estender nós sob o **conexões do SharePoint** nó **Server Explorer**. Isso é útil quando você deseja adicionar novos nós filho, itens de menu de atalho ou propriedades de um nó existente. Para obter mais informações, consulte [estendendo o nó de conexões do SharePoint no Gerenciador de servidores](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).  
  
### <a name="to-extend-a-sharepoint-node-in-server-explorer"></a>Para estender um nó SharePoint no Gerenciador de servidores  
  
1.  Crie um projeto de biblioteca de classes.  
  
2.  Adicione referências aos assemblies a seguir:  
  
    -   Microsoft.VisualStudio.SharePoint  
  
    -   Microsoft.VisualStudio.SharePoint.Explorer.Extensions  
  
    -   System.ComponentModel.Composition  
  
3.  Crie uma nova classe que implemente a interface <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension>.  
  
4.  Adicionar o <xref:System.ComponentModel.Composition.ExportAttribute> para a classe de atributo. Este atributo permite que o Visual Studio para descobrir e carregar sua <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> implementação. Passar o <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> tipo para o construtor de atributo.  
  
5.  Adicionar o <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeTypeAttribute> para a classe de atributo. Esse atributo especifica o identificador de cadeia de caracteres para o tipo de nó que você deseja estender.  
  
     Para especificar os tipos de nó interno fornecidos pelo Visual Studio, passe um dos seguintes valores de enumeração para o construtor de atributo:  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeTypes>: Use esses valores para especificar nós de conexão de site (os nós que exibem as URLs do site), site nós ou todos os outros nós pai em **Server Explorer**.  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.ExtensionNodeTypes>: Use esses valores para especificar um de nós internos que representam um componente individual em um site do SharePoint, como um nó que representa uma lista, um campo ou um tipo de conteúdo.  
  
6.  Na implementação do <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension.Initialize%2A> método, use membros o *nodeType* parâmetro para adicionar recursos para o nó. Esse parâmetro é um <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeType> objeto que fornece acesso para os eventos definidos no <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents> interface. Por exemplo, você pode manipular os eventos a seguir:  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents.NodeChildrenRequested>: Manipule esse evento para adicionar novos nós filho para o nó. Para obter mais informações, consulte [como: adicionar um nó do SharePoint personalizado para o Gerenciador de servidores](../sharepoint/how-to-add-a-custom-sharepoint-node-to-server-explorer.md).  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents.NodeMenuItemsRequested>: Manipule esse evento para adicionar um item de menu de atalho personalizado para o nó.  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents.NodePropertiesRequested>: Manipule esse evento para adicionar propriedades personalizadas para o nó. As propriedades aparecem no **propriedades** janela quando o nó é selecionado.  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir demonstra como criar dois tipos diferentes de extensões de nó:  
  
-   Uma extensão que adiciona um item de menu de contexto para nós de site do SharePoint. Quando você clicar no item de menu, ele exibe o nome do nó que foi clicado.  
  
-   Uma extensão que adiciona uma propriedade personalizada denominada **ContosoExampleProperty** para cada nó que representa um campo chamado **corpo**.  
  
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#9](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/serverexplorerextension.cs#9)]
 [!code-vb[SPExtensibility.ProjectSystemExtension.General#9](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/serverexplorerextension.vb#9)]  
  
 Essa extensão adiciona uma propriedade de cadeia de caracteres editável para nós. Você também pode criar propriedades personalizadas que exibem dados somente leitura do servidor do SharePoint. Para obter um exemplo que demonstra como fazer isso, consulte [passo a passo: estendendo o Gerenciador de servidores para exibir Web Parts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md).  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Este exemplo requer referências para os seguintes assemblies:  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   Microsoft.VisualStudio.SharePoint.Explorer.Extensions  
  
-   System.ComponentModel.Composition  
  
-   System.Windows.Forms  
  
## <a name="deploying-the-extension"></a>Implantando a extensão  
 Para implantar o **Server Explorer** extensão, criar um [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] pacote de extensão (VSIX) para o assembly e outros arquivos que você quer distribuir com a extensão. Para obter mais informações, consulte [implantação de extensões para ferramentas do SharePoint no Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## <a name="see-also"></a>Consulte também  
 [Como: adicionar um nó do SharePoint personalizado para o Gerenciador de servidores](../sharepoint/how-to-add-a-custom-sharepoint-node-to-server-explorer.md)   
 [Estendendo o nó de conexões do SharePoint no Gerenciador de servidores](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)   
 [Passo a passo: Estendendo o Gerenciador de servidores para exibir Web Parts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)   
 [Associando dados personalizados a extensões de Ferramentas do SharePoint](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)  
  
  