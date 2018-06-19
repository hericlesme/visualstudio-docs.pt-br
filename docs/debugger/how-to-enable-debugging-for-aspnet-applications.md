---
title: Habilitar a depuração para aplicativos ASP.NET | Microsoft Docs
ms.custom: H1HackMay2017
ms.date: 09/21/17
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging ASP.NET Web applications
- Web.config configuration file, debug mode
- debugging [Visual Studio], ASP.NET
ms.assetid: 3beed819-cece-4864-8184-bd410000973a
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- aspnet
ms.openlocfilehash: 3418e1d2e05d687f8cb73a7857178ae1060d56f8
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2018
ms.locfileid: "31479384"
---
# <a name="debug-aspnet-applications-in-visual-studio"></a>Depurar aplicativos ASP.NET no Visual Studio

Você pode depurar aplicativos do ASP.NET no Visual Studio.

## <a name="requirements"></a>Requisitos

Para seguir as instruções neste tópico, você precisa:

- O IIS Express, que é incluído por padrão no Visual Studio 2012 e posterior

    -ou-

- Local IIS web server (versão 8.0 ou superior) que está configurado corretamente e pode executar o aplicativo ASP.NET sem erros.

Se o servidor for remoto, o depurador remoto deve estar executando no computador remoto. Para depurar em um servidor remoto do IIS, consulte [ASP.NET de depuração remota em um computador com IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md). 

## <a name="configure-debug-settings"></a>Definir configurações de depuração

### <a name="enable-aspnet-debugging-in-the-project-properties"></a>Habilitar depuração ASP.NET nas propriedades do projeto

1. Abra seu projeto do ASP.NET no Visual Studio.

2. Clique com botão direito no projeto no **Solution Explorer**, escolha **propriedades**e, em seguida, clique no **Web** guia.

    Para alguns tipos de projeto, selecione **Propriedades > Depurar** em vez disso. Para um projeto Web Forms ASP.NET, clique com o botão direito e selecione **páginas de propriedade > Opções de inicialização**.
  
3.  Em **depuradores**, selecione o **ASP.NET** caixa de seleção.

    ![Configurações do depurador](../debugger/media/dbg-aspnet-enable-debugging.png "configurações do depurador")

> [!NOTE]
> Se você criar um novo projeto ASP.NET (**arquivo > Novo projeto**), as configurações de depuração já estão configuradas corretamente.

### <a name="enable-debugging-in-the-webconfig-file"></a>Habilitar a depuração no arquivo Web. config  

Para depurar um aplicativo web, arquivo de Web. config do aplicativo deve ser configurado corretamente. Se você hospedar o aplicativo no IIS ou IIS Express, é necessário um arquivo Web. config.

Para o ASP.NET Core, o arquivo Web. config é criado automaticamente quando o aplicativo é implantado (se ainda não estiver presente).

> [!TIP]
> O processo de implantação pode atualizar as configurações de Web. config. Portanto, antes de tentar depurar, verifique a configuração de Web. config no servidor.
  
1.  No Visual Studio, abra o arquivo do projeto Web. config.  
  
    > [!NOTE]  
    > Você não pode acessar o arquivo Web. config remotamente, usando um navegador da Web. Por razões de segurança, o [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] configura o servidor IIS da Microsoft para ajudar a impedir o acesso direto do navegador aos arquivos Web.config. Se você tentar acessar um arquivo de configuração usando um navegador, você receberá um erro de acesso HTTP 403 (proibido).  
  
2.  Localize o elemento `configuration/system.web/compilation`. Se o elemento de compilação não existir, crie-o.

    Web.config é um arquivo XML e, assim, contém as seções aninhadas marcadas por aspas.
  
3.  Se o elemento `compilation` não contiver um atributo `debug`, adicione o atributo ao elemento.  
  
4.  Verifique se o valor do atributo `debug` está definido como `true`.  
  
O arquivo Web. config deve ser semelhante ao seguinte exemplo:

> [!NOTE]
> Este exemplo é um arquivo Web. config parcial. Seções XML adicionais são normalmente presentes entre a configuração e os elementos de System. Web. Elemento compilation também pode conter outros elementos e atributos.
  
#### <a name="example"></a>Exemplo  
  
```  
<configuration>  
    ...  
    <system.web>  
        <compilation  
            debug="true"  
            ...  
        >  
        ...  
        </compilation>  
    </system.web>  
</configuration>  
```

Se você estiver usando um servidor externo em vez do servidor de IIS Express padrão, você também deve verificar se que o `targetFramework` valor de atributo corresponde à configuração no servidor.

> [!IMPORTANT]
> Para melhor desempenho, defina um aplicativo de produção `debug=false` e especifique uma compilação de versão, quando você criar e publica o aplicativo.

## <a name="configure-project-settings-for-the-server"></a>Definir configurações de projeto para o servidor

