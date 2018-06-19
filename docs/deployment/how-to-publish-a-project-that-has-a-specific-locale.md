---
title: 'Como: publicar um projeto que tem uma localidade específica | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- publishing, localized projects
- locales, publishing for
- deploying applications [ClickOnce], localized projects
- locales, deploying for
- publishing localized projects
- macros, deploying with
- macros, publishing with
ms.assetid: 7c4cd83a-f985-4c85-9022-fadb5dbd2b39
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5e8975c362039e347700e4256036998e8386c2e2
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/19/2018
ms.locfileid: "31561604"
---
# <a name="how-to-publish-a-project-that-has-a-specific-locale"></a>Como publicar um projeto que tem uma localidade específica
Não é incomum para um aplicativo conter componentes que possuem diversas localidades. Nesse cenário, seria criada uma solução que possui diversos projetos e publicados projetos separados para cada localização. Esse procedimento mostra como usar uma macro para publicar o primeiro projeto em uma solução usando a localização 'en'. Se desejar tentar esse procedimento com outra localidade além de 'en', certifique-se de definir `localeString` na macro para corresponder à localidade que estiver usando (por exemplo, 'de' ou 'de-DE').  
  
> [!NOTE]
>  Ao usar essa macro, o Local de Publicação deve ser uma URL válida ou um compartilhamento Universal Naming Convention (UNC). Além disso, Serviços de Informações da Internet (IIS) deve estar instalado no computador. Para instalar o IIS, o **iniciar** menu, clique em **painel de controle**. Clique duas vezes em **adicionar ou remover programas**. Em **adicionar ou remover programas**, clique em **Adicionar/remover componentes do Windows**. No **Assistente de componentes do Windows**, selecione o **serviços de informações da Internet (IIS)** caixa de seleção de **componentes** lista. Em seguida, clique em **concluir** para fechar o assistente.  
  
### <a name="to-create-the-publishing-macro"></a>Criar a macro de publicação  
  
1.  Para abrir o Gerenciador de Macro no **ferramentas** , aponte para **Macros**e, em seguida, clique em **Macro Explorer**.  
  
2.  Criar um novo módulo de macro. No Gerenciador de Macro, selecione **MyMacros**. Sobre o **ferramentas** , aponte para **Macros**e, em seguida, clique em **novo módulo de Macro**. Nomeie o módulo **PublishSpecificCulture**.  
  
3.  No Explorador de Macro, expanda o **MyMacros** nó e, em seguida, abra o **PublishAllProjects** módulo clicando duas vezes nele (ou, do **ferramentas** , aponte para **Macros**e, em seguida, clique em **Macros IDE**).  
  
4.  No Macros IDE, adicione o seguinte código ao módulo, após as instruções `Import`:  
  
    ```vb  
    Module PublishSpecificCulture  
        Sub PublishProjectFirstProjectWithEnLocale()  
            ' Note: You should publish projects by using the IDE at least once  
            ' before you use this macro. Items such as the certficate and the   
            ' security zone must be set.  
            Dim localeString As String = "en"  
  
            ' Get first project.  
            Dim proj As Project = DTE.Solution.Projects.Item(1)  
            Dim publishProperties As Object = proj.Properties.Item("Publish").Value  
  
            ' GenerateManifests and SignManifests must always be set to  
            ' True for publishing to work.   
            proj.Properties.Item("GenerateManifests").Value = True  
            proj.Properties.Item("SignManifests").Value = True  
  
            'Set the publish language.  
            'This will set the deployment language and pick up all   
            ' en resource dlls:  
            Dim originalTargetCulture As String = _  
                publishProperties.Item("TargetCulture").Value  
            publishProperties.Item("TargetCulture").Value = localeString  
  
            'Append 'en' to end of publish, install, and update URLs if needed:  
            Dim originalPublishUrl As String = _  
                publishProperties.Item("PublishUrl").Value  
            Dim originalInstallUrl As String = _  
                publishProperties.Item("InstallUrl").Value  
            Dim originalUpdateUrl As String = _  
                publishProperties.Item("UpdateUrl").Value  
            publishProperties.Item("PublishUrl").Value = _  
                AppendStringToUrl(localeString, New Uri(originalPublishUrl))  
            If originalInstallUrl <> String.Empty Then  
                publishProperties.Item("InstallUrl").Value = _  
                    AppendStringToUrl(localeString, New Uri(originalInstallUrl))  
            End If  
            If originalUpdateUrl <> String.Empty Then  
                publishProperties.Item("UpdateUrl").Value = _  
                    AppendStringToUrl(localeString, New Uri(originalUpdateUrl))  
            End If  
            proj.Save()  
  
            Dim slnbld2 As SolutionBuild2 = _  
                CType(DTE.Solution.SolutionBuild, SolutionBuild2)  
            slnbld2.Clean(True)  
  
            slnbld2.BuildProject( _  
            proj.ConfigurationManager.ActiveConfiguration.ConfigurationName, _  
            proj.UniqueName, True)  
  
            ' Only publish if build is successful.  
            If slnbld2.LastBuildInfo <> 0 Then  
                MsgBox("Build failed for " & proj.UniqueName)  
            Else  
                slnbld2.PublishProject( _  
                proj.ConfigurationManager.ActiveConfiguration.ConfigurationName, _  
                proj.UniqueName, True)  
                If slnbld2.LastPublishInfo = 0 Then  
                    MsgBox("Publish succeeded for " & proj.UniqueName _  
                    & vbCrLf & "." _  
                    & " Publish Language was '" & localeString & "'.")  
                Else  
                    MsgBox("Publish failed for " & proj.UniqueName)  
                End If  
            End If  
  
            ' Return URLs and target culture to their previous state.  
            publishProperties.Item("PublishUrl").Value = originalPublishUrl  
            publishProperties.Item("InstallUrl").Value = originalInstallUrl  
            publishProperties.Item("UpdateUrl").Value = originalUpdateUrl  
            publishProperties.Item("TargetCulture").Value = originalTargetCulture  
            proj.Save()  
        End Sub  
  
        Private Function AppendStringToUrl(ByVal str As String, _  
        ByVal baseUri As Uri) As String  
            Dim returnValue As String = baseUri.OriginalString  
            If baseUri.IsFile OrElse baseUri.IsUnc Then  
                returnValue = IO.Path.Combine(baseUri.OriginalString, str)  
            Else  
                If Not baseUri.ToString.EndsWith("/") Then  
                    returnValue = baseUri.OriginalString & "/" & str  
                Else  
                    returnValue = baseUri.OriginalString & str  
                End If  
            End If  
            Return returnValue  
        End Function  
    End Module  
    ```  
  
