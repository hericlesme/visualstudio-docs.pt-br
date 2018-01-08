---
title: "Como: criar uma extensão de projeto do SharePoint | Microsoft Docs"
ms.custom: 
ms.date: 04/28/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- projects [SharePoint development in Visual Studio], extending
- SharePoint development in Visual Studio, extending projects
- SharePoint projects, extending
ms.assetid: ceecb9cb-4a5d-44c9-992f-9624737ac996
caps.latest.revision: "29"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: e673d084b2327c345febca57c608174c83816796
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-sharepoint-project-extension"></a>Como criar uma extensão do projeto do SharePoint
  Crie uma extensão de projeto quando você deseja adicionar funcionalidade a qualquer projeto do SharePoint que está aberto no Visual Studio. Para obter mais informações, consulte [estendendo o sistema de projeto do SharePoint](../sharepoint/extending-the-sharepoint-project-system.md).  

### <a name="to-create-a-project-extension"></a>Para criar um projeto de extensão  

1.  Crie um projeto de biblioteca de classes.  

2.  Adicione referências aos assemblies a seguir:  

    -   Microsoft.VisualStudio.SharePoint  

    -   System.ComponentModel.Composition  

3.  Crie uma nova classe que implemente a interface <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension>.  

4.  Adicionar o <xref:System.ComponentModel.Composition.ExportAttribute> à classe. Este atributo permite que o Visual Studio para descobrir e carregar sua <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> implementação. Passar o <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> tipo para o construtor de atributo.  

5.  Na implementação do <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension.Initialize%2A> método, use os membros do *projectService* parâmetro para definir o comportamento de sua extensão. Esse parâmetro é um <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> objeto que fornece acesso para os eventos definidos no <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents> interface.  

