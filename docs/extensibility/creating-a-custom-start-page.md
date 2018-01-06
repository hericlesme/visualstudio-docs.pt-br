---
title: "Página inicial de criar um personalizado | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d67e0c53-9f5a-45fb-a929-b9d2125c3c82
caps.latest.revision: "18"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: f1ce8112adffabcee835d7adf598e73d327ca3b6
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="creating-a-custom-start-page"></a>Criando uma página de início personalizado
Você pode criar uma página inicial personalizada, seguindo as etapas neste documento.  
  
## <a name="creating-a-blank-start-page"></a>Criando uma página em branco inicial  
 Primeiro, verifique uma página em branco começar criando um arquivo. XAML que tem uma estrutura de marca que reconheça o Visual Studio. Em seguida, adicione a marcação e o code-behind para produzir a aparência e a funcionalidade desejada.  
  
#### <a name="to-create-a-blank-start-page"></a>Para criar uma página de início em branco  
  
1.  Criar um novo projeto do tipo **aplicativo WPF** (**Visual C# / área de trabalho do Windows**.  
  
2.  Adicione uma referência ao `Microsoft.VisualStudio.Shell.14.0`.  
  
3.  Abra o arquivo XAML no editor de XML e alterar o nível superior \<Janela > elemento para uma \<UserControl > elemento sem remover qualquer uma das declarações de namespace.  
  
4.  Remover o `x:Class` declaração do elemento de nível superior. Isso torna o conteúdo XAML compatível com a janela de ferramenta do Visual Studio que hospeda a página inicial.  
  
5.  Adicione as seguintes declarações de namespace para o nível superior \<UserControl > elemento.  
  
    ```  
    xmlns:vs="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"  
    xmlns:vsfx="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"  
    ```  
  
     Esses namespaces permitem acessar comandos do Visual Studio, controles e as configurações de interface do usuário. Para obter mais informações, consulte [adicionando comandos do Visual Studio para uma página de início](../extensibility/adding-visual-studio-commands-to-a-start-page.md).  
  
     O exemplo a seguir mostra a marcação no arquivo. XAML para uma página de início em branco. Qualquer conteúdo personalizado deve entrar interna <xref:System.Windows.Controls.Grid> elemento.  
  
    ```vb  
    <UserControl  
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"  
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
        xmlns:MyNamespace="clr-namespace:ManualStartPage;assembly=ManualStartPage"  
        xmlns:vs="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"  
                xmlns:vsfx="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"  
        xmlns:local="clr-namespace:StartPageHost"  
        mc:Ignorable="d"  
         Height="350" Width="525">  
        <Grid>  
        <!--Add content here.-->  
        </Grid>  
    </UserControl>  
    ```  
  
6.  Adicionar controles a vazio \<UserControl > elemento para preencher a página inicial personalizada. Para obter informações sobre como adicionar a funcionalidade específica para o Visual Studio, consulte [adicionando comandos do Visual Studio para uma página de início](../extensibility/adding-visual-studio-commands-to-a-start-page.md).  
  
## <a name="testing-and-applying-the-custom-start-page"></a>Página inicial do teste e aplicando personalizado  
 Não defina a instância primária do Visual Studio para executar a página inicial personalizada até que você verificar que ele não pane no Visual Studio. Em vez disso, teste-o na instância experimental.  
  
#### <a name="to-test-a-manually-created-custom-start-page"></a>Para testar uma página de início personalizados criados manualmente  
  
1.  Copie seu arquivo XAML e quaisquer arquivos de texto de suporte ou marcação arquivos, como o **%USERPROFILE%\My Documentos\Visual Studio 2015\StartPages\\**  pasta.  
  
2.  Se sua página inicial referenciar os controles ou tipos em assemblies que não estão instalados pelo Visual Studio, copie os assemblies e, em seguida, cole-os em *pasta de instalação do Visual Studio***\Common7\IDE\ PrivateAssemblies\\**.  
  
3.  Em um prompt de comando do Visual Studio, digite **/rootsuffix devenv Exp** para abrir uma instância experimental do Visual Studio.  
  
4.  Na instância experimental, vá para o **Ferramentas / opções / ambiente / inicialização** página e selecione seu arquivo XAML do **Personalizar página inicial** lista suspensa.  
  
5.  Sobre o **exibição** menu, clique em **página inicial**.  
  
     A página de início personalizado deve ser exibida. Se você deseja alterar todos os arquivos, você deve fechar a instância experimental, faça as alterações, copie e cole os arquivos alterados e, em seguida, reabra a instância experimental para exibir as alterações.  
  
#### <a name="to-apply-the-custom-start-page-in-the-primary-instance-of-visual-studio"></a>Para aplicar personalizado página inicial na instância primária do Visual Studio  
  
-   Depois de testar sua página de início e consideramos estável, use o **Personalizar página inicial** opção o **opções** caixa de diálogo para selecioná-la como a página de início na instância primária do Visual Studio  
  
## <a name="see-also"></a>Consulte também  
 [Passo a passo: Adicionando XAML personalizado para a página inicial](../extensibility/walkthrough-adding-custom-xaml-to-the-start-page.md)   
 [Adicionar um controle de usuário para a página inicial](../extensibility/adding-user-control-to-the-start-page.md)   
 [Adicionando comandos do Visual Studio para uma página de início](../extensibility/adding-visual-studio-commands-to-a-start-page.md)   
 [Passo a passo: Salvando as configurações do usuário em uma página de início](../extensibility/walkthrough-saving-user-settings-on-a-start-page.md)   
 [Implantar páginas iniciais personalizadas](../extensibility/deploying-custom-start-pages.md)