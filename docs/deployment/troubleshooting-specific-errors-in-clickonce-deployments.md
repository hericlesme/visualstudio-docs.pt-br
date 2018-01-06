---
title: "Solucionando problemas de erros específicos nas implantações do ClickOnce | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- Microsoft.VisualStudio.Publish.ClickOnceProvider.ErrorPrompt.UncRequired
- Microsoft.VisualStudio.Publish.ClickOnceProvider.ErrorPrompt.NoInstallUrl
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- deploying applications, ClickOnce
- troubleshooting ClickOnce deployments
- ClickOnce deployment, troubleshooting
ms.assetid: 22dfe8f1-8271-4708-9c25-6bbb13920ac8
caps.latest.revision: "13"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload: multiple
ms.openlocfilehash: ffa7449347fe5e898f2984237dfc8908e3bb2003
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="troubleshooting-specific-errors-in-clickonce-deployments"></a>Solução de problemas com erros específicos nas implantações do ClickOnce
Este tópico lista os seguintes erros comuns que podem ocorrer quando você implanta um [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativo e fornece etapas para resolver cada problema.  
  
## <a name="general-errors"></a>Erros gerais  
  
#### <a name="when-you-try-to-locate-an-application-file-nothing-occurs-or-xml-renders-in-internet-explorer-or-you-receive-a-run-or-save-as-dialog-box"></a>Quando tenta localizar um arquivo. Application, nada ocorre, XML renderiza no Internet Explorer, ou você recebe uma caixa de diálogo Executar ou salvar como  
 Esse erro provavelmente é causado por tipos de conteúdo (também conhecidos como tipos MIME) não está sendo registrados corretamente no servidor ou cliente.  
  
 Primeiro, certifique-se de que o servidor está configurado para associar a extensão. Application "application/x-ms-application" tipo de conteúdo.  
  
 Se o servidor está configurado corretamente, certifique-se de que o [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)] está instalado no seu computador. Se o [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)] estiver instalado, e você ainda estiver vendo esse problema, tente desinstalar e reinstalar o [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)] para registrar novamente o tipo de conteúdo no cliente.  
  
#### <a name="error-message-says-unable-to-retrieve-application-files-missing-in-deployment-or-application-download-has-been-interrupted-check-for-network-errors-and-try-again-later"></a>Mensagem de erro dizendo "não é possível recuperar o aplicativo. Arquivos ausentes na implantação"ou"download do aplicativo foi interrompida, verifique se há erros de rede e tente novamente mais tarde"  
 Esta mensagem indica que um ou mais arquivos que está sendo referenciados pelo [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifestos não podem ser baixados. A maneira mais fácil para depurar esse erro é tentar baixar a URL que [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] diz que não é possível baixar. Aqui estão algumas das possíveis causas:  
  
-   Se o arquivo de log diz "proibido (403)" ou "(404) não encontrado," verificar se o servidor Web está configurado para que ele não bloqueia o download deste arquivo. Para obter mais informações, consulte [Problemas de configuração de servidor e cliente em implantações do ClickOnce](../deployment/server-and-client-configuration-issues-in-clickonce-deployments.md).  
  
-   Se o arquivo. config está sendo bloqueado pelo servidor, consulte a seção "Baixar erro quando você tentar instalar um [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativo que tem um arquivo. config" mais adiante neste tópico.  
  
-   Determinar se isso ocorreu porque o `deploymentProvider` URL no manifesto de implantação está apontando para um local diferente a URL usada para ativação.  
  
-   Certifique-se de que todos os arquivos estão presentes no servidor. o [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] log deve indicar a qual o arquivo não foi encontrado.  
  
-   Se houver problemas de conectividade de rede; Você pode receber essa mensagem se o computador cliente ficou offline durante o download.  
  
#### <a name="download-error-when-you-try-to-install-a-clickonce-application-that-has-a-config-file"></a>Erro de download, quando você tentar instalar um aplicativo ClickOnce que tem um arquivo. config  
 Por padrão, um aplicativo do Windows do Visual Basic inclui um arquivo App. config. Haverá um problema quando um usuário tenta instalar de um servidor Web que usa o Windows Server 2003, porque o sistema operacional bloqueia a instalação dos arquivos. config por motivos de segurança. Para habilitar o arquivo. config para ser instalado, clique em **usar a extensão de arquivo. Deploy"** no **opções de publicação** caixa de diálogo.  
  
 Você também deve definir os tipos de conteúdo (também conhecidos como tipos MIME) adequadamente para arquivos. Deploy,. Application e. manifest. Para obter mais informações, consulte a documentação do servidor Web.  
  
 Para obter mais informações, consulte "Windows Server 2003: outra tipos de conteúdo" em [servidor e problemas de configuração de cliente em implantações do ClickOnce](../deployment/server-and-client-configuration-issues-in-clickonce-deployments.md).  
  
#### <a name="error-message-application-is-improperly-formatted-log-file-contains-xml-signature-is-invalid"></a>Mensagem de erro: "Aplicativo está formatado incorretamente;" Arquivo de log contém a "assinatura XML é inválida"  
 Verifique se você atualizou o arquivo de manifesto e assinado novamente. Republicar seu aplicativo usando [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ou usar a imagem para assinar o aplicativo novamente.  
  
#### <a name="you-updated-your-application-on-the-server-but-the-client-does-not-download-the-update"></a>Você atualizou o seu aplicativo no servidor, mas o cliente não baixa a atualização  
 Esse problema pode ser resolvido executando uma das seguintes tarefas:  
  
-   Examine o `deploymentProvider` URL no manifesto de implantação. Certifique-se de que você está atualizando os bits no mesmo local que `deploymentProvider` aponta para.  
  
-   Verifique se o intervalo de atualização no manifesto de implantação. Se esse intervalo é definido para um intervalo periódico, como uma vez a cada seis horas, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] não verificarão de uma atualização até que esse intervalo. Você pode alterar o manifesto para verificar se há uma atualização toda vez que o aplicativo for iniciado. Alterar o intervalo de atualização é uma opção conveniente durante o tempo de desenvolvimento para verificar as atualizações estão sendo instaladas, mas ela reduz a velocidade de ativação de aplicativo.  
  
-   Tente reiniciar o aplicativo no menu Iniciar. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]possivelmente foram detectados a atualização em segundo plano, mas será solicitado a instalar os bits na próxima ativação.  
  
