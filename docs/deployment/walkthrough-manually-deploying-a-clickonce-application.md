---
title: 'Passo a passo: Implantando um aplicativo ClickOnce manualmente | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Mage.exe, manual ClickOnce deployments
- MageUI.exe, manual ClickOnce deployments
- deploying applications [ClickOnce], manual ClickOnce deployments
- ClickOnce deployment, manually
- ClickOnce deployment, SDK tools
- manual ClickOnce deployments
- manifests [ClickOnce]
ms.assetid: ccee6551-a1b9-4ca2-8845-9c1cf4ac2560
caps.latest.revision: "49"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload: multiple
ms.openlocfilehash: 2e0035641a8ed374892060dbaabe79d808150cc2
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-manually-deploying-a-clickonce-application"></a>Instruções passo a passo: implantando um aplicativo ClickOnce manualmente
Se você não pode usar o Visual Studio para implantar seu [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativo, ou você precisa usar os recursos de implantação avançada, como implantação de aplicativos confiáveis, você deve usar a ferramenta de linha de comando Mage.exe para criar seu [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifestos. Este passo a passo descreve como criar um [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] implantação usando a versão de linha de comando (Mage.exe) ou a versão gráfica (MageUI.exe) da ferramenta de edição e geração de manifesto.  
  
## <a name="prerequisites"></a>Pré-requisitos  
 Este passo a passo tem alguns pré-requisitos e opções que você precisa escolher antes de criar uma implantação.  
  
-   Instale o Mage.exe e MageUI.exe.  
  
     Mage.exe e MageUI.exe fazem parte do [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)]. Você deve ter o [!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)] instalado ou a versão do [!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)] incluídos com o Visual Studio. Para obter mais informações, consulte [SDK do Windows](http://go.microsoft.com/fwlink/?LinkId=158044) no MSDN.  
  
-   Forneça um aplicativo para implantação.  
  
     Este passo a passo pressupõe que você tenha um aplicativo do Windows que você está pronto para implantar. Este aplicativo será referenciado como AppToDeploy.  
  
-   Determine como a implantação será distribuída.  
  
     As opções de distribuição incluem: Web, compartilhamento de arquivos ou CD. Para obter mais informações, consulte [Segurança e implantação do ClickOnce](../deployment/clickonce-security-and-deployment.md).  
  
-   Determine se o aplicativo exige um nível elevado de confiança.  
  
     Se seu aplicativo requer confiança total — por exemplo, acesso completo ao sistema do usuário — você pode usar o `-TrustLevel` opção de Mage.exe para definir isso. Se você quiser definir uma permissão personalizada definida para o seu aplicativo, copie a seção de permissão Internet ou intranet do manifesto de outro, modificá-lo para atender às suas necessidades e adicioná-lo ao manifesto do aplicativo usando um editor de texto ou MageUI.exe. Para obter mais informações, consulte [Trusted Application Deployment Overview](../deployment/trusted-application-deployment-overview.md).  
  
-   Obtenha um certificado Authenticode.  
  
     Você deve assinar a implantação com um certificado Authenticode. Você pode gerar um certificado de teste usando as ferramentas do Visual Studio, MageUI.exe, ou MakeCert.exe e Pvk2Pfx.exe, ou você pode obter um certificado de uma autoridade de certificação (CA). Se você optar por usar a implantação de aplicativos confiáveis, você também deve executar uma única instalação do certificado em todos os computadores cliente. Para obter mais informações, consulte [Trusted Application Deployment Overview](../deployment/trusted-application-deployment-overview.md).  
  
    > [!NOTE]
    >  Você também pode assinar a implantação com um certificado CNG que você pode obter de uma autoridade de certificação.  
  
-   Certifique-se de que o aplicativo não tem um manifesto com informações de UAC.  
  
     Você precisa determinar se seu aplicativo contém um manifesto com informações de controle de conta de usuário (UAC), como um `<dependentAssembly>` elemento. Para examinar um manifesto de aplicativo, você pode usar o Windows Sysinternals [Sigcheck](http://go.microsoft.com/fwlink/?LinkId=158035) utilitário.  
  
     Se seu aplicativo contém um manifesto com detalhes UAC, você deve criá-lo novamente sem as informações de UAC. Para um projeto c# no Visual Studio, abra as propriedades do projeto e selecione a guia do aplicativo. No **manifesto** lista suspensa, selecione **criar aplicativo sem um manifesto**. Para um projeto do Visual Basic no Visual Studio, abra as propriedades do projeto, selecione a guia do aplicativo e clique em **exibir configurações de UAC**. No arquivo de manifesto aberto, remova todos os elementos dentro do único `<asmv1:assembly>` elemento.  
  
-   Determine se o aplicativo exige pré-requisitos no computador cliente.  
  
     [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]os aplicativos implantados no Visual Studio podem incluir um bootstrapper de instalação de pré-requisito (setup.exe) com sua implantação. Este passo a passo cria dois manifestos necessários para um [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] implantação. Você pode criar um bootstrapper pré-requisito usando o [tarefa GenerateBootstrapper](../msbuild/generatebootstrapper-task.md).  
  
### <a name="to-deploy-an-application-with-the-mageexe-command-line-tool"></a>Para implantar um aplicativo com a ferramenta de linha de comando Mage.exe  
  
1.  Crie um diretório onde você armazenará o [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] arquivos de implantação.  
  
2.  No diretório de implantação que você acabou de criar, crie um subdiretório de versão. Se esta for a primeira vez que você está implantando o aplicativo, nome de subdiretório de versão **1.0.0.0**.  
  
    > [!NOTE]
    >  A versão da sua implantação pode ser diferente da versão do seu aplicativo.  
  
3.  Copie todos os arquivos de aplicativo para o subdiretório de versão, incluindo arquivos executáveis, assemblies, recursos e arquivos de dados. Se necessário, você pode criar mais subpastas que contêm arquivos adicionais.  
  
4.  Abra o [!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)] ou o comando prompt e mudar para a subpasta de versão do Visual Studio.  
  
5.  Crie o manifesto do aplicativo com uma chamada para Mage.exe. A instrução a seguir cria um manifesto de aplicativo para o código compilado para ser executado no processador Intel x86.  
  
    ```  
    mage -New Application -Processor x86 -ToFile AppToDeploy.exe.manifest -name "My App" -Version 1.0.0.0 -FromDirectory .   
    ```  
  
    > [!NOTE]
    >  Certifique-se de incluir o ponto (.) após o `-FromDirectory` opção, que indica o diretório atual. Se você não incluir o ponto final, você deve especificar o caminho para os arquivos do aplicativo.  
  
6.  Assinar o manifesto de aplicativo com o seu certificado Authenticode. Substituir *mycert.pfx* com o caminho para o arquivo de certificado. Substituir *senhas* com a senha para o arquivo de certificado.  
  
    ```  
    mage -Sign AppToDeploy.exe.manifest -CertFile mycert.pfx -Password passwd  
    ```  
  
     Para assinar o manifesto do aplicativo com um certificado CNG, use o seguinte. Substituir *cngCert.pfx* com o caminho para o arquivo de certificado.  
  
    ```  
    mage -Sign AppToDeploy.exe.manifest -CertFile cngCert.pfx  
    ```  
  
7.  Alterar a raiz do diretório de implantação.  
  
8.  Gere o manifesto de implantação com uma chamada para Mage.exe. Por padrão, Mage.exe marcará o [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] implantação como um aplicativo instalado, para que ele possa executar ambos online e offline. Para disponibilizar o aplicativo somente quando o usuário está online, use o `-Install` opção com um valor de `false`. Se você usar o padrão e usuários instalem o aplicativo de um site ou compartilhamento de arquivos, verifique se o valor da `-ProviderUrl` de manifesto no servidor Web ou compartilhamento de pontos de opção para o local do aplicativo.  
  
    ```  
    mage -New Deployment -Processor x86 -Install true -Publisher "My Co." -ProviderUrl "\\myServer\myShare\AppToDeploy.application" -AppManifest 1.0.0.0\AppToDeploy.exe.manifest -ToFile AppToDeploy.application  
    ```  
  
9. Assinar o manifesto de implantação com o seu certificado Authenticode ou CNG.  
  
    ```  
    mage -Sign AppToDeploy.application -CertFile mycert.pfx -Password passwd  
    ```  
  
     ou  
  
    ```  
    mage -Sign AppToDeploy.exe.manifest -CertFile cngCert.pfx  
    ```  
  
10. Copie todos os arquivos no diretório de implantação para o destino de implantação ou a mídia. Isso pode ser uma pasta em um site da Web ou site FTP, um compartilhamento de arquivos ou um CD-ROM.  
  
11. Fornece aos usuários com a URL, UNC ou mídia física necessárias para instalar o aplicativo. Se você fornecer uma URL ou um UNC, você deve dar aos usuários o caminho completo para o manifesto de implantação. Por exemplo, se AppToDeploy for implantado em http://webserver01/ no diretório AppToDeploy, o caminho completo de URL seria http://webserver01/AppToDeploy/AppToDeploy.application.  
  
### <a name="to-deploy-an-application-with-the-mageuiexe-graphical-tool"></a>Para implantar um aplicativo com a ferramenta gráfica MageUI.exe  
  
1.  Crie um diretório onde você armazenará o [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] arquivos de implantação.  
  
2.  No diretório de implantação que você acabou de criar, crie um subdiretório de versão. Se esta for a primeira vez que você está implantando o aplicativo, nome de subdiretório de versão **1.0.0.0**.  
  
    > [!NOTE]
    >  A versão da implantação é provavelmente diferente da versão do seu aplicativo.  
  
3.  Copie todos os arquivos de aplicativo para o subdiretório de versão, incluindo arquivos executáveis, assemblies, recursos e arquivos de dados. Se necessário, você pode criar mais subpastas que contêm arquivos adicionais.  
  
4.  Inicie a ferramenta gráfica MageUI.exe.  
  
    ```  
    MageUI.exe  
    ```  
  
5.  Criar um novo manifesto de aplicativo, selecionando **arquivo**, **novo**, **manifesto do aplicativo** no menu.  
  
6.  O padrão **nome** guia, digite o número de versão e o nome desta implantação. Especifique também o **processador** que seu aplicativo é criado, como x86.  
  
7.  Selecione o **arquivos** guia e clique no botão de reticências (**...** ) ao lado de **diretório de aplicativo** caixa de texto. Será exibida uma caixa de diálogo Procurar pasta.  
  
8.  Selecione o subdiretório de versão que contém os arquivos de aplicativo e, em seguida, clique em **Okey**.  
  
9. Se você implantará do Internet Information Services (IIS), selecione o **quando popular adicionar a extensão. Deploy para qualquer arquivo que não tem** caixa de seleção.  
  
10. Clique o **popular** botão para adicionar todos os arquivos de aplicativo à lista de arquivos. Se seu aplicativo contém mais de um arquivo executável, marcar o arquivo executável principal para a implantação do aplicativo de inicialização selecionando **ponto de entrada** do **tipo de arquivo** lista suspensa. (Se seu aplicativo contiver apenas um arquivo executável, MageUI.exe será marcá-la para você.)  
  
11. Selecione o **permissões necessárias** guia e selecione o nível de confiança que você precisa declarar seu aplicativo. O padrão é **FullTrust**, que será adequado para a maioria dos aplicativos.  
  
12. Selecione **arquivo**, **Salvar como** no menu. Uma caixa de diálogo Opções de assinatura é exibida solicitando que você assine o manifesto do aplicativo.  
  
13. Se você tiver um certificado armazenado como um arquivo no sistema de arquivos, use o **entrar com o arquivo de certificado** opção e selecione o certificado do sistema de arquivos usando o botão de reticências (**...** ) botão. Em seguida, digite a senha do certificado.  
  
     -ou-  
  
     Se o certificado é mantido em um repositório de certificados acessível em seu computador, selecione o **assinar com certificado armazenado** opção e selecione o certificado na lista fornecida.  
  
14. Clique em **Okey** para assinar o manifesto do aplicativo. Será exibida a caixa de diálogo Salvar como.  
  
15. Na caixa de diálogo Salvar como, especifique o diretório de versão e, em seguida, clique em **salvar**.  
  
16. Selecione **arquivo**, **novo**, **manifesto de implantação** no menu para criar o manifesto de implantação.  
  
17. Sobre o **nome** guia, especifique um nome e número de versão para essa implantação (**1.0.0.0** neste exemplo). Especifique também o **processador** que seu aplicativo é criado, como x86.  
  
18. Selecione o **descrição** guia e especificar valores para **publicador** e **Produc * t**. (**Produto** é o nome fornecido para seu aplicativo no menu Iniciar do Windows quando seu aplicativo é instalado em um computador cliente para uso off-line.)  
  
19. Selecione o **opções de implantação** guia e no **local iniciar** texto, especifique o local do manifesto do aplicativo no servidor Web ou no compartilhamento. Por exemplo, \\\myServer\myShare\AppToDeploy.application.  
  
20. Se você adicionou a extensão. Deploy em uma etapa anterior, também selecione **usar a extensão de nome de arquivo. Deploy** aqui.  
  
21. Selecione o **as opções de atualização** guia e, em seguida, especifique a frequência na qual você quer que este aplicativo para atualizar. Se seu aplicativo usa <xref:System.Deployment.Application.UpdateCheckInfo> para verificar se há atualizações em si, desmarque o **este aplicativo deve verificar se há atualizações** caixa de seleção.  
  
22. Selecione o **aplicativo referência** guia e, em seguida, clique no **selecione manifesto** botão. Uma caixa de diálogo Abrir é exibida.  
  
23. Selecione o manifesto do aplicativo que você criou anteriormente e, em seguida, clique em **abrir**.  
  
24. Selecione **arquivo**, **Salvar como** no menu. Uma caixa de diálogo Opções de assinatura é exibida solicitando que você assinar o manifesto de implantação.  
  
25. Se você tiver um certificado armazenado como um arquivo no sistema de arquivos, use o **entrar com o arquivo de certificado** opção e selecione o certificado do sistema de arquivos usando o botão de reticências (**...** ) botão. Em seguida, digite a senha do certificado.  
  
     -ou-  
  
     Se o certificado é mantido em um repositório de certificados acessível em seu computador, selecione o **assinar com certificado armazenado** opção e selecione o certificado na lista fornecida.  
  
26. Clique em **Okey** para assinar seu manifesto de implantação. Será exibida a caixa de diálogo Salvar como.  
  
27. No **Salvar como** caixa de diálogo Mover para cima de um diretório para a raiz da sua implantação e clique **salvar**.  
  
28. Copie todos os arquivos no diretório de implantação para o destino de implantação ou a mídia. Isso pode ser uma pasta em um site da Web ou site FTP, um compartilhamento de arquivos ou um CD-ROM.  
  
29. Fornece aos usuários com a URL, UNC ou mídia física necessárias para instalar o aplicativo. Se você fornecer uma URL ou um UNC, você deve fornecer aos usuários o caminho completo, o manifesto de implantação. Por exemplo, se AppToDeploy for implantado em http://webserver01/ no diretório AppToDeploy, o caminho completo de URL seria http://webserver01/AppToDeploy/AppToDeploy.application.  
  
## <a name="next-steps"></a>Próximas etapas  
 Quando você precisa implantar uma nova versão do aplicativo, crie um novo diretório chamado após a nova versão — por exemplo, 1.0.0.1—and copiar os novos arquivos de aplicativo para o novo diretório. Em seguida, você precisa seguir as etapas anteriores para criar e assinar um novo manifesto de aplicativo, atualizar e assinar o manifesto de implantação. Tenha cuidado para especificar a mesma versão superior em ambos os Mage.exe `-New` e `-Update` chamadas, como [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] só atualiza versões superiores, com o inteiro mais à esquerda mais significativo. Se você usou MageUI.exe, você pode atualizar o manifesto de implantação abrindo-o, selecionando o **aplicativo referência** guia, clicando no **selecione manifesto** botão e, em seguida, selecionando a atualização manifesto do aplicativo.  
  
## <a name="see-also"></a>Consulte também  
 [Mage.exe (Manifest Generation and Editing Tool)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)   
 [MageUI.exe (Manifest Generation and Editing Tool, Cliente Gráfico)](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client)   
 [Publicando aplicativos ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Manifesto de implantação do ClickOnce](../deployment/clickonce-deployment-manifest.md)   
 [Manifesto de aplicativo ClickOnce](../deployment/clickonce-application-manifest.md)