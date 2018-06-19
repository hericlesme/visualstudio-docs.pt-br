---
title: Adicionando comandos do Visual Studio para uma página inicial | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- start page commands
- vs:VSCommands
ms.assetid: a8e2765c-cfb5-47b5-a414-6e48b434e0c2
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 87a5e6d29877efb857b846a7b3fac5f19f790d7c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31101788"
---
# <a name="adding-visual-studio-commands-to-a-start-page"></a>Adicionando comandos do Visual Studio para uma página de início
Quando você cria uma página de início personalizados, você pode adicionar comandos do Visual Studio para ele. Este documento descreve as diferentes maneiras para associar os comandos do Visual Studio para objetos XAML em uma página de início.  
  
 Para obter mais informações sobre os comandos no XAML, consulte [visão geral de comandos](/dotnet/framework/wpf/advanced/commanding-overview)  
  
## <a name="adding-commands-from-the-command-well"></a>Adicionando comandos do comando bem  
 A página inicial criada em [criando uma página de início personalizado](../extensibility/creating-a-custom-start-page.md) adicionado a <xref:Microsoft.VisualStudio.PlatformUI?displayProperty=fullName> e <xref:Microsoft.VisualStudio.Shell?displayProperty=fullName> namespaces, da seguinte maneira.  
  
```  
xmlns:vs="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"  
xmlns:vsfx="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"  
```  
  
 Adicione outro namespace para Microsoft.VisualStudio.Shell do assembly Microsoft.VisualStudio.Shell.Immutable.11.0.dll. (Talvez seja necessário adicionar uma referência a esse assembly em seu projeto.)  
  
```xml  
xmlns:vscom="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.Immutable.11.0"  
```  
  
 Você pode usar o `vscom:` alias para associar os comandos do Visual Studio para XAML controles na página, definindo o <xref:System.Windows.Controls.Primitives.ButtonBase.Command%2A> propriedade do controle para `vscom:VSCommands.ExecuteCommand`. Você pode definir o <xref:System.Windows.Controls.Primitives.ButtonBase.CommandParameter%2A> propriedade para o nome do comando a ser executado, conforme mostrado no exemplo a seguir.  
  
```xml  
<Button Name="btnNewProj" Content="New Project"   
    Command="{x:Static vscom:VSCommands.ExecuteCommand}"  
    CommandParameter="File.NewProject" >  
</Button>  
```  
  
> [!NOTE]
>  O `x:` alias que se refere ao esquema XAML, é necessário no início de todos os comandos.  
  
 Você pode definir o valor da `Command` propriedade qualquer comando que pode ser acessado a partir de **comando** janela. Para obter uma lista de comandos disponíveis, consulte [Aliases de comando do Visual Studio](../ide/reference/visual-studio-command-aliases.md).  
  
 Se o comando para adicionar requer um parâmetro adicional, você pode adicioná-lo para o valor da `CommandParameter` propriedade. Parâmetros separados de comandos usando espaços, conforme mostrado no exemplo a seguir.  
  
```xml  
<Button Content="Web Search"   
        Command="{x:Static vscom:VSCommands.ExecuteCommand}"  
        CommandParameter="View.WebBrowser www.bing.com" />  
```  
  
### <a name="calling-extensions-from-the-command-well"></a>Extensões de chamada do comando bem  
 Você pode chamar comandos de VSPackages registrados usando a mesma sintaxe que é usada para chamar outros comandos do Visual Studio. Por exemplo, se um VSPackage instalado adiciona um **Home Page** comando o **exibição** menu, você pode chamar o comando definindo `CommandParameter` para `View.HomePage`.  
  
> [!NOTE]
>  Se você chamar um comando que está associado um VSPackage, o pacote deve ser carregado quando o comando é invocado.  
  
## <a name="adding-commands-from-assemblies"></a>Adicionando comandos de Assemblies  
 Para chamar um comando de um assembly, ou para o código de acesso em um VSPackage que não está associado um comando de menu, você deve criar um alias para o assembly e, em seguida, chamar o alias.  
  
#### <a name="to-call-a-command-from-an-assembly"></a>Para chamar um comando de um assembly  
  
1.  Em sua solução, adicione uma referência ao assembly.  
  
2.  Na parte superior do arquivo StartPage.xaml, adicione uma diretiva de namespace para o assembly, conforme mostrado no exemplo a seguir.  
  
    ```xml  
    xmlns:vsc="clr-namespace:WebUserControl;assembly=WebUserControl"  
    ```  
  
3.  Invocar o comando definindo o `Command` propriedade de um objeto XAML, como mostrado no exemplo a seguir.  
  
     XAML  
  
    ```  
    <vs:Button Text="Hide me" Command="{x:Static vsc:HideControl}" .../>  
    ```  
  
> [!NOTE]
>  Você deve copiar o assembly e, em seguida, cole-o no. \\ *Pasta de instalação do visual Studio*\Common7\IDE\PrivateAssemblies\ para certificar-se de que ele está carregado antes que ele seja chamado.  
  
## <a name="adding-commands-with-the-dte-object"></a>Adicionando comandos com o objeto DTE  
 Você pode acessar o objeto DTE de uma página de início, na marcação e no código.  
  
 Na marcação, você pode acessá-lo usando o [associação de extensão de marcação](/dotnet/framework/wpf/advanced/binding-markup-extension) sintaxe para chamar o <xref:EnvDTE.DTE> objeto. Você pode usar essa abordagem para vincular a propriedades simples, como aqueles que retornam coleções, mas não é possível associar métodos ou serviços. A exemplo a seguir mostra um <xref:System.Windows.Controls.TextBlock> controle que associa ao <xref:EnvDTE._DTE.Name%2A> propriedade e um <xref:System.Windows.Controls.ListBox> controle que enumera o <xref:EnvDTE.Window.Caption%2A> propriedades da coleção que é retornado pelo <xref:EnvDTE._DTE.Windows%2A> propriedade.  
  
```xml  
<TextBlock Text="{Binding Path=DTE.Name}" FontSize="12" HorizontalAlignment="Center"/>  
<ListBox ItemsSource="{Binding Path=DTE.Windows}">  
    <ListBox.ItemTemplate>  
        <DataTemplate>  
            <TextBlock Text="{Binding Path=Caption}"/>  
        </DataTemplate>  
    </ListBox.ItemTemplate>  
</ListBox  
```  
  
 Para obter um exemplo, consulte [passo a passo: salvando as configurações de usuário em uma página de início](../extensibility/walkthrough-saving-user-settings-on-a-start-page.md).  
  
## <a name="see-also"></a>Consulte também  
 [Adicionar um controle de usuário à página inicial](../extensibility/adding-user-control-to-the-start-page.md)