5.  Feche o Macros IDE. O foco retornará ao Visual Studio.  
  
### <a name="to-publish-a-project-for-a-specific-locale"></a>Publicar um projeto para uma localização específica  
  
1.  Para criar um projeto de aplicativo do Windows Visual Basic, sobre o **arquivo** , aponte para **novo**e, em seguida, clique em **projeto**.  
  
2.  No **novo projeto** caixa de diálogo, selecione **aplicativo do Windows** do **Visual Basic** nó. Nomeie o projeto **PublishLocales**.  
  
3.  Clique em Form1. No **propriedades** janela, em **Design**, alterar o **idioma** propriedade **(padrão)** para **inglês**. Alterar o **texto** propriedade a fim de **MyForm**.  
  
     Observe que as DLLs do recurso localizado não são criadas até serem necessárias. Por exemplo, são criadas ao alterar o texto do formulário ou um de seus controles após especificar a nova localização.  
  
4.  Publicar PublishLocales usando o Visual Studio IDE.  
  
     Em **Solution Explorer**, selecione PublishLocales. Sobre o **projeto** menu, selecione **propriedades**. No Designer de projeto, sobre o **publicar** página, especifique um local de publicação de **http://localhost/PublishLocales**e, em seguida, clique em **publicar agora**.  
  
     Quando a página Web publicar for exibida, feche-a. (Para esta etapa, é necessário apenas publicar o projeto; não é necessário instalar.)  
  
5.  Publique PublishLocales novamente invocando a macro na janela do Prompt de Comando do Visual Studio. Para exibir a janela de Prompt de comando, no **exibição** , aponte para **outras janelas** e, em seguida, clique em **janela de comando**, ou pressione CTRL + ALT + A. Na janela do Prompt de comando, digite `macros`; o preenchimento automático fornecerá uma lista de macros disponíveis. Selecione a seguinte macro e pressione ENTER:  
  
     `Macros.MyMacros.PublishSpecificCulture.PublishProjectFirstProjectWithEnLocale`  
  
6.  Quando o processo de publicação for bem-sucedido, gerará uma mensagem que diz "Publicação bem-sucedida para PublishLocales\PublishLocales.vbproj. O idioma de publicação foi 'en'." Clique em **Okey** na caixa de mensagem. Quando a página da Web de publicação for exibida, clique em **instalar**.  
  
7.  Procure em C:\Inetpub\wwwroot\PublishLocales\en. Deverá ser possível visualizar os arquivos instalados como os manifestos, setup.exe e o arquivo da página Web publicar, além da DLL do recurso localizado. (Por padrão, ClickOnce anexa uma extensão .deploy em EXEs e DLLs; é possível remover essa extensão após a implantação.)  
  
## <a name="see-also"></a>Consulte também  
 [Publicando aplicativos ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Ambiente de desenvolvimento de macros](http://msdn.microsoft.com/en-us/d23105d8-34fe-4ad9-8278-fae2c660aeac)   
 [Janela do Gerenciador de macro](http://msdn.microsoft.com/en-us/762169e6-f83f-44b4-bffa-d0f107cae9a3)   
 [Como: editar e criar programaticamente Macros](http://msdn.microsoft.com/en-us/6716f820-1feb-48ad-a718-27eb6b473c5a)