#### <a name="during-update-you-receive-an-error-that-has-the-following-log-entry-the-reference-in-the-deployment-does-not-match-the-identity-defined-in-the-application-manifest"></a>Durante a atualização você receber um erro que tenha a seguinte entrada de log: "a referência na implantação não corresponde à identidade definida no manifesto do aplicativo"  
 Esse erro pode ocorrer porque você editar manualmente os manifestos de aplicativo e implantação e ter causado a descrição da identidade de um assembly em um manifesto para ficarem fora de sincronia com o outro. A identidade de um conjunto consiste em seu nome, versão, cultura e token de chave pública. Examine as descrições de identidade em seus manifestos e corrija qualquer diferença.  
  
#### <a name="first-time-activation-from-local-disk-or-cd-rom-succeeds-but-subsequent-activation-from-start-menu-does-not-succeed"></a>Primeira vez que a ativação do CD-ROM ou disco local for bem-sucedida, mas subsequente ativação do Menu Iniciar não for bem-sucedida  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]usa a URL do provedor de implantação para receber atualizações para o aplicativo. Verifique se o local que aponta para a URL está correto.  
  
#### <a name="error-cannot-start-the-application"></a>Erro: "não é possível iniciar o aplicativo"  
 Essa mensagem de erro geralmente indica que há um problema ao instalar este aplicativo para o [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] armazenar. O aplicativo tem um erro ou o armazenamento está corrompido. O arquivo de log pode informar onde ocorreu o erro.  
  
 Você deve fazer o seguinte:  
  
-   Verifique se a identidade do manifesto de implantação, a identidade do manifesto do aplicativo e identidade do aplicativo principal EXE sejam exclusivas.  
  
-   Verifique se seus caminhos de arquivo não estão mais de 100 caracteres. Se seu aplicativo contém os caminhos de arquivo que são muito longos, pode exceder o máximo de caminho, você pode armazenar as limitações. Tente encurtar os caminhos e reinstalar.  
  
#### <a name="privatepath-settings-in-application-config-file-are-not-honored"></a>Configurações de PrivatePath no arquivo de configuração do aplicativo não são respeitadas  
 Para usar PrivatePath (caminhos de investigação de fusão), o aplicativo deve solicitar permissão de confiança total. Tente alterar o manifesto do aplicativo para solicitar confiança total e, em seguida, tente novamente.  
  
