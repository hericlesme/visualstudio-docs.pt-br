---
title: 'Passo a passo: Criar um bootstrapper personalizado com um aviso de privacidade | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, prerequisites
- dependencies [.NET Framework], custom bootstrapper package
- deploying applications [Visual Studio], custom prerequisites
- Windows Installer deployment, prerequisites
- prerequisites [.NET Framework], custom bootstrapper package
ms.assetid: 2f3edd6a-84d1-4864-a1ae-6a13c5732aae
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 22feab436d701124b7e3843a0e6855d2830d570d
ms.sourcegitcommit: 1b9c1e333c2f096d35cfc77e846116f8e5054557
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2018
ms.locfileid: "34816036"
---
# <a name="walkthrough-create-a-custom-bootstrapper-with-a-privacy-prompt"></a>Passo a passo: criar um bootstrapper personalizado com um aviso de privacidade
Você pode configurar aplicativos ClickOnce para atualizar automaticamente quando assemblies com as versões de arquivo mais recentes e assembly estiverem disponíveis. Para certificar-se de que os clientes de consentimento para esse comportamento, você pode exibir um prompt de privacidade para eles. Em seguida, eles podem optar por conceder permissão ao aplicativo para atualizar automaticamente. Se o aplicativo não tem permissão para atualizar automaticamente, ela não instala.  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
## <a name="prerequisites"></a>Pré-requisitos  
 Você precisa dos seguintes componentes para concluir esta instrução passo a passo:  
  
-   Visual Studio 2010.  
  
## <a name="create-an-update-consent-dialog-box"></a>Criar uma caixa de diálogo de consentimento de atualização  
 Para exibir um aviso de privacidade, crie um aplicativo que solicita que o leitor de consentimento para atualizações automáticas para o aplicativo.  
  
#### <a name="to-create-a-consent-dialog-box"></a>Para criar uma caixa de diálogo de consentimento  
  
1.  No menu **Arquivo**, aponte para **Novo** e clique em **Projeto**.  
  
2.  No **novo projeto** caixa de diálogo, clique em **Windows**e, em seguida, clique em **WindowsFormsApplication**.  
  
3.  Para o **nome**, tipo **ConsentDialog**e, em seguida, clique em **Okey**.  
  
4.  No designer, clique no formulário.  
  
5.  No **propriedades** janela, altere o **texto** propriedade para **caixa de diálogo de consentimento atualização**.  
  
6.  No **caixa de ferramentas**, expanda **todos os Windows Forms**e arraste um **rótulo** controle no formulário.  
  
7.  No designer, clique no controle de rótulo.  
  
8.  No **propriedades** janela, altere o **texto** propriedade em **aparência** para o seguinte:  
  
     Verifica se o aplicativo que você está prestes a instalar as atualizações mais recentes na Web. Ao clicar em "Aceito", você autorizar o aplicativo para verificar e instalar atualizações automaticamente da Internet.  
  
9. No **caixa de ferramentas**, arraste um **caixa de seleção** controle no meio do formulário.  
  
10. No **propriedades** janela, altere o **texto** propriedade em **Layout** para **concordo**.  
  
11. No **caixa de ferramentas**, arraste um **botão** controle para o canto inferior esquerdo do formulário.  
  
12. No **propriedades** janela, altere o **texto** propriedade em **Layout** para **continuar**.  
  
13. No **propriedades** janela, altere o **(nome)** propriedade em **Design** para **ProceedButton**.  
  
14. No **caixa de ferramentas**, arraste um **botão** controle para a parte inferior direita do formulário.  
  
15. No **propriedades** janela, altere o **texto** propriedade em **Layout** para **Cancelar**.  
  
16. No **propriedades** janela, altere o **(nome)** propriedade em **Design** para **CancelButton**.  
  
17. No designer, clique duas vezes o **concordo** caixa de seleção para gerar o manipulador de eventos CheckedChanged.  
  
