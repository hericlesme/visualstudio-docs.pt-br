---
title: 'Como: publicar um aplicativo do WPF com estilos visuais habilitados | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 73b22b02-fc75-42aa-82d3-51fdcaf8e5c8
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: multiple
ms.openlocfilehash: bab4660d0e76e467bc95c373002a9035a4ccd672
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-publish-a-wpf-application-with-visual-styles-enabled"></a>Como publicar um aplicativo WPF com estilos visuais habilitados
Estilos visuais permitem a aparência de controles comuns para mudar de acordo com o tema escolhido pelo usuário. Por padrão, estilos visuais não estão habilitados para aplicativos do Windows Presentation Foundation (WPF), portanto você deve habilitá-las manualmente. No entanto, habilitar estilos visuais para um aplicativo do WPF e, em seguida, a solução de publicação causa um erro. Este tópico descreve como resolver esse erro e o processo para publicar um aplicativo do WPF com estilos visuais habilitados. Para obter mais informações sobre estilos visuais, consulte [visão geral de estilos](http://msdn.microsoft.com/5b5d7bb6-684f-478d-bf5f-b8d18bbcff2e). Para obter mais informações sobre a mensagem de erro, consulte [de solução de problemas de erros específicos nas implantações do ClickOnce](../deployment/troubleshooting-specific-errors-in-clickonce-deployments.md).  
  
 Para resolver o erro e publicar a solução, você deve executar as seguintes tarefas:  
  
-   [Publicar a solução sem estilos visuais habilitados](#BKMK_publishsolwovs).  
  
-   [Criar um arquivo de manifesto](#BKMK_CreateManifest).  
  
-   [Inserir o arquivo de manifesto para o arquivo executável da solução publicado](#BKMK_embedmanifest).  
  
-   [Assinar os manifestos de aplicativo e implantação](#BKMK_signappdeplyman).  
  
 Em seguida, você pode mover os arquivos publicados para o local do qual você deseja que os usuários finais para instalar o aplicativo.  
  
##  <a name="BKMK_publishsolwovs"></a>Publicar a solução sem estilos visuais habilitados  
  
1.  Certifique-se de que seu projeto não possui estilos visuais habilitados. Primeiro, verifique o arquivo de manifesto do projeto para o XML a seguir. Em seguida, se o XML estiver presente, coloque o XML com uma marca de comentário.  
  
     Por padrão, os estilos visuais não estão habilitados.  
  
    ```  
    <dependency>    <dependentAssembly>      <assemblyIdentity          type="win32"          name="Microsoft.Windows.Common-Controls"          version="6.0.0.0"          processorArchitecture="*"          publicKeyToken="6595b64144ccf1df"          language="*"        />    </dependentAssembly>  </dependency>  
    ```  
  
     Os procedimentos a seguir mostram como abrir o arquivo de manifesto associado ao seu projeto.  
  
    ###### <a name="to-open-the-manifest-file-in-a-visual-basic-project"></a>Para abrir o arquivo de manifesto em um projeto do Visual Basic  
  
    1.  Na barra de menus, escolha **projeto**, *ProjectName***propriedades**, onde *ProjectName* é o nome do seu projeto.  
  
         As páginas de propriedade para o seu projeto WPF aparecem.  
  
    2.  Sobre o **aplicativo** guia, escolha **exibir configurações do Windows**.  
  
         O arquivo App. manifest abre no **Editor de código**.  
  
    ###### <a name="to-open-the-manifest-file-in-a-c-project"></a>Para abrir o arquivo de manifesto em um projeto c#  
  
    1.  Na barra de menus, escolha **projeto**, *ProjectName***propriedades**, onde *ProjectName* é o nome do seu projeto.  
  
         As páginas de propriedade para o seu projeto WPF aparecem.  
  
    2.  Sobre o **aplicativo** guia, anote o nome que aparece no campo de manifesto. Esse é o nome do manifesto que está associado ao seu projeto.  
  
        > [!NOTE]
        >  Se **Inserir manifesto com configurações padrão** ou **criar aplicativo sem um manifesto** aparecem no campo de manifesto, estilos visuais não estão habilitados. Se o nome de um arquivo de manifesto é exibido no campo de manifesto, vá para a próxima etapa deste procedimento.  
  
    3.  Em **Solution Explorer**, escolha **Mostrar todos os arquivos** ().  
  
         Esse botão mostra todos os itens de projeto, incluindo aqueles que foram excluídos e aqueles que normalmente são ocultas. O arquivo de manifesto aparece como um item de projeto.  
  
2.  Criar e publicar sua solução. Para obter mais informações sobre como publicar a solução, consulte [como: publicar um aplicativo ClickOnce usando o Assistente de publicação](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).  
  
##  <a name="BKMK_CreateManifest"></a>Criar um arquivo de manifesto  
  
1.  Cole o seguinte XML em um arquivo do bloco de notas.  
  
     Esse XML descreve o assembly que contém os controles que oferecem suporte a estilos visuais.  
  
    ```  
    <?xml version="1.0" encoding="utf-8"?><asmv1:assembly manifestVersion="1.0"                xmlns="urn:schemas-microsoft-com:asm.v1"                xmlns:asmv1="urn:schemas-microsoft-com:asm.v1"                xmlns:asmv2="urn:schemas-microsoft-com:asm.v2"                xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  <dependency>    <dependentAssembly>      <assemblyIdentity        type="win32"        name="Microsoft.Windows.Common-Controls"        version="6.0.0.0"        processorArchitecture="*"        publicKeyToken="6595b64144ccf1df"        language="*"        />    </dependentAssembly>  </dependency></asmv1:assembly>  
    ```  
  
2.  No bloco de notas, clique em **arquivo**e, em seguida, clique em **Salvar como**.  
  
3.  No **Salvar como** na caixa de **Salvar como tipo** lista suspensa, selecione **todos os arquivos**.  
  
4.  No **nome de arquivo** caixa, nomeie o arquivo e acrescentar **. manifest** ao final do nome do arquivo. Por exemplo: **themes.manifest**.  
  
5.  Escolha o **procurar pastas** botão, selecione qualquer pasta e, em seguida, clique em **salvar**.  
  
    > [!NOTE]
    >  Procedimentos restantes supõem que o nome desse arquivo é **themes.manifest** e que o arquivo é salvo no diretório C:\temp do computador.  
  
##  <a name="BKMK_embedmanifest"></a>Inserir o arquivo de manifesto para o arquivo executável da solução publicado  
  
1.  Abra o **Prompt de comando do Visual Studio**.  
  
     Para obter mais informações sobre como abrir o **Prompt de comando do Visual Studio**, consulte [Prompts de comando](/dotnet/framework/tools/developer-command-prompt-for-vs).  
  
    > [!NOTE]
    >  As etapas restantes fazem as seguintes suposições sobre sua solução:  
    >   
    >  -   O nome da solução é **MyWPFProject**.  
    > -   A solução está localizada no seguinte diretório: `%UserProfile%\Documents\Visual Studio 2010\Projects\`.  
    >   
    >      A solução é publicada no seguinte diretório: `%UserProfile%\Documents\Visual Studio 2010\Projects\publish`.  
    > -   A versão mais recente dos arquivos do aplicativo publicado está localizada no seguinte diretório:`%UserProfile%\Documents\Visual Studio 2010\Projects\publish\Application Files\WPFApp_1_0_0_0`  
    >   
    >  Você não precisa usar o nome ou os locais de diretório descritos acima. O nome e locais descritos acima são usados apenas para ilustrar as etapas necessárias para publicar sua solução.  
  
2.  No prompt de comando, altere o caminho para o diretório que contém a versão mais recente dos arquivos do aplicativo publicado. O exemplo a seguir demonstra essa etapa.  
  
    ```  
    cd "%UserProfile%\Documents\Visual Studio 2010\Projects\MyWPFProject\publish\Application Files\WPFApp_1_0_0_0"  
    ```  
  
3.  No prompt de comando, execute o seguinte comando para inserir o arquivo de manifesto para o arquivo executável do aplicativo.  
  
    ```  
    mt -manifest c:\temp\themes.manifest -outputresource:MyWPFApp.exe.deploy  
    ```  
  
##  <a name="BKMK_signappdeplyman"></a>Assinar os manifestos de aplicativo e implantação  
  
1.  No prompt de comando, execute o seguinte comando para remover o `.deploy` extensão do arquivo executável na pasta atual.  
  
    ```  
    ren MyWPFApp.exe.deploy MyWPFApp.exe  
    ```  
  
    > [!NOTE]
    >  Este exemplo presume que apenas um arquivo tem o `.deploy` extensão de arquivo. Certifique-se de que você renomeie todos os arquivos neste diretório com o `.deploy` extensão de arquivo.  
  
2.  No prompt de comando, execute o seguinte comando para assinar o manifesto de aplicativo.  
  
    ```  
    mage -u MyWPFApp.exe.manifest -cf ..\..\..\MyWPFApp_TemporaryKey.pfx  
    ```  
  
    > [!NOTE]
    >  Este exemplo supõe que você assina o manifesto usando o `.pfx` arquivo do projeto. Se você não estiver se registrando o manifesto, você pode omitir o `-cf` parâmetro que é usado neste exemplo. Se você estiver se registrando o manifesto com um certificado que requer uma senha, especifique o `-password` opção (`For example: mage -u MyWPFApp.exe.manifest -cf ..\..\..\MyWPFApp_TemporaryKey.pfx - password Password`).  
  
3.  No prompt de comando, execute o seguinte comando para adicionar o `.deploy` extensão para o nome do arquivo que você renomeou na etapa anterior deste procedimento.  
  
    ```  
    ren MyWPFApp.exe MyWPFApp.exe.deploy  
    ```  
  
    > [!NOTE]
    >  Este exemplo presume que apenas um arquivo tinha um `.deploy` extensão de arquivo. Certifique-se de que você renomeie todos os arquivos neste diretório que anteriormente tinha o `.deploy` extensão de nome de arquivo.  
  
4.  No prompt de comando, execute o seguinte comando para assinar o manifesto de implantação.  
  
    ```  
    mage -u ..\..\MyWPFApp.application -appm MyWPFApp.exe.manifest -cf ..\..\..\MyWPFApp_TemporaryKey.pfx  
    ```  
  
    > [!NOTE]
    >  Este exemplo supõe que você assina o manifesto usando o `.pfx` arquivo do projeto. Se você não estiver se registrando o manifesto, você pode omitir o `-cf` parâmetro que é usado neste exemplo. Se você estiver se registrando o manifesto com um certificado que requer uma senha, especifique o `-password` opção, como neste exemplo:`For example: mage -u MyWPFApp.exe.manifest -cf ..\..\..\MyWPFApp_TemporaryKey.pfx - password Password`.  
  
 Depois de executar essas etapas, você pode mover os arquivos publicados para o local do qual você deseja que os usuários finais para instalar o aplicativo. Se você pretende atualizar solução geralmente, você pode mover esses comandos em um script e execute o script cada vez que você publica uma nova versão.  
  
## <a name="see-also"></a>Consulte também  
 [Solucionando problemas de erros específicos nas implantações do ClickOnce](../deployment/troubleshooting-specific-errors-in-clickonce-deployments.md)   
 [Visão geral de estilos visuais](http://msdn.microsoft.com/5b5d7bb6-684f-478d-bf5f-b8d18bbcff2e)   
 [Habilitar estilos visuais](https://msdn.microsoft.com/library/bb773175.aspx)   
 [Prompts de Comando](/dotnet/framework/tools/developer-command-prompt-for-vs)