## <a name="example"></a>Exemplo  
 O exemplo de código a seguir demonstra como criar uma extensão de projeto simples que manipula a maioria dos eventos de projeto do SharePoint que são definidos pelo <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents> interface. Para testar o código, crie um projeto do SharePoint no [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] e, em seguida, adicionar mais projetos à solução, alterar valores de propriedade do projeto, ou excluir ou excluir um projeto. A extensão de notificações de eventos escrevendo mensagens para o **saída** janela e **lista de erros** janela.  

  ```vb  
    Imports Microsoft.VisualStudio.SharePoint
    Imports System.ComponentModel
    Imports System.ComponentModel.Composition

    Namespace Contoso.ExampleProjectExtension
      <Export(GetType(ISharePointProjectExtension))> _
      Class ExampleProjectExtension
        Implements ISharePointProjectExtension

        Private WithEvents projectService As ISharePointProjectService

        Public Sub Initialize(ByVal projectService As ISharePointProjectService) _
            Implements ISharePointProjectExtension.Initialize
            Me.projectService = projectService
        End Sub

        ' A project was added.
        Private Sub projectService_ProjectAdded(ByVal sender As Object, ByVal e As SharePointProjectEventArgs) _
            Handles projectService.ProjectAdded
            Dim project As ISharePointProject = CType(sender, ISharePointProject)
            Dim message As String = String.Format("The following project was added: {0}", e.Project.Name)
            project.ProjectService.Logger.WriteLine(message, LogCategory.Message)
        End Sub

        ' A project was loaded in the IDE.
        Private Sub projectService_ProjectInitialized(ByVal sender As Object, ByVal e As SharePointProjectEventArgs) _
            Handles projectService.ProjectInitialized
            Dim project As ISharePointProject = CType(sender, ISharePointProject)
            Dim message As String = String.Format("The following project is being initialized: {0}", e.Project.Name)
            project.ProjectService.Logger.WriteLine(message, LogCategory.Message)
        End Sub

        ' The name of a property was changed.
        Private Sub projectService_ProjectNameChanged(ByVal sender As Object, ByVal e As NameChangedEventArgs) _
            Handles projectService.ProjectNameChanged
            Dim project As ISharePointProject = CType(sender, ISharePointProject)
            Dim message As String = String.Format("The project named {0} was changed to {1}.", e.OldName, project.Name)
            project.ProjectService.Logger.WriteLine(message, LogCategory.Message)
        End Sub

        ' A project property value was changed.
        Private Sub ProjectPropertyChanged(ByVal sender As Object, ByVal e As PropertyChangedEventArgs) _
            Handles projectService.ProjectPropertyChanged
            Dim project As ISharePointProject = CType(sender, ISharePointProject)
            Dim message As String = String.Format("The following property of the {0} project was changed: {1}",
                project.Name, e.PropertyName)
            project.ProjectService.Logger.WriteLine(message, LogCategory.Message)
        End Sub

        ' A project is being removed or unloaded.
        Private Sub projectService_ProjectRemoved(ByVal sender As Object, ByVal e As SharePointProjectEventArgs) _
            Handles projectService.ProjectRemoved
            Dim project As ISharePointProject = CType(sender, ISharePointProject)
            Dim message As String = String.Format("The following project is being removed or unloaded: {0}", e.Project.Name)
            project.ProjectService.Logger.WriteLine(message, LogCategory.Message)
        End Sub

        ' A project was removed or unloaded.
        Private Sub projectService_ProjectDisposing(ByVal sender As Object, ByVal e As SharePointProjectEventArgs) _
            Handles projectService.ProjectDisposing
            Dim project As ISharePointProject = CType(sender, ISharePointProject)
            Dim message As String = String.Format("The following project was removed or unloaded: {0}", e.Project.Name)
            project.ProjectService.Logger.WriteLine(message, LogCategory.Message)
        End Sub
      End Class
    End Namespace  
    ```  

    ```csharp  
    using Microsoft.VisualStudio.SharePoint;
    using System;
    using System.ComponentModel;
    using System.ComponentModel.Composition;

    namespace Contoso.ExampleProjectExtension
    {
      [Export(typeof(ISharePointProjectExtension))]
      internal class ExampleProjectExtension : ISharePointProjectExtension
      {
        public void Initialize(ISharePointProjectService projectService)
        {
            projectService.ProjectAdded += projectService_ProjectAdded;
            projectService.ProjectInitialized += projectService_ProjectInitialized;
            projectService.ProjectNameChanged += projectService_ProjectNameChanged;
            projectService.ProjectPropertyChanged += projectService_ProjectPropertyChanged;
            projectService.ProjectRemoved += projectService_ProjectRemoved;
            projectService.ProjectDisposing += projectService_ProjectDisposing;
        }

        // A project was added.
        void projectService_ProjectAdded(object sender, SharePointProjectEventArgs e)
        {
            ISharePointProject project = (ISharePointProject)sender;
            string message = String.Format("The following project was added: {0}", e.Project.Name);
            project.ProjectService.Logger.WriteLine(message, LogCategory.Message);
        }

        // A project is loaded in the IDE.
        void projectService_ProjectInitialized(object sender, SharePointProjectEventArgs e)
        {
            ISharePointProject project = (ISharePointProject)sender;
            string message = String.Format("The following project is being initialized: {0}", e.Project.Name);
            project.ProjectService.Logger.WriteLine(message, LogCategory.Message);
        }

        // The name of a project was changed.
        void projectService_ProjectNameChanged(object sender, NameChangedEventArgs e)
        {
            ISharePointProject project = (ISharePointProject)sender;
            string message = String.Format("The project named {0} was changed to {1}.", e.OldName, project.Name);
            project.ProjectService.Logger.WriteLine(message, LogCategory.Message);
        }

        // A project property value was changed.
        private void projectService_ProjectPropertyChanged(object sender, PropertyChangedEventArgs e)
        {
            ISharePointProject project = (ISharePointProject)sender;
            string message = String.Format("The following property of the {0} project was changed: {1}",
                project.Name, e.PropertyName);
            project.ProjectService.Logger.WriteLine(message, LogCategory.Message);
        }

        // A project is being removed or unloaded.
        void projectService_ProjectRemoved(object sender, SharePointProjectEventArgs e)
        {
            ISharePointProject project = (ISharePointProject)sender;
            string message = String.Format("The following project is being removed or unloaded: {0}", e.Project.Name);
            project.ProjectService.Logger.WriteLine(message, LogCategory.Message);
        }

        // A project was removed or unloaded.
        void projectService_ProjectDisposing(object sender, SharePointProjectEventArgs e)
        {
            ISharePointProject project = (ISharePointProject)sender;
            string message = String.Format("The following project was removed or unloaded: {0}", e.Project.Name);
            project.ProjectService.Logger.WriteLine(message, LogCategory.Message);
        }
     }
  }  
  ```  

Este exemplo usa o serviço de projeto do SharePoint para gravar a mensagem para o **saída** janela e **lista de erros** janela. Para obter mais informações, consulte [usando o serviço de projeto do SharePoint](../sharepoint/using-the-sharepoint-project-service.md).  

 Para obter exemplos que demonstram como tratar o <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectMenuItemsRequested> e <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectPropertiesRequested> eventos, consulte [como: adicionar um Item de Menu de atalho a projetos do SharePoint](../sharepoint/how-to-add-a-shortcut-menu-item-to-sharepoint-projects.md) e [como: adicionar uma propriedade a projetos SharePoint](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md).  

## <a name="compiling-the-code"></a>Compilando o código  
 Este exemplo requer referências para os seguintes assemblies:  

-   Microsoft.VisualStudio.SharePoint  

-   System.ComponentModel.Composition  

## <a name="deploying-the-extension"></a>Implantando a extensão  
 Para implantar a extensão, criar um [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] pacote de extensão (VSIX) para o assembly e outros arquivos que você quer distribuir com a extensão. Para obter mais informações, consulte [implantação de extensões para ferramentas do SharePoint no Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  

## <a name="see-also"></a>Consulte também  
 [Estendendo o sistema de projeto do SharePoint](../sharepoint/extending-the-sharepoint-project-system.md)   
 [Como: adicionar um Item de Menu de atalho a projetos do SharePoint](../sharepoint/how-to-add-a-shortcut-menu-item-to-sharepoint-projects.md)   
 [Como: adicionar uma propriedade a projetos do SharePoint](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)   
 [Instruções passo a passo: criando uma extensão de projeto do SharePoint](../sharepoint/walkthrough-creating-a-sharepoint-project-extension.md)  
