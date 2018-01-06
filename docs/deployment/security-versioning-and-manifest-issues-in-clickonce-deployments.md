---
title: "Segurança, controle de versão e problemas de manifesto em implantações do ClickOnce | Microsoft Docs"
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
- versioning, ClickOnce applications
- ClickOnce applications, Windows Vista User Account Control
- ClickOnce applications, versioning issues
- security, ClickOnce applications
- Windows 7, ClickOnce deployments
- ClickOnce applications, manifest issues
- User Account Control, ClickOnce applications
- Windows Vista, ClickOnce deployments
- manifests [ClickOnce]
- ClickOnce applications, security issues
ms.assetid: d5d0c90b-ac1a-44e2-88dc-0d0ffd881624
caps.latest.revision: "21"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload: multiple
ms.openlocfilehash: 53f9c0114573c6f08a2d9219e4dd2028ffe9ac7c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="security-versioning-and-manifest-issues-in-clickonce-deployments"></a>Problemas de segurança, controle de versão e manifesto em implantações do ClickOnce
Há uma variedade de problemas com [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] segurança, controle de versão do aplicativo e manifesto sintaxe e semântica que pode causar um [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] implantação não seja bem-sucedida.  
  
## <a name="clickonce-and-windows-vista-user-account-control"></a>ClickOnce e controle de conta de usuário do Windows Vista  
 Em [!INCLUDE[windowsver](../deployment/includes/windowsver_md.md)], por padrão, aplicativos executem como um usuário padrão, mesmo se o usuário atual está conectado com uma conta que tenha permissões de administrador. Se um aplicativo deve executar uma ação que requer permissões de administrador, ele informa o sistema operacional, que, em seguida, solicita que o usuário insira suas credenciais de administrador. Esse recurso, que é chamado controle de conta de usuário (UAC), impede que aplicativos façam alterações que podem afetar todo o sistema operacional sem aprovação explícita do usuário. Aplicativos do Windows declarar que exigem elevação Essa permissão, especificando o `requestedExecutionLevel` atributo o `trustInfo` seção de manifesto do aplicativo.  
  
 Devido ao risco de expor os aplicativos a ataques de elevação de segurança, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativos não é possível solicitar a elevação de permissão se o UAC estiver ativado para o cliente. Qualquer [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativo que tenta definir seu `requestedExecutionLevel` atributo `requireAdministrator` ou `highestAvailable` não será instalado em [!INCLUDE[windowsver](../deployment/includes/windowsver_md.md)].  
  
 Em alguns casos, seu [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativo pode tentar executar com permissões de administrador devido a lógica de detecção do instalador em [!INCLUDE[windowsver](../deployment/includes/windowsver_md.md)]. Nesse caso, você pode definir o `requestedExecutionLevel` atributo no manifesto do aplicativo para `asInvoker`. Isso fará com que o aplicativo seja executado sem elevação. [!INCLUDE[vs_orcas_long](../debugger/includes/vs_orcas_long_md.md)]adiciona automaticamente esse atributo para todos os manifestos de aplicativo.  
  
 Se você estiver desenvolvendo um aplicativo que requer permissões de administrador para todo o tempo de vida do aplicativo, considere a possibilidade de implantar o aplicativo usando a tecnologia Windows Installer (MSI) em vez disso. Para obter mais informações, consulte [Noções básicas do Windows Installer](../extensibility/internals/windows-installer-basics.md).  
  
## <a name="online-application-quotas-and-partial-trust-applications"></a>Aplicativos de confiança parcial e cotas do aplicativo online  
 Se seu [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativo é executada online, em vez de por meio de uma instalação, ele deverá ser adequada a cota reservou para aplicativos online. Além disso, um aplicativo de rede que é executado em confiança parcial, como com um conjunto restrito de permissões de segurança, não pode ser maior do que a metade do tamanho da cota.  
  
 Para obter mais informações e instruções sobre como alterar a cota do aplicativo online, consulte [visão geral de Cache do ClickOnce](../deployment/clickonce-cache-overview.md).  
  
## <a name="versioning-issues"></a>Problemas de controle de versão  
 Você pode enfrentar problemas se você atribuir nomes fortes ao seu assembly e aumente o número de versão do assembly para refletir uma atualização do aplicativo. Qualquer assembly compilado com uma referência a um assembly de nome forte deve próprio ser recompilado ou o assembly tentará fazer referência à versão mais antiga. O assembly fará isso porque o assembly está usando o valor antigo da versão em sua solicitação de associação.  
  
 Por exemplo, digamos que você tenha um assembly de nome forte em seu próprio projeto com versão 1.0.0.0. Depois de compilar o assembly, adicione-o como uma referência ao projeto que contém o aplicativo principal. Se você atualizar o assembly, incrementa a versão 1.0.0.1 e tenta implantá-lo sem também recompilar o aplicativo, o aplicativo não poderá carregar o assembly em tempo de execução.  
  
 Esse erro pode ocorrer somente se você estiver editando o [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifestos manualmente; você não deverá ter esse erro se você gerar sua implantação usando [!INCLUDE[vsprvslong](../code-quality/includes/vsprvslong_md.md)].  
  
## <a name="specifying-individual-net-framework-assemblies-in-the-manifest"></a>Especificando Assemblies individuais do .NET Framework no manifesto  
 O aplicativo falhará ao carregar se você tiver editado manualmente um [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] implantação para fazer referência a uma versão mais antiga de um [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] assembly. Por exemplo, se você adicionou uma referência ao assembly System.Net para obter uma versão de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] antes da versão especificada no manifesto, em seguida, um erro ocorrerá. Em geral, você não deve tentar especificar referências a pessoa [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] assemblies, como a versão do [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] em que seu aplicativo é executado é especificado como uma dependência no manifesto do aplicativo.  
  
## <a name="manifest-parsing-issues"></a>Problemas de análise de manifesto  
 Os arquivos de manifesto que são usados por [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] são arquivos XML e devem ser bem formado e válido: eles devem obedecer as regras de sintaxe XML e usar apenas os elementos e atributos definidos no esquema XML relevante.  
  
 Algo que pode causar problemas em um arquivo de manifesto é selecionar um nome para seu aplicativo que contém um caractere especial, como aspas simples ou duplas. O nome do aplicativo é parte de seu [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] identidade. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]no momento não analisar as identidades que contenham caracteres especiais. Se seu aplicativo não ativar, certifique-se de que você está usando somente alfabéticos e numéricos para o nome e tenta implantá-lo novamente.  
  
 Se você tiver editado manualmente seus manifestos de implantação ou aplicativo, você pode ter acidentalmente corrompida-los. Manifesto corrompido impedirá um correto [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] instalação. Você pode depurar esses erros em tempo de execução clicando **detalhes** no **erro ClickOnce** caixa de diálogo e ler a mensagem de erro no log. O log lista uma das seguintes mensagens:  
  
-   Uma descrição do erro de sintaxe e o número de linha e caractere posição onde ocorreu o erro.  
  
-   O nome de um elemento ou atributo usado em violação do esquema do manifesto. Se você tiver adicionado o XML manualmente para seus manifestos, você precisará comparar seu adições para os esquemas de manifesto. Para obter mais informações, consulte [manifesto de implantação do ClickOnce](../deployment/clickonce-deployment-manifest.md) e [manifesto do aplicativo ClickOnce](../deployment/clickonce-application-manifest.md).  
  
-   Um conflito de ID. Referências de dependência nos manifestos de aplicativo e implantação devem ser exclusivas no seu `name` e `publicKeyToken` atributos. Se ambos os atributos correspondam entre quaisquer dois elementos dentro de um manifesto, análise de manifesto não terá êxito.  
  
## <a name="precautions-when-manually-changing-manifests-or-applications"></a>Precauções ao alterar manualmente os manifestos ou aplicativos  
 Quando você atualiza um manifesto de aplicativo, você deve assinar novamente o manifesto do aplicativo e o manifesto de implantação. O manifesto de implantação contém uma referência para o manifesto do aplicativo que inclui o hash do arquivo e sua assinatura digital.  
  
### <a name="precautions-with-deployment-provider-usage"></a>Precauções com o uso do provedor de implantação  
 O [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] o manifesto de implantação tem um `deploymentProvider` propriedade que aponta para o caminho completo do local de onde o aplicativo deve ser instalado e atendido:  
  
```  
<deploymentProvider codebase="http://myserver/myapp.application" />  
```  
  
 Esse caminho é definido quando [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] cria o aplicativo e é obrigatória para aplicativos instalados. O caminho aponta para o local padrão onde o [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] installer instalará o aplicativo e a procura por atualizações. Se você usar o **xcopy** comando para copiar um [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativo para um local diferente, mas não alterar o `deploymentProvider` propriedade [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] ainda farão referência volta para o local original quando ele tenta baixar o aplicativo.  
  
 Se você deseja mover ou copiar um aplicativo, você também deve atualizar o `deploymentProvider` caminho, para que o cliente é instalado, na verdade, de um novo local. Esse caminho de atualização é principalmente uma preocupação, se você tiver instalado os aplicativos. Para aplicativos online sempre são iniciados por meio da URL original, definindo o `deploymentProvider` é opcional. Se `deploymentProvider` estiver definido, ele será respeitado; caso contrário, a URL usada para iniciar o aplicativo será usada como a URL base para baixar os arquivos de aplicativo.  
  
> [!NOTE]
>  Toda vez que você atualize o manifesto deve também assiná-lo novamente.  
  
## <a name="see-also"></a>Consulte também  
 [Solucionando problemas de implantações do ClickOnce](../deployment/troubleshooting-clickonce-deployments.md)   
 [Protegendo aplicativos ClickOnce](../deployment/securing-clickonce-applications.md)   
 [Escolhendo uma estratégia de implantação do ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md)