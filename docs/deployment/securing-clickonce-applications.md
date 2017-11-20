---
title: Protegendo aplicativos ClickOnce | Microsoft Docs
ms.custom: 
ms.date: 02/17/2017
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
- Windows applications, ClickOnce security
- ClickOnce deployment, security
- deploying applications, ClickOnce security
ms.assetid: a05b5f2f-d1f2-471a-8096-8b11f7554265
caps.latest.revision: "45"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: 331cdf8ddc449ea8d1d29af346b8f7faea549c00
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="securing-clickonce-applications"></a>Protegendo aplicativos ClickOnce
Os aplicativos [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] estão sujeitos às restrições de segurança de acesso a código no .NET Framework para ajudar a limitar o acesso que o código tem a recursos e operações protegidos. Por esse motivo, é importante compreender as implicações de segurança de acesso a código para desenvolver seus aplicativos [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] adequadamente. Seus aplicativos podem usar o modo Confiança Total ou zonas parciais, como as zonas da Internet e intranet, para limitar o acesso.  
  
 Além disso, o ClickOnce usa certificados para verificar a autenticidade do editor do aplicativo e assinar os manifestos do aplicativo e de implantação para provar que os arquivos não foram violados. Assinar é uma etapa opcional, o que facilita alterar os arquivos do aplicativo depois que os manifestos são gerados. No entanto, sem manifestos assinados, é difícil assegurar que o instalador do aplicativo não seja violado em ataques de segurança a intermediários. Por isso, recomendamos assinar seus manifestos do aplicativo e de implantação para ajudar a proteger seus aplicativos.  
  
## <a name="zones"></a>Zonas  
 Os aplicativos que são implantados usando a tecnologia [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] são restritos a um conjunto de permissões e ações definidas pela zona de segurança. As zonas de segurança são definidas no Internet Explorer e baseadas no local do aplicativo. A tabela a seguir lista as permissões padrão com base no local de implantação:  
  
|Local de implantação|Zona de segurança|  
|-------------------------|-------------------|  
|Executar da Web|Zona da Internet|  
|Instalar da Web|Zona da Internet|  
|Instalar do compartilhamento de arquivos de rede|Zona de Intranet Local|  
|Instalar de CD-ROM|Confiança Total|  
  
 As permissões padrão são baseadas no local do qual a versão original do aplicativo foi implantada; as atualizações para o aplicativo herdarão as permissões. Se o aplicativo estiver configurado para verificar se há atualizações de um local na Web ou rede e uma versão mais recente estiver disponível, a instalação original poderá receber permissões para a zona da Internet ou intranet em vez de permissões de confiança total. Para evitar solicitações aos usuários, um administrador de sistema poderá especificar uma política de implantação ClickOnce que defina um editor de aplicativos específico como uma fonte confiável. Para computadores nos quais esta política é implantada, as permissões serão concedidas automaticamente e o usuário não será interpelado. Para obter mais informações, consulte [Trusted Application Deployment Overview](../deployment/trusted-application-deployment-overview.md). Para configurar a implantação do aplicativo de confiança, o certificado poderá ser instalado no computador ou em nível corporativo. Para obter mais informações, consulte [como: adicionar um editor confiável para um computador cliente para aplicativos ClickOnce](../deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications.md).  
  
## <a name="code-access-security-policies"></a>Políticas de segurança de acesso a código  
 Permissões para um aplicativo são determinadas pelas configurações de [ \<trustInfo > elemento](../deployment/trustinfo-element-clickonce-application.md) elemento do manifesto do aplicativo. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]gera automaticamente essas informações com base nas configurações do projeto **segurança** página de propriedades. Um [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativo é concedido somente as permissões específicas que solicita a ele. Por exemplo, onde o acesso ao arquivo exige permissões de confiança total, se o aplicativo solicitar permissão de acesso a arquivos, ele receberá apenas permissão de acesso a arquivos, não permissões de confiança total. Ao desenvolver seu aplicativo [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], certifique-se de solicitar apenas as permissões específicas que o aplicativo precisa. Na maioria dos casos, você pode usar zonas da Internet ou intranet local para limitar seu aplicativo à confiança parcial. Para obter mais informações, consulte [como: definir uma zona de segurança para um aplicativo ClickOnce](../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md). Se seu aplicativo exigir permissões personalizadas, você poderá criar uma zona personalizada. Para obter mais informações, consulte [como: definir permissões personalizadas para um aplicativo ClickOnce](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md).  
  
 Incluir uma permissão que não faça parte do conjunto de permissões padrão para a zona da qual o aplicativo será implantado fará com que o usuário final seja solicitado a conceder permissão no momento da instalação ou atualização. Para evitar solicitações aos usuários, um administrador de sistema poderá especificar uma política de implantação ClickOnce que defina um editor de aplicativos específico como uma fonte confiável. Em computadores onde esta política é implantada, permissões serão concedidas automaticamente e o usuário não será interpelado.  
  
 Como um desenvolvedor, você é responsável por garantir que seu aplicativo seja executado com as permissões apropriadas. Se o aplicativo solicitar permissões fora de uma zona durante o tempo de execução, uma exceção de segurança poderá aparecer. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]permite que você depure seu aplicativo na zona de segurança de destino. e fornece ajuda para o desenvolvimento de aplicativos seguros. Para obter mais informações, consulte [como: depurar um aplicativo ClickOnce com permissões restritas](../deployment/how-to-debug-a-clickonce-application-with-restricted-permissions.md).  
  
 Para obter mais informações sobre a segurança de acesso do código e ClickOnce, consulte [Code Access Security para aplicativos ClickOnce](../deployment/code-access-security-for-clickonce-applications.md).  
  
