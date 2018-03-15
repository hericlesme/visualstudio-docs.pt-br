---
title: "Implementação do comando | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- commands, implementation
ms.assetid: c782175c-cce4-4bd0-8374-4a897ceb1b3d
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 2e56fbdb6056ba02df0cafac73dd4baab60ab3be
ms.sourcegitcommit: e01ccb5ca4504a327d54f33589911f5d8be9c35c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2018
---
# <a name="command-implementation"></a>Implementação de comando
Para implementar um comando em um VSPackage, você deve executar as seguintes tarefas:  
  
1.  No arquivo. VSCT, configure um grupo de comandos e, em seguida, adicione o comando a ele. Para obter mais informações, consulte [tabela de comando do Visual Studio (. Arquivos VSCT)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)'  
  
2.  Registre o comando com o Visual Studio.  
  
3.  Implemente o comando.  
  
 As seções a seguir explicam como registrar e implementar comandos.  
  
## <a name="registering-commands-with-visual-studio"></a>Registro de comandos com o Visual Studio  
 Se o comando é exibido em um menu, você deve adicionar o <xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute> VSPackage e usado como um valor, o nome do menu ou sua ID de recurso.  
  
```  
[ProvideMenuResource("Menus.ctmenu", 1)]  
...  
    public sealed class MyPackage : Package  
    {.. ..}  
  
```  
  
 Além disso, você deve registrar o comando com o <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService>. Você pode obter esse serviço usando o <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> método se seu VSPackage é derivado de <xref:Microsoft.VisualStudio.Shell.Package>.  
  
```  
OleMenuCommandService mcs = GetService(typeof(IMenuCommandService)) as OleMenuCommandService;  
if ( null != mcs )  
{  
    // Create the command for the menu item.  
    CommandID menuCommandID = new CommandID(guidCommandGroup, myCommandID);  
    MenuCommand menuItem = new MenuCommand(MenuItemCallback, menuCommandID );  
    mcs.AddCommand( menuItem );  
}  
  
```  
  
## <a name="implementing-commands"></a>Implementação de comandos  
 Há várias maneiras de implementar comandos. Se você quiser que um comando de menu estático, o que é um comando que aparece sempre a mesma forma e no menu de, criar o comando usando <xref:System.ComponentModel.Design.MenuCommand> conforme mostrado nos exemplos na seção anterior. Para criar um comando estático, você deve fornecer um manipulador de eventos que é responsável pela execução do comando. Como o comando está sempre visível e habilitado, você não precisa fornecer seu status para o Visual Studio. Se você quiser alterar o status de um comando dependendo de certas condições, você pode criar o comando como uma instância do <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> de classe e, em seu construtor, fornecer um manipulador de eventos para executar o comando e um manipulador de status de consulta notifique Visual Studio quando o status do comando é alterado. Você também pode implementar <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> como parte de uma classe de comando ou, você pode implementar <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> se você estiver fornecendo um comando como parte de um projeto. As duas interfaces e <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> classe todos têm métodos que notificam o Visual Studio de uma alteração no status de um comando e outros métodos que permitem a execução do comando.  
  
 Quando um comando é adicionado para o serviço de comando, ele se torna um de uma cadeia de comandos. Quando você implementa os métodos de notificação e a execução de status para o comando, tome cuidado para fornecer apenas para esse comando específico e passar todos os outros casos em outros comandos na cadeia. Se você não conseguir passar o comando (geralmente, retornando <xref:Microsoft.VisualStudio.OLE.Interop.Constants.OLECMDERR_E_NOTSUPPORTED>), o Visual Studio pode parar de funcionar corretamente.  
  
## <a name="query-status-methods"></a>Métodos de Status de consulta  
 Se você estiver implementando um o <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> método ou o <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> método, verificar se o GUID do comando definido ao qual pertence o comando e a ID do comando. Siga estas diretrizes:  
  
-   Se o GUID não é reconhecido, sua implementação de um método deve retornar <xref:Microsoft.VisualStudio.OLE.Interop.Constants.OLECMDERR_E_UNKNOWNGROUP>.  
  
-   Se sua implementação de um método reconhece o GUID, mas não implementou o comando, o método deve retornar <xref:Microsoft.VisualStudio.OLE.Interop.Constants.OLECMDERR_E_NOTSUPPORTED>.  
  
