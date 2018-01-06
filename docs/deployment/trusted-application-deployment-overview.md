---
title: Trusted Application Deployment Overview | Microsoft Docs
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
- ClickOnce deployment, install without prompting
- ClickOnce deployment, security
- trusted application deployment
ms.assetid: b24a1702-8fbe-45b1-87a0-9618a0708f1d
caps.latest.revision: "31"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload: multiple
ms.openlocfilehash: 34e83d6b035ba6ea91190fa89b9e1a63366e7907
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="trusted-application-deployment-overview"></a>Visão geral da implantação de aplicativos confiáveis
Este tópico fornece uma visão geral de como implantar [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativos que têm permissões elevadas usando a tecnologia de implantação de aplicativos confiáveis.  
  
 Confiável parte da implantação do aplicativo a [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] tecnologia de implantação, torna mais fácil para organizações de qualquer tamanho para conceder permissões adicionais para um aplicativo gerenciado de maneira mais segura e mais segura sem nenhum aviso ao usuário. Implantação do aplicativo confiável, uma organização pode configurar apenas um computador cliente para ter uma lista de fornecedores confiáveis, que são identificados com o uso de certificados do Authenticode. Depois disso, qualquer [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativo assinado por um destes confiável Publicadores recebe um nível mais alto de confiança.  
  
> [!NOTE]
>  Confiável a que implantação de aplicativo requer a configuração do computador do usuário. Em ambientes de área de trabalho gerenciados, essa configuração pode ser executada por meio da política global. Se este for não o que você deseja para seu aplicativo, use elevação de permissões. Para obter mais informações, consulte [Securing ClickOnce Applications](../deployment/securing-clickonce-applications.md) (Protegendo aplicativos ClickOnce).  
  
## <a name="trusted-application-deployment-basics"></a>Noções básicas sobre a implantação do aplicativo confiável  
 A tabela a seguir mostra os objetos e as funções que estão envolvidas na implantação de aplicativos confiáveis.  
  
|Objeto ou função|Descrição|  
|--------------------|-----------------|  
|Administrador|A entidade organizacional responsável por atualizar e manter os computadores cliente|  
|Gerenciador de confiança|O subsistema dentro o common language runtime (CLR) responsável pela aplicação de segurança do aplicativo cliente.|  
|Publicador|A entidade que grava e mantém o aplicativo.|  
|implantador|A entidade que pacotes e distribui o aplicativo para usuários.|  
|certificado|Uma assinatura criptográfica que consiste em uma chave pública e privada; geralmente é emitido por uma autoridade de certificação (CA) que pode comprovar a autenticidade.|  
|Certificado Authenticode|Um certificado com os metadados inseridos descrever, entre outras coisas, os usos para o qual o certificado pode ser empregado.|  
|autoridade de certificação|Uma organização que verifica a identidade de editores e emite os certificados são inseridos com metadados do publicador.|  
|autoridade raiz|Uma autoridade de certificação que autoriza a outras autoridades de certificação para emitir certificados.|  
|contêiner de chave|Um espaço de armazenamento lógico no Microsoft Windows para o armazenamento de certificados.|  
|editores confiáveis|Um publicador cujo certificado Authenticode foi adicionado a uma lista de certificados confiáveis (CTL) em um computador cliente.|  
  
 Em organizações maiores, o publicador e o implantador são frequentemente duas entidades separadas:  
  
-   O publicador é o grupo que cria o [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativo.  
  
-   O implantador é o grupo, normalmente o departamento de TI (tecnologia) de informações, que distribui [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativo para computadores desktop corporativos.  
  
 Você deve seguir estas etapas para tirar proveito da implantação de aplicativos confiáveis:  
  
1.  Obter um certificado para o publicador.  
  
2.  Adicione o publicador para o repositório de editores confiáveis em todos os clientes.  
  
3.  Criar seu [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativo.  
  
4.  Assinar o manifesto de implantação com o certificado do Editor.  
  
5.  Publica a implantação do aplicativo em computadores cliente.  
  
### <a name="obtain-a-certificate-for-the-publisher"></a>Obter um certificado para o publicador  
 Certificados digitais são um componente principal do sistema de segurança e autenticação do Microsoft Authenticode. Authenticode é uma parte padrão do sistema operacional Windows. Todos os [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativos devem ser assinados com um certificado digital, independentemente se eles participarem de implantação de aplicativos confiáveis. Para obter uma explicação completa de como funciona com o Authenticode [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], consulte [ClickOnce e Authenticode](../deployment/clickonce-and-authenticode.md).  
  
### <a name="add-the-publisher-to-the-trusted-publishers-store"></a>Adicionar o publicador para o repositório de editores confiáveis  
 Para sua [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativo receber um nível mais alto de confiança, você deve adicionar o certificado como um editor confiável para cada computador cliente no qual o aplicativo será executado. Para executar essa tarefa é uma configuração única. Depois de concluído, você pode implantar tantas [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativos assinados com um certificado de editor conforme desejado, e eles serão executados com confiança alta.  
  
 Se você estiver implantando seu aplicativo em um ambiente de área de trabalho gerenciado; Por exemplo, uma intranet corporativa executando o sistema operacional Windows; Você pode adicionar editores confiáveis ao armazenamento do cliente, criando uma nova lista de certificados confiáveis (CTL) com a política de grupo. Para obter mais informações, consulte [criar uma lista de certificados confiáveis para um objeto de diretiva de grupo](http://go.microsoft.com/fwlink/?LinkId=102576).  
  
 Se você não estiver implantando seu aplicativo em um ambiente de área de trabalho gerenciado, você tem as seguintes opções para adicionar um certificado ao repositório de editores confiáveis:  
  
-   O <xref:System.Security.Cryptography?displayProperty=fullName> namespace.  
  
-   CertMgr.exe, que é um componente do Internet Explorer e, portanto, existe no Windows 98 e todas as versões posteriores. Para obter mais informações, consulte [Certmgr.exe (ferramenta de Gerenciador de certificados)](/dotnet/framework/tools/certmgr-exe-certificate-manager-tool).  
  
### <a name="create-a-clickonce-application"></a>Criar um aplicativo ClickOnce  
 Um [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativo é um [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] aplicativo cliente combinado com os arquivos de manifesto que descrevem o aplicativo e fornecem os parâmetros de instalação. Você pode ativar o seu programa em um [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativo usando o **publicar** do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Como alternativa, você pode gerar todos os arquivos necessários para [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] implantação usando ferramentas que acompanham o [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)]. Para obter etapas detalhadas sobre [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] implantação, consulte [passo a passo: Implantando manualmente um aplicativo ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).  
  
 Implantação de aplicativo confiável é específica para [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]e só pode ser usado com [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativos.  
  
### <a name="sign-the-deployment"></a>Assinar a implantação  
 Depois de obter seu certificado, você deve usar para assinar sua implantação. Se você estiver implantando seu aplicativo usando o [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Assistente de publicação, o assistente gerará automaticamente um certificado de teste para você se você não especificou um certificado por conta própria. Você também pode usar o [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] janela do Designer de projeto, no entanto, para fornecer um certificado fornecido por uma autoridade de certificação.  Também consulte [como: publicar um aplicativo ClickOnce usando o Assistente de publicação] (http://msdn.microsoft.com/library/31kztyey\(v=vs.110\).  
  
> [!CAUTION]
>  Não é recomendável que o aplicativo ser implantado com um certificado de teste.  
  
 Você também pode assinar o aplicativo usando as ferramentas de Mage.exe ou MageUI.exe SDK. Para obter mais informações, consulte [passo a passo: Implantando manualmente um aplicativo ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md). Para obter uma lista completa das opções de linha de comando relacionadas à implantação de assinatura, consulte [Mage.exe (ferramenta de edição e geração de manifesto)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool).  
  
### <a name="publish-the-application"></a>Publicar o aplicativo  
 Assim que você entrar com sua [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifestos, o aplicativo está pronto para publicar em seu local de instalação. O local de instalação pode ser um servidor Web, um compartilhamento de arquivos ou no disco local. Quando um cliente acessa o manifesto de implantação pela primeira vez, o Gerenciador de confiança deve escolher se o [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativo tenha autoridade ou não seja executado em um nível mais alto de confiança por instalado confiável publicador. O Gerenciador de confiança faz esta escolha comparando o certificado usado para assinar a implantação com os certificados armazenados em um editor confiável do cliente armazenar. Se o Gerenciador de confiança encontrar uma correspondência, o aplicativo é executado com confiança alta.  
  
## <a name="trusted-application-deployment-and-permission-elevation"></a>Implantação de aplicativos confiáveis e elevação de permissão  
 Se o publicador atual não é um fornecedor confiável, o Gerenciador de confiança usará elevação de permissão para consultar o usuário sobre se ele deseja conceder que permissões elevadas do seu aplicativo. No entanto, se a elevação de permissões é desabilitada pelo administrador, o aplicativo não é possível obter permissão para executar. O aplicativo não será executado e nenhuma notificação será exibida ao usuário. Para obter mais informações sobre a elevação de permissões, consulte [proteger os aplicativos ClickOnce](../deployment/securing-clickonce-applications.md).  
  
## <a name="limitations-of-trusted-application-deployment"></a>Limitações de implantação de aplicativos confiáveis  
 Você pode usar a implantação de aplicativos confiáveis para conceder confiança elevada para [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativos implantados pela Web ou por meio de um compartilhamento de arquivos da empresa. Você não precisa usar a implantação de aplicativos confiáveis para [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativos distribuídos em um CD, porque, por padrão, esses aplicativos são concedidos confiança total.  
  
## <a name="see-also"></a>Consulte também  
 [Mage.exe (Manifest Generation and Editing Tool)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)   
 [Passo a passo: implantando um aplicativo ClickOnce manualmente](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)
