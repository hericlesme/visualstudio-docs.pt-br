---
title: "Criar uma janela de ferramenta com várias instâncias | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- multi
- tool windows
ms.assetid: 4a7872f1-acc9-4f43-8932-5a526b36adea
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: e13fb299d513f045c4c7c339a9c6602890079e40
ms.sourcegitcommit: e01ccb5ca4504a327d54f33589911f5d8be9c35c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2018
---
# <a name="creating-a-multi-instance-tool-window"></a>Criar uma janela de ferramentas de várias instâncias
Você pode programar uma janela de ferramenta para que várias instâncias dele podem ser abertas simultaneamente. Por padrão, janelas de ferramentas podem ter apenas uma instância abrir.  
  
 Quando você usar uma janela de ferramenta com várias instâncias, você pode mostrar várias fontes relacionados de informações ao mesmo tempo. Por exemplo, você pode colocar uma multilinha <xref:System.Windows.Forms.TextBox> controle em uma janela de ferramenta com várias instâncias para que vários trechos de código estão disponíveis simultaneamente durante uma sessão de programação. Além disso, por exemplo, você pode colocar um <xref:System.Windows.Forms.DataGrid> controle e uma lista suspensa caixa em uma janela de ferramenta com várias instâncias para que várias fontes de dados em tempo real podem ser rastreadas simultaneamente.  
  
## <a name="creating-a-basic-single-instance-tool-window"></a>Criar uma janela de ferramenta Basic (instância única)  
  
1.  Crie um projeto chamado **MultiInstanceToolWindow** usando o modelo VSIX e adicionar um modelo de item da janela de ferramenta personalizada denominado **MIToolWindow**.  
  
    > [!NOTE]
    >  Para obter mais informações sobre como criar uma extensão com uma janela da ferramenta, consulte [criando uma extensão com uma janela de ferramenta](../extensibility/creating-an-extension-with-a-tool-window.md).  
  
## <a name="making-a-tool-window-multi-instance"></a>Fazer uma instância múltipla de janela de ferramenta  
  
1.  Abra o **MIToolWindowPackage.cs** de arquivos e localizar o `ProvideToolWindow` atributo. e o `MultiInstances=true` parâmetro, conforme mostrado no exemplo a seguir:  
  
    ```csharp  
    [PackageRegistration(UseManagedResourcesOnly = true)]  
        [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)] // Info on this package for Help/About  
        [ProvideMenuResource("Menus.ctmenu", 1)]  
        [ProvideToolWindow(typeof(MultiInstanceToolWindow.MIToolWindow), MultiInstances = true)]  
        [Guid(MIToolWindowPackage.PackageGuidString)]  
        public sealed class MIToolWindowPackage : Package  
    {. . .}  
    ```  
  
2.  No arquivo MIToolWindowCommand.cs, localize o método ShowToolWindos(). Nesse método, chame o <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A> método e defina seu `create` sinalizador como `false` para que ele irá iterar instâncias existentes de janela de ferramenta até um `id` foi encontrado.  
  
3.  Para criar uma instância da janela da ferramenta, chame o <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A> método e defina seu `id` para um valor disponível e seu `create` sinalizador como `true`.  
  
     Por padrão, o valor da `id` parâmetro o <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A> método é `0`. Esse valor faz com que uma janela de ferramenta de instância única. Para mais de uma instância sejam hospedados, cada instância deve ter seu próprio exclusivo `id`.  
  
4.  Chamar o <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> método o <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> objeto que é retornado pelo <xref:Microsoft.VisualStudio.Shell.ToolWindowPane.Frame%2A> propriedade da instância de janela de ferramenta.  
  
5.  Por padrão, o `ShowToolWindow` método que é criado pelo modelo de item da janela de ferramenta cria uma janela de ferramenta de instância única. O exemplo a seguir mostra como modificar o `ShowToolWindow` método para criar várias instâncias.  
  
    ```csharp  
    private void ShowToolWindow(object sender, EventArgs e)  
    {  
        for (int i = 0; i < 10; i++)  
        {  
            ToolWindowPane window = this.package.FindToolWindow(typeof(MIToolWindow), i, false);  
            if (window == null)  
            {  
                // Create the window with the first free ID.   
                window = (ToolWindowPane)this.package.FindToolWindow(typeof(MIToolWindow), i, true);  
                if ((null == window) || (null == window.Frame))  
                {  
                    throw new NotSupportedException("Cannot create tool window");  
                }  
  
            IVsWindowFrame windowFrame = (IVsWindowFrame)window.Frame;  
            Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure(windowFrame.Show());  
            break;  
            }  
        }  
    }  
    ```