#### <a name="during-uninstall-a-message-appears-saying-failed-to-uninstall-application"></a>Durante a desinstalação será exibida uma mensagem dizendo, "Falha ao desinstalar o aplicativo"  
 Essa mensagem geralmente indica que o aplicativo já foi removido ou o armazenamento está corrompido. Depois de clicar em **Okey**, o **adicionar ou remover programa** entrada será removida.  
  
#### <a name="during-installation-a-message-appears-that-says-that-the-platform-dependencies-are-not-installed"></a>Durante a instalação, será exibida uma mensagem informando que as dependências de plataforma não estão instaladas  
 Você não tem um pré-requisito no GAC (cache de assembly global) que o aplicativo precisa para executar.  
  
## <a name="publishing-with-visual-studio"></a>Publicação com o Visual Studio  
  
#### <a name="publishing-in-visual-studio-fails"></a>Falha de publicação no Visual Studio  
 Verifique se você tem o direito de publicar no servidor de destino. Por exemplo, se você estiver conectado a um servidor de terminal como um usuário comum, não como um administrador, você provavelmente não terá os direitos necessários para publicar o servidor Web local.  
  
 Se você estiver publicando uma URL, certifique-se de que o computador de destino tem extensões habilitado.  
  
#### <a name="error-message-unable-to-create-the-web-site-site-the-components-for-communicating-with-frontpage-server-extensions-are-not-installed"></a>Mensagem de erro: Não é possível criar o site da Web '\<site >'. Os componentes para comunicação com essas extensões não estão instalados.  
 Certifique-se de que você tenha o Microsoft Visual Studio Web criação componente instalado no computador que você está publicando da. Para usuários do Express, esse componente não está instalado por padrão. Para obter mais informações, consulte [http://go.microsoft.com/fwlink/?LinkId=102310](http://go.microsoft.com/fwlink/?LinkId=102310).  
  
#### <a name="error-message-could-not-find-file-microsoftwindowscommon-controls-version6000-culture-publickeytoken6595b64144ccf1df-processorarchitecture-typewin32"></a>Mensagem de erro: Não foi possível encontrar o arquivo ' Microsoft.Windows.Common-controles, versão = 6.0.0.0, cultura = *, PublicKeyToken = 6595b64144ccf1df, ProcessorArchitecture =\*, tipo = win32'  
 Essa mensagem de erro é exibida quando você tentar publicar um aplicativo do WPF com estilos visuais habilitados. Para resolver esse problema, consulte [como: publicar um aplicativo do WPF com habilitado de estilos visuais](../deployment/how-to-publish-a-wpf-application-with-visual-styles-enabled.md).  
  
## <a name="using-mage"></a>Usando a imagem  
  
#### <a name="you-tried-to-sign-with-a-certificate-in-your-certificate-store-and-a-received-blank-message-box"></a>Você tentou entrar com um certificado no repositório de certificados e uma caixa de mensagem em branco  
 No **assinatura** caixa de diálogo, você deve:  
  
-   Selecione **assinar com um certificado armazenado**, e  
  
-   Selecione um certificado da lista; o primeiro certificado não é a seleção padrão.  
  
#### <a name="clicking-the-dont-sign-button-causes-an-exception"></a>Clicar no botão "Logon não" faz com que uma exceção  
 Esse problema é um bug conhecido. Todos os [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifestos são deve ser assinado. Selecione uma das opções de assinatura e, em seguida, clique em **Okey**.  
  
## <a name="additional-errors"></a>Outros erros  
 A tabela a seguir mostra algumas mensagens de erro comuns que um usuário do computador cliente pode receber quando o usuário instala um [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativo. Cada mensagem de erro é listada ao lado de uma descrição do que a causa mais provável do erro.  
  
|Mensagem de erro|Descrição|  
|-------------------|-----------------|  
|Não é possível iniciar o aplicativo. Entre em contato com o Editor do aplicativo.<br /><br /> Não é possível iniciar o aplicativo. Para obter assistência, entre em contato com o fornecedor do aplicativo.|Essas são mensagens de erro genérico que ocorrem quando o aplicativo não pode ser iniciado e nenhum outro motivo específico pode ser encontrado. Geralmente isso significa que o aplicativo está corrompido de alguma forma, ou que o [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] repositório está corrompido.|  
|Não é possível continuar. O aplicativo está formatado incorretamente. Para obter assistência, entre em contato com o Editor do aplicativo.<br /><br /> Validação de aplicativo não teve êxito. Não é possível continuar.<br /><br /> Não é possível recuperar os arquivos de aplicativo. Arquivos corrompidos na implantação.|Um dos arquivos de manifesto da implantação sintaticamente não é válido ou contém um hash que não pode ser reconciliado com o arquivo correspondente. Esse erro também pode indicar que o manifesto inserido dentro de um assembly está corrompido. Crie novamente sua implantação e recompilar o aplicativo, ou localizar e corrigir os erros manualmente em seus manifestos.|  
|Não é possível recuperar o aplicativo. Erro de autenticação.<br /><br /> Instalação do aplicativo não teve êxito. Não é possível localizar arquivos de aplicativos no servidor. Entre em contato com o Editor do aplicativo ou o administrador para obter assistência.|Não não possível baixar um ou mais arquivos na implantação porque você não tem permissão para acessá-los. Isso pode ser causado por um erro proibido 403 sendo retornados por um servidor Web, que pode ocorrer se um dos arquivos na sua implantação termina com uma extensão que faz com que o servidor Web tratá-lo como um arquivo protegido. Além disso, um diretório que contém um ou mais dos arquivos do aplicativo pode exigir um nome de usuário e uma senha para acessar.|  
|Não é possível baixar o aplicativo. O aplicativo não tem arquivos necessários. Para obter assistência, contate o fornecedor do aplicativo ou o administrador do sistema.|Um ou mais dos arquivos listados no manifesto do aplicativo não podem ser encontrado no servidor. Verifique se você carregou arquivos dependentes de todos da implantação e tente novamente.|  
|Download do aplicativo não teve êxito. Verifique sua conexão de rede ou contate o administrador do sistema ou o provedor de serviços de rede.|[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]não é possível estabelecer uma conexão de rede para o servidor. Examine a disponibilidade do servidor e o estado da sua rede.|  
|URLDownloadToCacheFile falhou com HRESULT '\<número >'. Ocorreu um erro ao tentar baixar '\<arquivo >'.|Se um usuário tiver definido a opção de segurança avançada do Internet Explorer "Avisar ao alterar o modo de segurança" no computador de destino de implantação, e se a URL de instalação do aplicativo ClickOnce que está sendo instalado é redirecionada de não seguro para um site seguro (ou o contrário), a instalação falhará porque o aviso do Internet Explorer interrompe-lo.<br /><br /> Para resolver esse problema, você pode fazer o seguinte:<br /><br /> -Desmarque a opção de segurança.<br />-Certifique-se de que a URL de instalação não será redirecionada de forma que altera os modos de segurança.<br />-Remover o redirecionamento completamente e aponte para a URL de instalação atual.|  
|Ocorreu um erro gravar no disco rígido. Pode haver espaço suficiente disponível no disco. Para obter assistência, contate o fornecedor do aplicativo ou o administrador do sistema.|Isso pode indicar que o espaço em disco suficiente para armazenar o aplicativo, mas ele também pode indicar um erro de e/s mais geral quando você está tentando salvar os arquivos do aplicativo para a unidade.|  
|Não é possível iniciar o aplicativo. Não há espaço suficiente disponível no disco.|O disco rígido está cheio. Desmarque desativar espaço e tente executar o aplicativo novamente.|  
|Muitas ativações implantadas estão tentando carregar ao mesmo tempo.|[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]limita o número de diferentes aplicativos que podem ser iniciados ao mesmo tempo. Isso é basicamente para ajudar a proteger contra tentativas mal-intencionadas iniciar ataques de negação de serviço contra o local [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] serviço; os usuários que tente iniciar o mesmo aplicativo repetidamente em sucessão rápida, apenas acabará com uma única instância das aplicativo.|  
|Atalhos não podem ser ativados pela rede.|Atalhos para um [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativo só pode ser iniciado no disco rígido local. Eles não podem ser iniciados através da abertura de uma URL que aponta para um arquivo de atalho em um servidor remoto.|  
|O aplicativo é muito grande para ser executado online em confiança parcial. Para obter assistência, contate o fornecedor do aplicativo ou o administrador do sistema.|Um aplicativo executado em confiança parcial não pode ser maior do que a metade do tamanho da cota de aplicativo online, que por padrão é 250 MB.|  
  
## <a name="see-also"></a>Consulte também  
 [Segurança e implantação do ClickOnce](../deployment/clickonce-security-and-deployment.md)   
 [Solução de problemas de implantações ClickOnce](../deployment/troubleshooting-clickonce-deployments.md)