Para depurar em um servidor web local, defina as propriedades do projeto. Para depurar em um servidor remoto, siga as instruções de mais abrangentes descritas em [ASP.NET de depuração remota no IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md) em vez disso.

1. No **Web** guia do projeto de propriedades, selecione **IIS Express** ou **servidor externo** sob o **servidor** configurações. (Para alguns tipos de projeto, essas configurações aparecem sob o **depurar** guia em vez disso.)

    ![As configurações do servidor](../debugger/media/dbg-aspnet-server-settings.png "as configurações do servidor")

    O IIS Express é o servidor padrão para o ASP.NET e geralmente não exige nenhuma configuração especial. Essa é a maneira mais fácil para depurar um aplicativo ASP.NET.

    Para um projeto Web Forms ASP.NET, com o botão direito no projeto, escolha **páginas de propriedade > Opções de inicialização**e selecione **usar o servidor Web padrão** ou **usar servidor personalizado** ( em vez de **servidor externo**).

    ![Configurações do servidor para o aplicativo Web Forms](../debugger/media/dbg-aspnet-server-settings-webforms.png "configurações do servidor para o aplicativo de Web Forms")

2. Se você escolher um servidor (personalizado), insira a URL correta no **URL do projeto** (ou **URL Base**) campo.

    Se o servidor externo é IIS local, o IIS deve ser instalado e configurado corretamente. Por exemplo, a versão correta do ASP.NET deve ser configurada no IIS. Para obter mais informações, consulte [IIS 8.0 usando ASP.NET 3.5 e o ASP.NET 4.5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45). Se você quiser testar a implantação, bem como de depuração, consulte [implantando para testar](/aspnet/web-forms/overview/deployment/visual-studio-web-deployment/deploying-to-iis).

    Se o servidor externo é [remoto](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md), anexar ao processo em vez disso, e essas configurações de projeto não são usadas para depuração.

## <a name="local-iis-web-server-configure-iis"></a>(Servidor web do IIS local) Configurar o IIS

Para o IIS Express, você não precisa configurar o servidor web (ignore esta seção). O IIS Express é recomendado para testes iniciais.

Se você estiver usando o servidor web local do IIS, siga estas etapas.

