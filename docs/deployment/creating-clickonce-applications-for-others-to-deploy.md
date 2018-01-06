---
title: "Criando aplicativos ClickOnce para que outros usuários para implantar | Microsoft Docs"
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
- preserved branding information
- useManifestForTrust element
- customer deployments [ClickOnce]
- multiple ClickOnce deployment and branding
- ClickOnce applications, previous .NET Framework versions
- application manifests [ClickOnce]
- <useManifestForTrust> element
- manifests [ClickOnce]
- trust applications, ClickOnce
- ClickOnce applications, deployed by others
- ClickOnce applications, previous .NET Framework
ms.assetid: d20766c7-4ef3-45ab-8aa0-3f15b61eccaa
caps.latest.revision: "10"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload: multiple
ms.openlocfilehash: d3a9762872f74b39d8cef387703488c01647dbcc
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="creating-clickonce-applications-for-others-to-deploy"></a>Criando aplicativos ClickOnce para a implantação por terceiros
Nem todos os desenvolvedores que estão criando as implantações do ClickOnce planeja implantar os próprios aplicativos. Muitas delas basta empacotar seu aplicativo usando o ClickOnce e entregar os arquivos para um cliente, como uma grande empresa. O cliente torna-se de um responsável para hospedar o aplicativo em sua rede. Este tópico discute alguns dos problemas inerentes essas implantações em versões do .NET Framework anteriores à versão 3.5. Em seguida, descreve uma nova solução fornecida usando o novo recurso de "usar o manifesto de confiança" no .NET Framework 3.5. Finalmente, ele conclui com estratégias recomendadas para a criação de implantações do ClickOnce para clientes que ainda estão usando versões mais antigas do .NET Framework.  
  
## <a name="issues-involved-in-creating-deployments-for-customers"></a>Problemas envolvidos na criação de implantações para clientes  
 Vários problemas ocorrem quando você planeja fornecer uma implantação de um cliente. O primeiro problema relacionado a assinatura de código. Para ser implantado em uma rede, o manifesto de implantação e o manifesto do aplicativo de uma implantação de ClickOnce devem ambos ser assinados com um certificado digital. Isso gera a pergunta de se usar o certificado do desenvolvedor ou o certificado do cliente ao assinar os manifestos.  
  
 A questão de qual certificado usar é crítica, como a identidade de um aplicativo ClickOnce baseia-se a assinatura digital do manifesto de implantação. Se o desenvolvedor fizer o manifesto de implantação, isso pode levar a conflitos se o cliente é uma grande empresa, e mais de uma divisão da empresa implanta uma versão personalizada do aplicativo.  
  
 Por exemplo, digamos que a Adventure Works tem um departamento de finanças e um departamento de recursos humanos. Ambos os departamentos de licença um aplicativo ClickOnce da Microsoft Corporation, que gera relatórios de dados armazenados em um banco de dados SQL. A Microsoft fornece cada departamento com uma versão do aplicativo que é personalizado para seus dados. Se os aplicativos são assinados com o mesmo certificado Authenticode, um usuário que tenta usar ambos os aplicativos encontra um erro, como o ClickOnce considere o segundo aplicativo como sendo idêntico ao primeiro. Nesse caso, o cliente pode apresentar efeitos colaterais indesejáveis e imprevisíveis que incluem a perda dos dados armazenados localmente pelo aplicativo.  
  
 Um problema adicional relacionado à assinatura de código é o `deploymentProvider` elemento no manifesto de implantação, que informa o ClickOnce onde procurar atualizações do aplicativo. Esse elemento deve ser adicionado ao manifesto de implantação antes de assiná-lo. Se esse elemento for adicionado posteriormente, o manifesto de implantação deve ser assinado novamente.  
  
### <a name="requiring-the-customer-to-sign-the-deployment-manifest"></a>Necessidade do cliente assinar o manifesto de implantação  
 Uma solução para esse problema de implantações não exclusivo é ter o sinal de desenvolvedor o manifesto do aplicativo e o cliente assinar o manifesto de implantação. Embora essa abordagem funciona, ele apresenta outros problemas. Como um certificado Authenticode deve permanecer um ativo protegido, o cliente não pode dar apenas o certificado para o desenvolvedor para entrar a implantação. Enquanto o cliente pode assinar o manifesto de implantação próprios usando ferramentas disponíveis gratuitamente com o .NET Framework SDK, isso pode exigir conhecimento técnico mais que o cliente está disposto ou é capaz de fornecer. Nesses casos, o desenvolvedor geralmente cria um aplicativo, site da Web ou outro mecanismo pelo qual o cliente pode enviar sua versão do aplicativo para a assinatura.  
  
