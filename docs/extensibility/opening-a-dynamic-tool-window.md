---
title: "Abrindo uma janela de ferramenta dinâmica | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: tool windows, dynamic
ms.assetid: 21547ba7-6e81-44df-9277-265bf34f877a
caps.latest.revision: "21"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: c96250c79ea283117254a96875c3a1f03f4cb30b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="opening-a-dynamic-tool-window"></a>Abrindo uma janela de ferramenta dinâmico
Janelas de ferramenta normalmente são abertas de um comando em um menu ou uma tecla de atalho equivalente. Às vezes, no entanto, talvez seja necessário uma janela de ferramenta que abre sempre que um contexto específico de interface do usuário se aplica e fecha quando o contexto de interface do usuário já não se aplica. Janelas de ferramentas como esses são chamadas *dinâmico* ou *automaticamente visíveis*.  
  
> [!NOTE]
>  Para obter uma lista de contextos de interface de usuário predefinidos, consulte <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT>. Para o  
  
 Se desejar abrir uma janela de ferramenta dinâmico na inicialização e é possível para a criação falha, você deve implementar o <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackageDynamicToolOwnerEx> interface e testar as condições de falha no <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackageDynamicToolOwnerEx.QueryShowTool%2A> método. Ordem do shell para saber se você tem uma janela de ferramenta dinâmico deve ser aberta na inicialização, você deve adicionar o `SupportsDynamicToolOwner` valor (definida como 1) para o registro do pacote. Esse valor não é parte do padrão <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute>, portanto, você deve criar um atributo personalizado para adicioná-lo. Para obter mais informações sobre atributos personalizados, consulte [usando um atributo personalizado do registro para registrar uma extensão](../extensibility/registering-and-unregistering-vspackages.md#using-a-custom-registration-attribute-to-register-an-extension).  
  
 Use <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A> para abrir uma janela de ferramenta. A janela de ferramentas é criada, conforme necessário.  
  
> [!NOTE]
>  Uma janela de ferramenta dinâmico pode ser fechada pelo usuário. Se você quiser criar um comando de menu para que o usuário pode reabrir a janela da ferramenta, o comando de menu deve ser habilitado no mesmo contexto de interface do usuário que abre a janela de ferramenta e desabilitado caso contrário.  
  
### <a name="to-open-a-dynamic-tool-window"></a>Para abrir uma janela de ferramenta dinâmico  
  
1.  Crie um projeto do VSIX denominado **DynamicToolWindow** e adicionar um modelo de item da janela de ferramenta chamado **DynamicWindowPane.cs**. Para obter mais informações, consulte [criando uma extensão com uma janela de ferramenta](../extensibility/creating-an-extension-with-a-tool-window.md).  
  
2.  No arquivo DynamicWindowPanePackage.cs, localize a declaração de DynamicWindowPanePackage. Adicionar o <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute> T:Microsoft.VisualStudio.Shell.ProvideToolWindowVisibilityAttribute atributos e para registrar a janela da ferramenta.  
  
    ```vb  
    [[ProvideToolWindow(typeof(DynamicWindowPane)]  
    [ProvideToolWindowVisibility(typeof(DynamicWindowPane), VSConstants.UICONTEXT.SolutionExists_string)]  
    [PackageRegistration(UseManagedResourcesOnly = true)]  
    [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)] // Info on this package for Help/About  
    [ProvideMenuResource("Menus.ctmenu", 1)]  
    [ProvideToolWindow(typeof(DynamicToolWindow.DynamicWindowPane))]  
    [Guid(DynamicWindowPanePackageGuids.PackageGuidString)]  
    public sealed class DynamicWindowPanePackage : Package  
    {. . .}  
    ```  
  
     Isso registra a janela da ferramenta denominada DynamicWindowPane como uma janela transitória que não é persistida quando o Visual Studio for fechado e reaberto. DynamicWindowPane é aberto sempre que <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExists_string> se aplica e fechado caso contrário.  
  
3.  Compile o projeto e comece a depuração. A instância experimental deve aparecer. Você não verá a janela da ferramenta.  
  
4.  Abra um projeto na instância experimental. A janela da ferramenta deverá aparecer.