18. No arquivo de código Form1, adicione o seguinte código para o manipulador de eventos CheckedChanged.  
  
     [!code-csharp[ConsentDialog#1](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_1.cs)]
     [!code-vb[ConsentDialog#1](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_1.vb)]  
  
19. Atualizar o construtor da classe para desabilitar o **continuar** botão por padrão.  
  
     [!code-csharp[ConsentDialog#6](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_2.cs)]
     [!code-vb[ConsentDialog#6](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_2.vb)]  
  
20. No arquivo de código Form1, adicione o seguinte código para uma variável booleana controlar se o usuário final consentiu atualizações online.  
  
     [!code-csharp[ConsentDialog#3](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_3.cs)]
     [!code-vb[ConsentDialog#3](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_3.vb)]  
  
21. No designer, clique duas vezes o **continuar** botão para gerar o manipulador de eventos.  
  
22. No arquivo de código Form1, adicione o seguinte código para o manipulador de eventos para o **continuar** botão.  
  
     [!code-csharp[ConsentDialog#2](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_4.cs)]
     [!code-vb[ConsentDialog#2](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_4.vb)]  
  
23. No designer, clique duas vezes o **Cancelar** botão para gerar o manipulador de eventos.  
  
24. No arquivo de código Form1, adicione o seguinte código para o manipulador de eventos para o **Cancelar** botão.  
  
     [!code-csharp[ConsentDialog#4](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_5.cs)]
     [!code-vb[ConsentDialog#4](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_5.vb)]  
  
25. Atualize o aplicativo retornar um erro se o usuário final não concordar em atualizações online.  
  
     Visual Basic somente para desenvolvedores:  
  
    1.  Em **Solution Explorer**, clique em **ConsentDialog**.  
  
    2.  Sobre o **projeto** menu, clique em **Adicionar módulo**e, em seguida, clique em **adicionar**.  
  
    3.  No arquivo de código Module1. vb, adicione o código a seguir.  
  
         [!code-vb[ConsentDialog#7](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_6.vb)]  
  
    4.  Sobre o **projeto** menu, clique em **ConsentDialog propriedades**e, em seguida, clique no **aplicativo** guia.  
  
    5.  Desmarque **habilitar estrutura de aplicativo**.  
  
    6.  No **objeto de inicialização** menu suspenso, selecione **Module1**.  
  
        > [!NOTE]
        >  Desabilitar a estrutura de aplicativo desabilita recursos como estilos visuais XP do Windows, eventos de aplicativo, tela inicial, o aplicativo de instância única e muito mais. Para obter mais informações, consulte [Página de aplicativo, Designer de Projeto (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md).  
  
     Visual c# somente para desenvolvedores:  
  
     Abra o arquivo de código Program.cs e adicione o código a seguir.  
  
     [!code-csharp[ConsentDialog#5](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_7.cs)]  
  
26. Sobre o **criar** menu, clique em **BuildSolution**.  
  
## <a name="create-the-custom-bootstrapper-package"></a>Criar o pacote de inicializador personalizado  
 Para mostrar o prompt de privacidade para os usuários finais, você pode criar um pacote de bootstrapper personalizado para o aplicativo de diálogo de consentimento de atualização e incluí-lo como um pré-requisito em todos os aplicativos ClickOnce.  
  
 Esse procedimento demonstra como criar um pacote de bootstrapper personalizado ao criar os seguintes documentos:  
  
-   Um Product manifesto do arquivo para descrever o conteúdo de bootstrapper.  
  
-   Um arquivo de manifesto package.xml para listar os aspectos específicos de localização de seu pacote, como cadeias de caracteres e os termos de licença de software.  
  
-   Um documento para os termos de licença de software.  
  
#### <a name="step-1-to-create-the-bootstrapper-directory"></a>Etapa 1: Criar o diretório de bootstrapper  
  
1.  Crie um diretório chamado **UpdateConsentDialog** em %PROGRAMFILES%\Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages.  
  
    > [!NOTE]
    >  Talvez seja necessário privilégios administrativos para criar essa pasta.  
  
2.  No diretório UpdateConsentDialog, crie um subdiretório chamado en.  
  
    > [!NOTE]
    >  Crie um novo diretório para cada localidade. Por exemplo, você pode adicionar subpastas para os francês e de localidades. Esses diretórios conteria o alemão e francês cadeias de caracteres e os pacotes de idiomas, se necessário.  
  
#### <a name="step-2-to-create-the-productxml-manifest-file"></a>Etapa 2: Criar o arquivo de manifesto Product  
  
1.  Crie um arquivo de texto chamado `product.xml`.  
  
2.  No arquivo Product, adicione o seguinte código XML. Certifique-se de que você não substituir o código XML existente.  
  
    ```xml  
    <Product  
      xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"  
      ProductCode="Microsoft.Sample.EULA">  
      <!-- Defines the list of files to be copied on build. -->  
      <PackageFiles CopyAllPackageFiles="false">  
        <PackageFile Name="ConsentDialog.exe"/>  
      </PackageFiles>  
  
      <!-- Defines how to run the Setup package.-->  
      <Commands >  
        <Command PackageFile = "ConsentDialog.exe" Arguments=''>  
          <ExitCodes>  
            <ExitCode Value="0" Result="Success" />  
            <ExitCode Value="-1" Result="Fail" String="AU_Unaccepted" />  
            <DefaultExitCode Result="Fail"   
              FormatMessageFromSystem="true" String="GeneralFailure" />  
          </ExitCodes>  
        </Command>  
      </Commands>  
  
    </Product>  
    ```  
  
3.  Salve o arquivo para o diretório de bootstrapper UpdateConsentDialog.  
  
#### <a name="step-3-to-create-the-packagexml-manifest-file-and-the-software-license-terms"></a>Etapa 3: Criar o manifesto de package.xml de arquivo e o software de termos de licença  
  
1.  Crie um arquivo de texto chamado `package.xml`.  
  
2.  No arquivo package.xml, adicione o seguinte código XML para definir a localidade e incluem os termos de licença de software. Certifique-se de que você não substituir o código XML existente.  
  
    ```xml  
    <Package   
      xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"  
      Name="DisplayName"  
      Culture="Culture"  
      LicenseAgreement="eula.rtf">  
      <PackageFiles>  
        <PackageFile Name="eula.rtf"/>  
      </PackageFiles>  
  
      <!-- Defines a localizable string table for error messages. -->  
      <Strings>  
        <String Name="DisplayName">Update Consent Dialog</String>  
        <String Name="Culture">en</String>  
        <String Name="AU_Unaccepted">The automatic update agreement is not accepted.</String>  
        <String Name="GeneralFailure">A failure occurred attempting to launch the setup.</String>  
      </Strings>  
    </Package>  
    ```  
  
3.  Salve o arquivo para o subdiretório en no diretório UpdateConsentDialog bootstrapper.  
  
4.  Crie um documento chamado EULA para os termos de licença de software.  
  
    > [!NOTE]
    >  Os termos de licença de software devem incluir informações sobre licenciamento, garantias, responsabilidades e leis locais. Esses arquivos devem ser específicos da localidade, portanto certifique-se de que o arquivo é salvo em um formato que oferece suporte a caracteres MBCS ou UNICODE. Consulte seu departamento jurídico sobre o conteúdo dos termos de licença de software.  
  
5.  Salve o documento para o subdiretório en no diretório UpdateConsentDialog bootstrapper.  
  
6.  Se necessário, crie um novo arquivo de manifesto de package.xml e um novo documento do EULA para os termos de licença de software para cada localidade. Por exemplo, se você criou subdiretórios para localidades fr e de, criar arquivos de manifesto package.xml separado e os termos de licença de software e salvá-los para os subdiretórios fr e de.  
  
## <a name="set-the-update-consent-application-as-a-prerequisite"></a>Defina o consentimento de atualização do aplicativo como um pré-requisito  
 No Visual Studio, você pode definir o aplicativo de atualização de consentimento como um pré-requisito.  
  
#### <a name="to-set-the-update-consent-application-as-a-prerequisite"></a>Para definir o aplicativo de consentimento de atualização como um pré-requisito  
  
1.  Em **Solution Explorer**, clique no nome do aplicativo que você deseja implantar.  
  
2.  Sobre o **projeto** menu, clique em *ProjectName* **propriedades**.  
  
3.  Clique o **publicar** página e, em seguida, clique em **pré-requisitos**.  
  
4.  Selecione **atualizar a caixa de diálogo de consentimento**.  
  
    > [!NOTE]
    >  Você terá que fechar e reabrir o Visual Studio para ver o diálogo de consentimento de atualização na caixa de diálogo pré-requisitos.  
  
5.  Clique em **OK**.  
  
## <a name="create-and-test-the-setup-program"></a>Criar e testar o programa de instalação  
 Depois de definir o aplicativo de atualização de consentimento como pré-requisito, você pode gerar o instalador e bootstrapper para seu aplicativo.  
  
#### <a name="to-create-and-test-the-setup-program-by-not-clicking-i-agree"></a>Para criar e testar o programa de instalação clicando não concordo  
  
1.  Em **Solution Explorer**, clique no nome do aplicativo que você deseja implantar.  
  
2.  Sobre o **projeto** menu, clique em *ProjectName* **propriedades**.  
  
3.  Clique o **publicar** página e, em seguida, clique em **publicar agora**.  
  
4.  Se a saída de publicação não abrir automaticamente, navegue até a saída de publicação.  
  
5.  Execute o programa Setup.exe.  
  
     O programa de instalação mostra o contrato de licença de software do diálogo de consentimento de atualização.  
  
6.  Leia o contrato de licença de software e, em seguida, clique em **aceitar**.  
  
     O aplicativo de diálogo de consentimento de atualização é exibida e mostra o seguinte texto: verifica se o aplicativo que você está prestes a instalar as atualizações mais recentes na Web. Ao clicar em concordo, você autoriza o aplicativo para verificar se há atualizações automaticamente na Internet.  
  
7.  Feche o aplicativo ou clique em Cancelar.  
  
     O aplicativo exibe o erro: Ocorreu um erro durante a instalação de componentes do sistema para *ApplicationName*. A instalação não pode continuar até que todos os componentes do sistema foi instalados com êxito.  
  
8.  Clique em detalhes para exibir a seguinte mensagem de erro: componente atualizar diálogo de consentimento não foi instalado com a seguinte mensagem de erro: "o contrato de atualização automática não foi aceito". Os seguintes componentes não conseguiu instalar:-caixa de diálogo de consentimento atualização  
  
9. Clique em **Fechar**.  
  
#### <a name="to-create-and-test-the-setup-program-by-clicking-i-agree"></a>Para criar e testar o programa de instalação, clicando em concordo  
  
1.  Em **Solution Explorer**, clique no nome do aplicativo que você deseja implantar.  
  
2.  Sobre o **projeto** menu, clique em *ProjectName* **propriedades**.  
  
3.  Clique o **publicar** página e, em seguida, clique em **publicar agora**.  
  
4.  Se a saída de publicação não abrir automaticamente, navegue até a saída de publicação.  
  
5.  Execute o programa Setup.exe.  
  
     O programa de instalação mostra o contrato de licença de software do diálogo de consentimento de atualização.  
  
6.  Leia o contrato de licença de software e, em seguida, clique em **aceitar**.  
  
     O aplicativo de diálogo de consentimento de atualização é exibida e mostra o seguinte texto: verifica se o aplicativo que você está prestes a instalar as atualizações mais recentes na Web. Ao clicar em concordo, você autoriza o aplicativo para verificar se há atualizações automaticamente na Internet.  
  
7.  Clique em **concordo**e, em seguida, clique em **continuar**.  
  
     Inicia o aplicativo instalar.  
  
8.  Se for exibida a caixa de diálogo de instalação do aplicativo, clique em **instalar**.  
  
## <a name="see-also"></a>Consulte também  
 [Pré-requisitos de implantação do aplicativo](../deployment/application-deployment-prerequisites.md)   
 [Criando pacotes de Bootstrapper](../deployment/creating-bootstrapper-packages.md)   
 [Como: criar um manifesto de produto](../deployment/how-to-create-a-product-manifest.md)   
 [Como: criar um manifesto de pacote](../deployment/how-to-create-a-package-manifest.md)   
 [Referência de esquema de produto e pacote](../deployment/product-and-package-schema-reference.md)