### <a name="the-impact-of-customer-signing-on-clickonce-application-security"></a>O impacto de segurança do aplicativo ClickOnce de assinatura de cliente  
 Mesmo que o desenvolvedor e o cliente concordam que o cliente deve assinar o manifesto de aplicativo, isso gera outras questões que envolvem a identidade do aplicativo, especialmente à medida que ele se aplica a implantação de aplicativos confiáveis. (Para obter mais informações sobre esse recurso, consulte [Trusted Application Deployment Overview](../deployment/trusted-application-deployment-overview.md).) Digamos que a Adventure Works quer configurar seus computadores cliente para que qualquer aplicativo fornecido a ele pela Microsoft Corporation seja executado com confiança total. Se a Adventure Works assina o manifesto de implantação, o ClickOnce usará assinatura de segurança do grupo de trabalho da Adventure para determinar o nível de confiança do aplicativo.  
  
## <a name="creating-customer-deployments-by-using-application-manifest-for-trust"></a>Criação de implantações de clientes usando o manifesto do aplicativo para a relação de confiança  
 ClickOnce no .NET Framework 3.5 contém um novo recurso que oferece uma nova solução a desenvolvedores e clientes para o cenário de como os manifestos devem ser assinados. O manifesto do aplicativo ClickOnce oferece suporte a um novo elemento chamado `<useManifestForTrust>` que permite que um desenvolvedor indicar que a assinatura digital do manifesto do aplicativo é o que deve ser usado para tomar decisões de confiança. O desenvolvedor usa ferramentas de empacotamento do ClickOnce — como Mage.exe, MageUI.exe e Visual Studio — incluem esse elemento no manifesto do aplicativo, bem como para inserir o nome do publicador e o nome do aplicativo no manifesto.  
  
 Ao usar `<useManifestForTrust>`, o manifesto de implantação não precisa ser assinado com um certificado Authenticode emitido por uma autoridade de certificação. Em vez disso, ele pode ser assinado com o que é conhecido como um certificado autoassinado. Um certificado autoassinado é gerado pelo cliente ou o desenvolvedor usando ferramentas padrão do .NET Framework SDK e, em seguida, aplicado ao manifesto de implantação usando as ferramentas de implantação do ClickOnce padrão. Para obter mais informações, consulte [MakeCert](https://msdn.microsoft.com/library/windows/desktop/aa386968.aspx).  
  
 Usar um certificado autoassinado para o manifesto de implantação apresenta várias vantagens. Eliminando a necessidade do cliente obter ou criar seu próprio certificado Authenticode, `<useManifestForTrust>` simplifica a implantação do cliente, permitindo que o desenvolvedor manter sua própria identidade de identidade visual do aplicativo. O resultado é um conjunto de implantações assinados que são mais seguros e ter identidades de aplicativo único. Isso elimina o conflito potencial que pode ocorrer de implantar o mesmo aplicativo em vários clientes.  
  
 Para obter informações passo a passo sobre como criar uma implantação de ClickOnce com `<useManifestForTrust>` habilitado, consulte [passo a passo: Implantando manualmente um aplicativo ClickOnce que Does não exigem assinando novamente e preserva a identidade visual informações](../deployment/walkthrough-manually-deploying-a-clickonce-application-that-does-not-require-re-signing-and-that-preserves-branding-information.md).  
  
### <a name="how-application-manifest-for-trust-works-at-runtime"></a>Manifesto de aplicativo como para confiança funciona em tempo de execução  
 Para obter um melhor entendimento de como usar o manifesto do aplicativo para confiança funciona em tempo de execução, considere o exemplo a seguir. Um aplicativo ClickOnce que tem como alvo o .NET Framework 3.5 é criado pela Microsoft. O manifesto do aplicativo usa o `<useManifestForTrust>` elemento e é assinada pela Microsoft. A Adventure Works assina o manifesto de implantação usando um certificado autoassinado. Adventure Works, os clientes são configurados para confiar em qualquer aplicativo assinado pela Microsoft.  
  
 Quando um usuário clica em um link para o manifesto de implantação, o ClickOnce instala o aplicativo no computador do usuário. As informações de certificado e implantação identificar com exclusividade o aplicativo ClickOnce no computador cliente. Se o usuário tentar instalar novamente o mesmo aplicativo de um local diferente, o ClickOnce pode usar essa identidade para determinar se o aplicativo já existe no cliente.  
  
 Em seguida, o ClickOnce examina o certificado Authenticode que é usado para assinar o manifesto do aplicativo, que determina o nível de confiança que concederá ClickOnce. Desde que a Adventure Works tiver configurado seus clientes para confiar em qualquer aplicativo assinado pela Microsoft, este aplicativo ClickOnce é concedido confiança total. Para obter mais informações, consulte [Trusted Application Deployment Overview](../deployment/trusted-application-deployment-overview.md).  
  
## <a name="creating-customer-deployments-for-earlier-versions"></a>Criar implantações para clientes de versões anteriores  
 Se um desenvolvedor é implantando aplicativos ClickOnce para clientes que estão usando versões mais antigas do .NET Framework? As seções a seguir resumem várias soluções recomendadas, junto com as vantagens e desvantagens de cada um.  
  
### <a name="sign-deployments-on-behalf-of-customer"></a>Implantações de entrada em nome do cliente  
 É uma estratégia de implantação possíveis para o desenvolvedor criar um mecanismo para implantações em nome dos seus clientes, se conectar usando a chave privada do cliente. Isso impede que o desenvolvedor de ter que gerenciar chaves particulares ou vários pacotes de implantação. O desenvolvedor fornece apenas da mesma implantação para cada cliente. Cabe ao cliente para personalizá-la para seu ambiente usando o serviço de autenticação.  
  
 Uma desvantagem desse método é o tempo e as despesas que são necessárias para implementá-la. Enquanto um serviço pode ser criado usando as ferramentas fornecidas no SDK do .NET Framework, ele adicionará mais tempo de desenvolvimento para o ciclo de vida do produto.  
  
 Conforme observado anteriormente neste tópico, outra desvantagem é que a versão do cliente do aplicativo terá a mesma identidade de aplicativo, que pode levar a conflitos. Se isso for uma preocupação, o desenvolvedor pode alterar o campo de nome é usado ao gerar o manifesto de implantação para fornecer um nome exclusivo a cada aplicativo. Isso criará uma identidade separada para cada versão do aplicativo e eliminar qualquer conflito potencial de identidade. Este campo corresponde ao `-Name` argumento para Mage.exe e o **nome** campo o **nome** guia MageUI.exe.  
  
 Por exemplo, digamos que o desenvolvedor tenha criado um aplicativo chamado Application1. Em vez de criar uma única implantação com o campo de nome definido como Application1, o desenvolvedor pode criar várias implantações com uma variação específicas do cliente, esse nome, como Application1-CustomerA, Application1-CustomerB e assim por diante.  
  
### <a name="deploy-using-a-setup-package"></a>Implantar usando um pacote de instalação  
 Uma estratégia de implantação possíveis segundo é gerar um projeto Microsoft Setup para realizar a implantação inicial do aplicativo ClickOnce. Isso pode ser fornecida em um dos vários formatos diferentes: como uma implantação de MSI, como um executável de instalação (. EXE), ou como um arquivo de gabinete (. cab) junto com um script em lotes.  
  
 Usando essa técnica, o desenvolvedor deve fornecer ao cliente uma implantação que inclui os arquivos do aplicativo, o manifesto do aplicativo e um manifesto de implantação que serve como um modelo. O cliente deve executar o programa de instalação, que solicitará-los para uma URL de implantação (o servidor ou local do qual usuários instalem o aplicativo ClickOnce do compartilhamento de arquivo), bem como um certificado digital. O aplicativo de instalação também pode optar por solicitar opções adicionais de configuração de ClickOnce, como o intervalo de verificação de atualização. Depois que essas informações são reunidas, o programa de instalação deve gerar o manifesto de implantação real, assiná-lo e publicar o aplicativo ClickOnce para o local de servidor designado.  
  
 Há três maneiras que o cliente pode assinar o manifesto de implantação nessa situação:  
  
1.  O cliente pode usar um certificado válido emitido por uma autoridade de certificação (CA).  
  
2.  Como uma variação nessa abordagem, o cliente pode escolher assinar seu manifesto de implantação com um certificado autoassinado. A desvantagem é que ela fará com que o aplicativo exibir as palavras "Editor desconhecido" quando o usuário é consultado se deseja instalá-lo. No entanto, a vantagem é que ela impede que clientes menores gastar tempo e dinheiro necessário para um certificado emitido por uma autoridade de certificação.  
  
3.  Por fim, o desenvolvedor pode incluir seu próprio certificado autoassinado no pacote de instalação. Isso introduz os possíveis problemas com a identidade de aplicativo abordados neste tópico.  
  
 A desvantagem do método de projeto de implantação de instalação é o tempo e as despesas exigidos para criar um aplicativo de implantação personalizada.  
  
### <a name="have-customer-generate-deployment-manifest"></a>Ter o cliente gerar manifesto de implantação  
 Uma estratégia de implantação possíveis terceira está manualmente apenas os arquivos de aplicativo e o manifesto do aplicativo desativado para o cliente. Nesse cenário, o cliente é responsável por usar o SDK do .NET Framework para gerar e assinar o manifesto de implantação.  
  
 A desvantagem desse método é que ele requer que o cliente para instalar as ferramentas do SDK do .NET Framework e ter um desenvolvedor ou administrador do sistema que é qualificada para usá-los. Alguns clientes podem exigir uma solução que requer pouco ou nenhum esforço técnico de sua parte.  
  
## <a name="see-also"></a>Consulte também  
 [Implantando aplicativos ClickOnce para teste e os servidores de produção sem assinar novamente](../deployment/deploying-clickonce-applications-for-testing-and-production-servers-without-resigning.md)   
 [Walkthrough: Manually Deploying a ClickOnce Application](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)  (Instruções passo a passo: implantando manualmente um aplicativo ClickOnce)  
 [Passo a passo: implantando manualmente um aplicativo ClickOnce que não requer nova assinatura e que preserva informações de identidade visual](../deployment/walkthrough-manually-deploying-a-clickonce-application-that-does-not-require-re-signing-and-that-preserves-branding-information.md)