## <a name="code-signing-certificates"></a>Certificados de assinatura de código  
 Para publicar um aplicativo usando a implantação de [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], você pode assinar os manifestos do aplicativo e de implantação para o aplicativo ao usar um par de chaves pública/privada. As ferramentas para assinar um manifesto estão disponíveis no **assinatura** página do **Project Designer**. Para obter mais informações, consulte [página de assinatura, Designer de projeto](../ide/reference/signing-page-project-designer.md). Como alternativa, você pode assinar os manifestos com um arquivo de chave durante o processo de publicação, usando o Assistente de publicação.  
  
 Depois que os manifestos são assinados, as informações do editor baseadas na assinatura Authenticode serão exibidas para o usuário na caixa de diálogo de permissões durante a instalação, para mostrar que o aplicativo é oriundo de uma fonte confiável.  
  
 Para obter mais informações sobre ClickOnce e certificados, consulte [ClickOnce e Authenticode](../deployment/clickonce-and-authenticode.md).  
  
## <a name="aspnet-form-based-authentication"></a>Autenticação baseada em formulários ASP.NET  
 Se você desejar controlar quais implantações cada usuário pode acessar, não habilite acesso anônimo aos aplicativos [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] implantados em um servidor Web. Em vez disso, habilite acesso de usuários às implantações instaladas com base em uma identidade de usuário usando a autenticação do Windows.  
  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] não oferece suporte à autenticação baseada em formulários ASP.NET, pois ela usa cookies persistentes; eles representam um risco à segurança porque residem no cache do Internet Explorer e podem ser violados. Portanto, se você estiver implantando aplicativos [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], não haverá suporte a qualquer cenário de autenticação além da autenticação do Windows.  
  
## <a name="passing-arguments"></a>Passando argumentos  
 Uma consideração adicional sobre segurança ocorrerá se você tiver que passar argumentos para um aplicativo [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]os desenvolvedores podem fornecer uma cadeia de caracteres de consulta para aplicativos implantados pela Web. A cadeia de caracteres de consulta assume a forma de uma série de pares nome-valor no fim da URL utilizada para iniciar o aplicativo:  
  
 `http://servername.adatum.com/WindowsApp1.application?username=joeuser`  
  
 Por padrão, os argumentos da cadeia de caracteres de consulta estão desabilitados. Para habilitá-los, o atributo `trustUrlParameters` deverá ser definido no manifesto de implantação do aplicativo. Esse valor pode ser definido de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] e MageUI.exe. Para obter etapas detalhadas sobre como habilitar passar cadeias de caracteres de consulta, consulte [como: recuperar informações de cadeia de caracteres de consulta em um aplicativo ClickOnce Online](../deployment/how-to-retrieve-query-string-information-in-an-online-clickonce-application.md).  
  
 Você nunca deve passar argumentos recuperados por meio de uma cadeia de caracteres de consulta a um banco de dados ou linha de comando sem verificar os argumentos para garantir que eles sejam seguros. Os argumentos inseguros são os que incluem caracteres de escape da linha de comando ou banco de dados que poderiam permitir que um usuário mal-intencionado manipulasse o seu aplicativo e executasse comandos arbitrários.  
  
> [!NOTE]
>  Os argumentos de cadeia de caracteres de consulta são a única maneira de passar argumentos para um aplicativo [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] na inicialização. Você não pode passar argumentos para um [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativos de linha de comando.  
  
## <a name="deploying-obfuscated-assemblies"></a>Implantando assemblies ofuscados  
 O Visual Studio inclui a versão gratuita [proteção preemptivo - Dotfuscator Community Edition](../ide/dotfuscator/index.md), que você pode usar para proteger seus aplicativos ClickOnce por meio de ofuscação de código e as medidas de proteção ativa.  Para obter detalhes, consulte [seção ClickOnce do guia do usuário Dotfuscator Community Edition](https://www.preemptive.com/dotfuscator/ce/docs/help/5.27/advanced_clickonce.html).

## <a name="see-also"></a>Consulte também  
 [Segurança e implantação do ClickOnce](../deployment/clickonce-security-and-deployment.md)   
 [Escolhendo uma estratégia de implantação do ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md)