-   Se sua implementação de um método reconhece o GUID e o comando, o método deve definir o campo de sinalizadores de comando de cada comando (no `prgCmds` parâmetro) usando a seguinte <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF> sinalizadores:  
  
    -   OLECMDF_SUPPORTED - se o comando é suportado.  
  
    -   OLECMDF_INVISIBLE - se o comando não deve ser visível.  
  
    -   OLECMDF_LATCHED - se o comando é ativado e parece ter sido verificada.  
  
    -   OLECMDF_ENABLED - se o comando está ativado.  
  
    -   OLECMDF_DEFHIDEONCTXTMENU - se o comando deve ser ocultado se ele for exibido em um menu de atalho.  
  
    -   OLECMDF_NINCHED - se o comando é um controlador de menu e não está habilitado, mas sua lista do menu suspenso não está vazia e ainda está disponível. (Esse sinalizador é raramente usado.)  
  
-   Se o comando foi definido no arquivo. VSCT com o `TextChanges` sinalizador, defina os seguintes parâmetros:  
  
    -   Definir o `rgwz` elemento o `pCmdText` parâmetro para o novo texto do comando.  
  
    -   Definir o `cwActual` elemento o `pCmdText` parâmetro para o tamanho da cadeia de caracteres de comando.  
  
 Certifique-se de que o contexto atual não é uma função de automação, também, a menos que o comando destina-se especificamente para lidar com funções de automação.  
  
 Para indicar que há suporte para um comando específico, retornar <xref:Microsoft.VisualStudio.VSConstants.S_OK>. Para todos os outros comandos, retornar <xref:Microsoft.VisualStudio.OLE.Interop.Constants.OLECMDERR_E_NOTSUPPORTED>.  
  
 No exemplo a seguir, o método de consulta de status primeiro assegura que o contexto não é uma função de automação, e então localiza o GUID do conjunto de comandos correta e a ID de comando. O comando é definido para ser habilitado e suporte. Não há suporte para nenhum outro comando.  
  
```  
public int QueryStatus(ref Guid pguidCmdGroup, uint cCmds, OLECMD[] prgCmds, IntPtr pCmdText)  
{  
    if (!VsShellUtilities.IsInAutomationFunction(m_provider.ServiceProvider))  
    {  
        if (pguidCmdGroup == VSConstants.VSStd2K && cCmds > 0)  
        {  
            // make the Right command visible   
            if ((uint)prgCmds[0].cmdID == (uint)VSConstants.VSStd2KCmdID.RIGHT)  
            {  
                prgCmds[0].cmdf = (int)Microsoft.VisualStudio.OLE.Interop.Constants.MSOCMDF_ENABLED | (int)Microsoft.VisualStudio.OLE.Interop.Constants.MSOCMDF_SUPPORTED;  
                return VSConstants.S_OK;  
            }  
        }  
        return Constants.OLECMDERR_E_NOTSUPPORTED;  
    }  
}  
  
```  
  
## <a name="execution-methods"></a>Métodos de execução  
 Implementação do método execute é semelhante a implementação do método de consulta de status. Primeiro, certifique-se de que o contexto não é uma função de automação. Em seguida, testar o GUID e a ID de comando. Se o GUID ou o ID de comando não é reconhecida, retorne <xref:Microsoft.VisualStudio.OLE.Interop.Constants.OLECMDERR_E_NOTSUPPORTED>.  
  
 Para tratar o comando, execute-o e retorne <xref:Microsoft.VisualStudio.VSConstants.S_OK> se a execução for bem-sucedida. O comando é responsável pela detecção de erro e notificação; Portanto, retorne um código de erro se a execução falhará. O exemplo a seguir demonstra como o método de execução deve ser implementado.  
  
```  
public int Exec(ref Guid pguidCmdGroup, uint nCmdID, uint nCmdexecopt, IntPtr pvaIn, IntPtr pvaOut)  
{  
    if (!VsShellUtilities.IsInAutomationFunction(m_provider.ServiceProvider))  
    {  
        if (pguidCmdGroup == VSConstants.GUID_VSStandardCommandSet97)  
        {  
             if (nCmdID ==(uint) uint)VSConstants.VSStd2KCmdID.RIGHT)  
            {  
                //execute the command  
                return VSConstants.S_OK;  
            }  
        }  
    }  
    return Constants.OLECMDERR_E_NOTSUPPORTED;  
}  
  
```  
  
## <a name="see-also"></a>Consulte também  
 [Como os VSPackages adicionam elementos da interface do usuário](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)