---
title: Compilando aplicativos ClickOnce a partir da linha de comando | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, from command line
- publishing
- publishing, ClickOnce
ms.assetid: d9bc6212-c584-4f72-88c9-9a4b998c555e
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4488f32b135d766f494bc94946fbf77d42eb1e95
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/19/2018
ms.locfileid: "31566180"
---
# <a name="building-clickonce-applications-from-the-command-line"></a>Compilando aplicativos ClickOnce a partir da linha de comando
Em [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)], você pode criar projetos de linha de comando, mesmo se eles são criados no ambiente de desenvolvimento integrado (IDE). Na verdade, você pode recompilar um projeto criado com [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] em outro computador que tenha apenas o [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] instalado. Isso permite que você reproduza uma compilação usando um processo automatizado, por exemplo, em uma compilação central de laboratório ou usando scripts avançados técnicas além do escopo de compilar o projeto em si.  
  
## <a name="using-msbuild-to-reproduce-clickonce-application-deployments"></a>Usando o MSBuild para reproduzir a implantações de aplicativos ClickOnce  
 Quando você invoca o msbuild /target:publish na linha de comando, ele informa ao sistema de MSBuild para compilar o projeto e criar um [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativo na pasta de publicação. Isso é equivalente a selecionar o **publicar** comando no IDE.  
  
 Esse comando executa o msbuild.exe, que está no caminho no ambiente de prompt de comando do Visual Studio.  
  
 Um "destino" é um indicador para o MSBuild sobre como processar o comando. Os destinos de chave são o destino de "criação" e o destino "Publicar". O destino de compilação é o equivalente a selecionar a compilação comando (ou pressionando F5) no IDE. Se você deseja compilar o projeto, você poderá obter que digitando `msbuild`. Esse comando funciona porque o destino de compilação é o destino padrão para todos os projetos gerados pelo [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]. Isso significa que você não precise explicitamente especificar o destino de compilação. Portanto, digitando `msbuild` é a mesma operação que digitar `msbuild /target:build`.  
  
 O `/target:publish` comando informa o MSBuild para invocar o destino de publicação. O destino de publicação depende do destino de compilação. Isso significa que a operação de publicação é um superconjunto da operação de compilação. Por exemplo, se você fez uma alteração em um de seus arquivos de origem do Visual Basic ou c#, o assembly correspondente automaticamente ser recriado pela operação de publicação.  
  
 Para obter informações sobre como gerar um completo [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] implantação usando a ferramenta de linha de comando Mage.exe para criar seu [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] de manifesto, consulte [passo a passo: Implantando manualmente um aplicativo ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).  
  
## <a name="creating-and-building-a-basic-clickonce-application-using-msbuild"></a>Criar e compilar um aplicativo ClickOnce básica usando MSBuild  
  
#### <a name="to-create-and-publish-a-clickonce-project"></a>Para criar e publicar um projeto do ClickOnce  
  
1.  Clique em **novo projeto** do **arquivo** menu. A caixa de diálogo **Novo Projeto** é exibida.  
  
2.  Selecione **aplicativo do Windows** e nomeie-o `CmdLineDemo`.  
  
3.  Do **criar** menu, clique no **publicar** comando.  
  
     Essa etapa garante que o projeto está configurado corretamente para produzir um [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] implantação de aplicativo.  
  
     O Assistente de Publicação será exibido.  
  
4.  No Assistente de publicação, clique em **concluir**.  
  
     O Visual Studio gera e exibe a página da Web padrão, chamada Publish.  
  
5.  Salvar seu projeto e anote o local da pasta na qual ela está armazenada.  
  
 As etapas acima para criar um [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] projeto que foi publicado pela primeira vez. Agora você pode reproduzir a compilação fora do IDE.  
  
#### <a name="to-reproduce-the-build-from-the-command-line"></a>Para reproduzir a compilação da linha de comando  
  
1.  Saia do [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)].  
  
2.  Do Windows **iniciar** menu, clique em **todos os programas**, em seguida, **Microsoft Visual Studio**, em seguida, **ferramentas do Visual Studio**, e **Prompt de comando do visual Studio**. Isso deve abrir um prompt de comando na pasta raiz do usuário atual.  
  
3.  No **Prompt de comando do Visual Studio**, altere o diretório atual para o local do projeto que você acabou de criar acima. Por exemplo, digite `chdir My Documents\Visual Studio\Projects\CmdLineDemo`.  
  
