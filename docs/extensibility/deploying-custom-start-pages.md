---
title: Implantação de páginas de início personalizado | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- package start page
- deploy start page
ms.assetid: 4a7eb360-de83-41d5-be53-3cfb160d19f9
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6110be404ec7de9b52aef23fc9d1d77d1ae7e2c3
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="deploying-custom-start-pages"></a>Implantação de páginas de início personalizado
Você pode implantar páginas de inicialização personalizada usando a implantação do VSIX ou copiar os arquivos para os locais corretos no computador de destino.  
  
## <a name="vsix-deployment-by-using-the-start-page-project-template"></a>Implantação do VSIX usando o modelo de projeto de página de início  
 Quando você cria uma página inicial usando o modelo de projeto de página inicial e, em seguida, compile o projeto, o Visual Studio cria um arquivo de .vsix que você pode distribuir. Empacotar uma página inicial em um arquivo .vsix oferece as seguintes opções para a implantação, dependendo de seu público-alvo:  
  
-   Você pode colocar o arquivo .vsix em um compartilhamento de rede ou em um site público. Quando alguém abre o arquivo, a página de início é instalada automaticamente.  
  
-   Você pode carregar o arquivo .vsix o [Galeria do Visual Studio](http://go.microsoft.com/fwlink/?LinkID=123847) Web site para que os usuários podem instalá-lo usando **Gerenciador de extensões**.  
  
 O modelo de projeto de página inicial cria uma cópia da página de início do Visual Studio padrão para que você possa modificar a cópia e preservar o original.  
  
 Você pode obter o modelo de projeto de página inicial usando **Gerenciador de extensões** ou fazendo o download no site da Web.  
  
## <a name="vsix-deployment-without-using-the-start-page-project-template"></a>Implantação do VSIX sem usar o modelo de projeto de página de início  
 Uma implantação bem-sucedida do VSIX requer uma extensão para ser instalado em pastas que são reconhecidas pelo processo de registro de VSIX e por **Gerenciador de extensões**. Como o modelo de projeto de página inicial já especifica as pastas corretas, recomendamos que você usá-lo sempre que você deseja compactar uma extensão para implantação do VSIX. No entanto, se você tiver um caso em que você não pode usar o modelo, você pode criar uma implantação do VSIX sem usá-lo.  
  
 Para criar uma implantação do VSIX sem usar o modelo de projeto de página inicial, primeiro crie um arquivo .vsix para a página de início de uma destas duas maneiras:  
  
-   Adicionando os arquivos de página inicial personalizados para um projeto vazio do VSIX. Para obter mais informações, consulte [modelo de projeto do VSIX](../extensibility/vsix-project-template.md).  
  
-   Criando manualmente um arquivo .vsix. Para criar um arquivo .vsix manualmente:  
    
    1.  Crie o arquivo extension.vsixmanifest e o arquivo. XML [Content_Types] em uma nova pasta. Para obter mais informações, consulte [Anatomia de um pacote do VSIX](/visualstudio/extensibility/anatomy-of-a-vsix-package).  
  
    2.  No Windows Explorer, clique na pasta que contém os dois arquivos XML, clique em Enviar para e, em seguida, clique em pasta compactada (zipada). Renomeie o arquivo. zip resultante para Filename.vsix, onde o nome do arquivo é o nome do arquivo redistribuível que instala o pacote.  
  
 Para o Visual Studio reconhecer uma página inicial, o `Content Element` o manifesto do VSIX deve conter um `CustomExtension Element` que tem o `Type` atributo definido como `"StartPage"`. Uma extensão da página inicial que foi instalada usando a implantação do VSIX aparece no **Personalizar página inicial** lista o **inicialização** página de opções como **[instalado extensão]** *Nome de extensão*.  
  
 Se o seu pacote de página inicial inclui assemblies, você deve adicionar o registro do caminho de associação para que fiquem disponíveis quando o Visual Studio inicia. Para fazer isso, certifique-se de que o pacote inclui um arquivo de .pkgdef que tem as seguintes informações.  
  
```  
[$RootKey$\BindingPaths\{Insert a new GUID here}]  
"$PackageFolder$"=""  
```  
  
### <a name="vsix-deployment-for-all-users"></a>Implantação do VSIX para todos os usuários  
 Por padrão, as extensões implantadas em pacotes VSIX instalam apenas para o usuário atual. Você pode fazer uma instalação de página inicial para todos os usuários do computador de destino ao criar uma implantação de todos os usuários.  
  
##### <a name="to-create-an-all-users-deployment"></a>Para criar uma implantação de todos os usuários  
  
1.  Abra o arquivo extension.vsixmanifest no modo de exibição de código.  
  
2.  No `Identifier` elemento do manifesto do vsix, adicione um `AllUsers` elemento que tem um valor de `true`.  
  
    ```  
    <AllUsers>true</AllUsers>  
    ```  
  
     Isso faz com que o instalador do vsix solicitar permissões de administrador e, em seguida, instalar os arquivos \Common7\IDE\Extensions.  
  
3.  Abra o arquivo .pkgdef.  
  
4.  Modificar o .pkgdef para definir a página de início padrão em HKLM adicionando o seguinte, onde *MyStartPage.xaml* é o nome do arquivo. XAML que contém a página inicial.  
  
     [$RootKey$ \StartPage\Default]  
  
     "Uri"="$PackageFolder$\\*MyStartPage.xaml*"  
  
     Isso informa Visual posicionado localização do mecanismo para pesquisar no novo local da página inicial.  
  
## <a name="file-copy-deployment"></a>Implantação de cópia de arquivo  
 Você não precisa criar um arquivo .vsix para implantar uma página inicial personalizada. Em vez disso, você pode copiar a marcação e arquivos de suporte diretamente para a pasta do usuário \StartPages\. O **Personalizar página inicial** lista o **inicialização** página de opções lista todos os arquivos nessa pasta, junto com o caminho. XAML — por exemplo, %USERPROFILE%\My Documentos\Visual Studio  *versão*\StartPages\\*nome de arquivo*. XAML. Se a página inicial inclui referências a assemblies privados, você deve copiá-los e colá-los na pasta \PrivateAssemblies\.  
  
 Para distribuir uma página inicial que você criou sem empacotamento-lo em um arquivo .vsix, é recomendável que você use uma estratégia de cópia do arquivo básico, por exemplo, um script em lotes ou qualquer outra tecnologia de implantação que permite que você coloque os arquivos nos diretórios necessários.  
  
#### <a name="to-manually-install-a-custom-start-page"></a>Para instalar manualmente uma página inicial personalizada  
  
1.  Copie o arquivo. XAML que contém a marcação de página inicial, junto com os arquivos de suporte que não sejam assemblies e colá-los na pasta de \StartPages\ do usuário.  
  
2.  Se a página de início requer que os assemblies, copiá-los e colá-los em... \\ *Pasta de instalação do visual Studio*\Common7\IDE\PrivateAssemblies\\.  
  
3.  No **Personalizar página inicial** lista o **inicialização** opções, selecione a nova página inicial. Para obter mais informações, consulte [Customizing the Start Page (Personalizando a página inicial)](../ide/customizing-the-start-page-for-visual-studio.md).  
  
## <a name="see-also"></a>Consulte também  
 [Personalizando a página inicial](../ide/customizing-the-start-page-for-visual-studio.md)   
 [Adicionar um controle de usuário à página inicial](../extensibility/adding-user-control-to-the-start-page.md)