1. Certifique-se de que o IIS está instalado corretamente. Para obter mais informações, consulte [IIS 8.0 usando ASP.NET 3.5 e o ASP.NET 4.5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45).

    * Certifique-se de que você instale a versão correta do ASP.NET no servidor. Use o Web Platform Installer (WebPI) para instalar o ASP.NET 4.5 (no nó do servidor no Windows Server 2012 R2, escolha **obter novos componentes do Web Platform** e, em seguida, procure ASP.NET). Para instalar o ASP.NET Core, consulte [publicar no IIS](https://docs.asp.net/en/latest/publishing/iis.html#iis-configuration).

    > [!NOTE]
    > Se você estiver usando o Windows Server 2008 R2, instale o ASP.NET 4, em vez de usar este comando:

     **C:\Windows\Microsoft.NET\Framework64\v4.0.30319\aspnet_regiis.exe -ir**

2. Abra o **serviços de informações da Internet (IIS) Manager**. (No painel esquerdo do Gerenciador do servidor, selecione **IIS**. O servidor e selecione **serviços de informações da Internet (IIS) Manager**.)

3. Em **conexões** no painel esquerdo, vá para **Sites**.

4. Clique com botão direito do **Default Web Site** nó e selecione **Adicionar aplicativo**.

5. Definir o **Alias** campo **MyASPApp**, aceite o padrão do Pool de aplicativos (**DefaultAppPool**) e defina o **caminho físico** para  **C:\inetpub\myNewFolder** (criar uma nova pasta para o aplicativo).

6. Em **conexões**, selecione **Pools de aplicativos**. Abra **DefaultAppPool** e defina o campo de pool de aplicativos para o valor correto para seu aplicativo (use ASP.NET 4 para ASP.NET 4.5. Use **nenhum código gerenciado** ASP.NET core).

## <a name="local-iis-web-server-deploy-the-app"></a>(Servidor web do IIS local) Implantar o aplicativo

Para o IIS Express, o aplicativo web é implantado automaticamente quando você inicia a depuração (ignore esta seção).

Se você estiver usando o servidor web local do IIS, siga estas etapas. Há maneiras diferentes para publicar seu aplicativo no IIS. Essas etapas, mostramos como criar e usar um perfil de publicação para que você possa implantar usando o sistema de arquivos.

1. Reinicie o Visual Studio como administrador.

    Para implantar usando esse método, você precisa de privilégios de administrador.

2. No Visual Studio, clique com o botão direito e escolha **publicar** (para formulários da Web, use **Publicar Web App**).

3. Escolha **IIS, FTP, etc.** e clique em **publicar**.

    ![Publicar no IIS](../debugger/media/dbg-aspnet-local-iis.png "publicar no IIS")

    Para um aplicativo de Web Forms, escolha **personalizado** na caixa de diálogo Publicar, insira um nome de perfil e escolha **Okey**.

4. No **publicar método** campo, escolha **sistema de arquivos**.

5. Para o **local de destino**, clique no **procurar** botão.

6. (ASP.NET Core) Escolha **sistema de arquivos** e selecione a pasta em que você criou anteriormente para o aplicativo.

6. (ASP.NET) Escolha **Local IIS**e selecione o site da web, você criou anteriormente e, em seguida, clique em **abrir**.

    ![Publicar no IIS](../debugger/media/dbg-aspnet-local-iis-select-site.png "publicar no IIS")

    > [!TIP]
    > Se você vir uma mensagem que diz que o servidor web não está configurada corretamente, certifique-se de que a versão correta do ASP.NET está instalada para o IIS.

7. Clique em **próximo** e escolha um **depurar** configuração.

    > [!NOTE]
    > Se você implantar com uma configuração de versão, isso define `debug=false` no arquivo de Web. config do servidor.

8. Clique em **salvar** para salvar as configurações de publicação e, em seguida, clique em **publicar**.

    > [!CAUTION]
    >  Se você precisar fazer alterações no código ou recompilação, você deve republicar e repita esta etapa. O executável que você copiou para o computador remoto deve corresponder exatamente, seu local de origem e símbolos.

## <a name="set-a-breakpoint-and-start-debugging"></a>Definir um ponto de interrupção e iniciar a depuração

1. Em seu projeto no Visual Studio, definir um ponto de interrupção em algum código que você sabe que será executado.

2. Para iniciar a depuração, pressione **F5** (**Depurar > Iniciar depuração**).

3. Execute ações para executar o código que contém o ponto de interrupção.

    A pausa do depurador onde você pode definir o ponto de interrupção.

### <a name="local-iis-troubleshooting-cannot-hit-the-breakpoint"></a>(IIS) local Solução de problemas: Não é possível atingir o ponto de interrupção

1. Iniciar o aplicativo web do IIS e certificar-se de que ele é executado corretamente. Deixe o aplicativo web em execução.

2. No Visual Studio, selecione **Depurar > Anexar ao processo** e conecte-se ao processo do ASP.NET (normalmente **w3wp.exe** ou **dotnet.exe**). Para obter mais informações, consulte [anexar ao processo](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).

    Se você puder se conectar usando **anexar ao processo** e pode atingir um ponto de interrupção, mas não é possível iniciar a depuração usando **F5**, em seguida, é provável que uma configuração incorreta nas propriedades do projeto. Se você estiver usando um arquivo de HOSTS, verifique se ele está configurado corretamente.

  
## <a name="robust-programming"></a>Programação robusta  
O [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] detecta automaticamente todas as alterações nos arquivos Web.config e aplica novos parâmetros de configuração. Você não precisa reiniciar o computador ou reinicie o servidor IIS para que as alterações entrem em vigor.  
  
Um site pode conter vários diretórios e subdiretórios virtuais, e arquivos Web.config podem existir em cada um. Os aplicativos [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] herdam as configurações de arquivos Web.config em níveis mais altos no caminho da URL. Os arquivos de configuração hierárquicos permitem modificar configurações de vários aplicativos [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] ao mesmo tempo, como, por exemplo, para todos os aplicativos abaixo deles na hierarquia. No entanto, se `debug` é definido em um arquivo inferior na hierarquia, ele substitui o valor mais alto.  
  
Por exemplo, você pode especificar `debug="true"` em www.microsoft.com/aaa/Web.config e qualquer aplicativo na pasta aaa ou em qualquer subpasta de aaa herdará essa configuração. Portanto, se seu [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplicativo é www.microsoft.com/aaa/bbb, ele herda essa configuração, assim como qualquer [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplicativos em www.microsoft.com/aaa/ccc, www.microsoft.com/aaa/ddd e assim por diante. A única exceção será se um desses aplicativos substituir a configuração por meio de seu próprio arquivo mais baixo Web.config.  
  
> [!IMPORTANT]
> Habilitar o modo de depuração muito afeta o desempenho do seu [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplicativo. Lembre-se de desabilitar o modo de depuração antes de implantar um aplicativo de versão ou conduzir medidas de desempenho.  
  
## <a name="see-also"></a>Consulte também  
[Depuração do ASP.NET: requisitos do sistema](aspnet-debugging-system-requirements.md)   
[Como: executar o processo de trabalho em uma conta de usuário](how-to-run-the-worker-process-under-a-user-account.md)   
[Como: localizar o nome do processo do ASP.NET](how-to-find-the-name-of-the-aspnet-process.md)   
[Depurar aplicativos da Web implantados](debugging-deployed-web-applications.md)   
[Passo a passo: Depurando um formulário da Web](walkthrough-debugging-a-web-form.md)   
[Como: depurar exceções do ASP.NET](how-to-debug-aspnet-exceptions.md)   
[Depurar aplicativos Web: erros e solução de problemas](debugging-web-applications-errors-and-troubleshooting.md)
  