4.  Para remover os arquivos existentes gerados em "para criar e publicar um [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] projeto," tipo `rmdir /s publish`.  
  
     Esta etapa é opcional, mas garante que os novos arquivos foram todos produzidos pela compilação de linha de comando.  
  
5.  Digite `msbuild /target:publish` no terminal integrado.  
  
 As etapas acima produzirá uma completa [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] implantação de aplicativo em uma subpasta do seu projeto chamado P**blicar**. CmdLineDemo.application é o [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] o manifesto de implantação. A pasta CmdLineDemo_1.0.0.0 contém os arquivos CmdLineDemo.exe e CmdLineDemo.exe.manifest, o [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] o manifesto do aplicativo. Setup.exe é o bootstrapper, que, por padrão, está configurado para instalar o [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]. A pasta DotNetFX contém redistribuíveis para o [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]. Este é o conjunto inteiro de arquivos que necessários para implantar seu aplicativo na Web ou por meio de CD/DVD ou UNC.  
  
## <a name="publishing-properties"></a>Propriedades de publicação  
 Quando você publicar o aplicativo nos procedimentos acima, as seguintes propriedades são inseridas no arquivo de projeto pelo Assistente de publicação. Essas propriedades diretamente influenciam como o [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativo é produzido.  
  
 Em CmdLineDemo.vbproj / CmdLineDemo.csproj:  
  
```  
<AssemblyOriginatorKeyFile>WindowsApplication3.snk</AssemblyOriginatorKeyFile>  
<GenerateManifests>true</GenerateManifests>  
<TargetZone>LocalIntranet</TargetZone>  
<PublisherName>Microsoft</PublisherName>  
<ProductName>CmdLineDemo</ProductName>  
<PublishUrl>http://localhost/CmdLineDemo</PublishUrl>  
<Install>true</Install>  
<ApplicationVersion>1.0.0.*</ApplicationVersion>  
<ApplicationRevision>1</ApplicationRevision>  
<UpdateEnabled>true</UpdateEnabled>  
<UpdateRequired>false</UpdateRequired>  
<UpdateMode>Foreground</UpdateMode>  
<UpdateInterval>7</UpdateInterval>  
<UpdateIntervalUnits>Days</UpdateIntervalUnits>  
<UpdateUrlEnabled>false</UpdateUrlEnabled>  
<IsWebBootstrapper>true</IsWebBootstrapper>  
<BootstrapperEnabled>true</BootstrapperEnabled>  
```  
  
 Você pode substituir qualquer uma dessas propriedades na linha de comando sem alterar o arquivo de projeto. Por exemplo, a seguir criará o [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] implantação de aplicativo sem o bootstrapper:  
  
```  
msbuild /target:publish /property:BootstrapperEnabled=false  
```  
  
 Propriedades de publicação são controladas no [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] do **publicar**, **segurança**, e **assinatura** páginas de propriedade a **Designer de projeto** . Abaixo está uma descrição das propriedades de publicação, juntamente com uma indicação de como cada um é configurada em várias páginas de propriedade do designer do aplicativo:  
  
-   `AssemblyOriginatorKeyFile` Determina o arquivo de chave usado para assinar seu [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifestos de aplicativo. Essa mesma chave também pode ser usado para atribuir um nome forte a seus assemblies. Essa propriedade é definida no **assinatura** página do **Project Designer**.  
  
 As seguintes propriedades são definidas no **segurança** página:  
  
-   **Habilitar configurações de segurança do ClickOnce** determina se [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifestos são gerados. Quando um projeto é criado inicialmente, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] geração de manifesto está desativado por padrão. O assistente se tornará automaticamente esse sinalizador em quando você publica pela primeira vez.  
  
-   **TargetZone** determina o nível de confiança para ser emitida no seu [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] o manifesto do aplicativo. Os valores possíveis são "Internet", "LocalIntranet" e "Custom". Internet e LocalIntranet fará com que um conjunto de permissões padrão para ser emitida no seu [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] o manifesto do aplicativo. LocalIntranet é o padrão e significa basicamente confiança total. Personalizado Especifica que somente as permissões explicitamente especificadas no arquivo App. manifest base devem ser emitida no [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] o manifesto do aplicativo. O arquivo App. manifest é um arquivo de manifesto parcial que contém apenas as definições de informações de confiança. É um arquivo oculto, quando você configurar permissões no automaticamente adicionado ao seu projeto de **segurança** página.  
  
 As seguintes propriedades são definidas no **publicar** página:  
  
-   `PublishUrl` é o local onde o aplicativo será publicado no IDE. Ele é inserido no [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifesto do aplicativo se nem o `InstallUrl` ou `UpdateUrl` propriedade for especificada.  
  
-   `ApplicationVersion` Especifica a versão do [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativo. Este é um número de versão de quatro dígitos. Se o último dígito é um "*", em seguida, o `ApplicationRevision` substituirá o valor inserido no manifesto no momento da compilação.  
  
-   `ApplicationRevision` Especifica a revisão. Este é um inteiro que é incrementado toda vez que você publica no IDE. Observe que não é incrementado automaticamente para compilações executadas na linha de comando.  
  
-   `Install` Determina se o aplicativo é um aplicativo de execução da Web ou de um aplicativo instalado.  
  
-   `InstallUrl` (não mostrado) é o local em que usuários instalem o aplicativo. Se especificado, esse valor é gravado no bootstrapper setup.exe se o `IsWebBootstrapper` propriedade está habilitada. Ele também é inserido na se manifesto do aplicativo a `UpdateUrl` não for especificado.  
  
-   `SupportUrl` (não mostrado) é o local vinculado a **adicionar ou remover programas** caixa de diálogo para um aplicativo instalado.  
  
 As seguintes propriedades são definidas **atualizações do aplicativo** caixa de diálogo, acessada a partir de **publicar** página.  
  
-   `UpdateEnabled` Indica se o aplicativo deve verificar se há atualizações.  
  
-   `UpdateMode` Especifica o primeiro plano ou atualizações em segundo plano.  
  
-   `UpdateInterval` Especifica a frequência com a qual o aplicativo deve verificar se há atualizações.  
  
-   `UpdateIntervalUnits` Especifica se o `UpdateInterval` valor está em unidades de horas, dias ou semanas.  
  
-   `UpdateUrl` (não mostrado) é o local em que o aplicativo receberá atualizações. Se especificado, esse valor é inserido no manifesto do aplicativo.  
  
-   As seguintes propriedades são definidas **opções de publicação** caixa de diálogo, acessada a partir de **publicar** página.  
  
-   `PublisherName` Especifica o nome do publicador exibido no prompt mostrado durante a instalação ou execução do aplicativo. No caso de um aplicativo instalado, ele também é usado para especificar o nome da pasta no **iniciar** menu.  
  
-   `ProductName` Especifica o nome do produto exibido no prompt mostrado durante a instalação ou execução do aplicativo. No caso de um aplicativo instalado, ele também é usado para especificar o nome do atalho no **iniciar** menu.  
  
-   As seguintes propriedades são definidas **pré-requisitos** caixa de diálogo, acessada a partir de **publicar** página.  
  
-   `BootstrapperEnabled` Determina se deve gerar bootstrapper setup.exe.  
  
-   `IsWebBootstrapper` Determina se o bootstrapper setup.exe funciona através da Web ou no modo baseado em disco.  
  
## <a name="installurl-supporturl-publishurl-and-updateurl"></a>InstallURL, SupportUrl, PublishURL e UpdateURL  
 A tabela a seguir mostra as quatro opções de URL para a implantação do ClickOnce.  
  
|Opção de URL|Descrição|  
|----------------|-----------------|  
|`PublishURL`|Necessário se você estiver publicando seu aplicativo ClickOnce para um site da Web.|  
|`InstallURL`|Opcional. Defina essa opção de URL se o site de instalação é diferente de `PublishURL`. Por exemplo, você pode definir o `PublishURL` para um caminho FTP e definir o `InstallURL` para uma URL da Web.|  
|`SupportURL`|Opcional. Defina essa opção de URL se o site de suporte é diferente de `PublishURL`. Por exemplo, você pode definir o `SupportURL` para o site de suporte ao cliente da sua empresa.|  
|`UpdateURL`|Opcional. Defina essa opção de URL se o local de atualização é diferente de `InstallURL`. Por exemplo, você pode definir o `PublishURL` para um caminho FTP e definir o `UpdateURL` para uma URL da Web.|  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.Build.Tasks.GenerateBootstrapper>   
 <xref:Microsoft.Build.Tasks.GenerateApplicationManifest>   
 <xref:Microsoft.Build.Tasks.GenerateDeploymentManifest>   
 [Segurança e implantação do ClickOnce](../deployment/clickonce-security-and-deployment.md)   
 [Passo a passo: implantando um aplicativo ClickOnce manualmente](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)