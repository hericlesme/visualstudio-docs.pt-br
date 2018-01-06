---
title: "&lt;implantação&gt; elemento (implantação do ClickOnce) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- urn:schemas-microsoft-com:asm.v2#subscription
- urn:schemas-microsoft-com:asm.v2#beforeApplicationStartup
- urn:schemas-microsoft-com:asm.v2#deploymentProvider
- urn:schemas-microsoft-com:asm.v2#update
- urn:schemas-microsoft-com:asm.v2#deployment
- urn:schemas-microsoft-com:asm.v2#expiration
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords: <deployment> element [ClickOnce deployment manifest]
ms.assetid: 4fafa9c2-97a0-4cea-b8fd-9746dca33af4
caps.latest.revision: "30"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload: multiple
ms.openlocfilehash: 0caff13f84208152b3fa2ff4e56a7a2c7f0b6dd7
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ltdeploymentgt-element-clickonce-deployment"></a>&lt;implantação&gt; elemento (implantação do ClickOnce)
Identifica os atributos usados para a implantação de atualizações e exposição ao sistema.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
      <deployment   
   install  
   minimumRequiredVersion  
   mapFileExtensions  
   disallowUrlActivation  
   trustUrlParameters  
>   
   <subscription>   
         <update>   
            <beforeApplicationStartup/>   
            <expiration  
               maximumAge  
               unit  
            />  
         </update>    
   </subscription>   
   <deploymentProvider   
      codebase   
   />   
</deployment>  
```  
  
## <a name="elements-and-attributes"></a>Elementos e atributos  
 O `deployment` elemento é necessário e está no `urn:schemas-microsoft-com:asm.v1` namespace. O elemento tem os seguintes atributos.  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`install`|Necessário. Especifica se o aplicativo define uma presença na Windows **iniciar** menu e no painel de controle **adicionar ou remover programas** aplicativo. Os valores válidos são `true` e `false`. Se `false`, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] sempre executará a versão mais recente deste aplicativo da rede e não reconhecerá o `subscription` elemento.|  
|`minimumRequiredVersion`|Opcional. Especifica a versão mínima do aplicativo que pode ser executados no cliente. Se o número de versão do aplicativo é menor que o número de versão fornecido no manifesto de implantação, o aplicativo não será executado. Números de versão devem ser especificados no formato `N.N.N.N`, onde `N` é um inteiro não assinado. Se o `install` atributo é `false`, `minimumRequiredVersion` não deve ser definido.|  
|`mapFileExtensions`|Opcional. Assume o padrão de `false`. Se `true`, todos os arquivos na implantação devem ter uma extensão. Deploy. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]irá remover essa extensão esses arquivos assim que ele baixa os arquivos do servidor Web. Se você publicar seu aplicativo usando [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], adicionará automaticamente essa extensão para todos os arquivos. Esse parâmetro permite que todos os arquivos dentro de um [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] implantação a ser baixado de um servidor Web que bloqueia a transmissão de arquivos que terminam em "unsafe" extensões como .exe.|  
|`disallowUrlActivation`|Opcional. Assume o padrão de `false`. Se `true`, impede que um aplicativo instalado que está sendo iniciado clicando na URL ou digitando a URL no Internet Explorer. Se o `install` atributo não estiver presente, esse atributo é ignorado.|  
|`trustURLParameters`|Opcional. Assume o padrão de `false`. Se `true`, permite que a URL conter parâmetros de cadeia de caracteres de consulta que são passados para o aplicativo, muito como argumentos de linha de comando são passados para um aplicativo de linha de comando. Para obter mais informações, consulte [como: recuperar informações de cadeia de caracteres de consulta em um aplicativo ClickOnce Online](../deployment/how-to-retrieve-query-string-information-in-an-online-clickonce-application.md).<br /><br /> Se o `disallowUrlActivation` atributo é `true`, `trustUrlParameters` deve ser excluído do manifesto, ou explicitamente definido como `false`.|  
  
 O `deployment` elemento também contém os seguintes elementos filho.  
  
## <a name="subscription"></a>Assinatura  
 Opcional. Contém o `update` elemento. O `subscription` elemento não tem atributos. Se o `subscription` o elemento não existe, o [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativo nunca verificar atualizações. Se o `install` atributo do `deployment` elemento `false`, o `subscription` elemento será ignorado, pois um [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativo é iniciado a partir da rede sempre usa a versão mais recente.  
  
## <a name="update"></a>atualizar  
 Necessário. Esse elemento é um filho do `subscription` elemento e contenha o `beforeApplicationStartup` ou `expiration` elemento. `beforeApplicationStartup`e `expiration` não pode ser especificados no manifesto de implantação do mesmo.  
  
 O `update` elemento não tem atributos.  
  
## <a name="beforeapplicationstartup"></a>beforeApplicationStartup  
 Opcional. Esse elemento é um filho de `update` elemento e sem atributos. Quando o `beforeApplicationStartup` existir, o aplicativo será bloqueada quando [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] verifica se há atualizações, se o cliente está online. Se esse elemento não existe, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] primeiro verificar atualizações com base nos valores especificados para o `expiration` elemento. `beforeApplicationStartup`e `expiration` não pode ser especificados no manifesto de implantação do mesmo.  
  
## <a name="expiration"></a>expiração  
 Opcional. Esse elemento é um filho de `update` elemento, e não tem filhos. `beforeApplicationStartup`e `expiration` não pode ser especificados no manifesto de implantação do mesmo. Quando ocorre a verificação de atualização e uma versão atualizada for detectada, a nova versão armazena em cache enquanto executa a versão existente. Em seguida, instala a nova versão na próxima inicialização da [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativo.  
  
 O `expiration` elemento suporta os seguintes atributos.  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`maximumAge`|Necessário. Identifica a idade de atualização atual deverá ficar antes do aplicativo executa uma verificação de atualização. A unidade de tempo é determinada pelo `unit` atributo.|  
|`unit`|Necessário. Identifica a unidade de tempo para `maximumAge`. Unidades válidas são `hours`, `days`, e `weeks`.|  
  
## <a name="deploymentprovider"></a>deploymentProvider  
 Para o .NET Framework 2.0, esse elemento é necessário se o manifesto de implantação contém um `subscription` seção. Para o .NET Framework 3.5 e versões posteriores, esse elemento é opcional e será padrão para o servidor e o caminho do arquivo no qual o manifesto de implantação foi descoberto.  
  
 Esse elemento é um filho de `deployment` elemento e tem o seguinte atributo.  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`codebase`|Necessário. Identifica o local, como um URI Uniform Resource Identifier (), do manifesto de implantação que é usado para atualizar o [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativo. Esse elemento também permite encaminhamento locais de atualização para instalações baseadas em CD. Deve ser um URI válido.|  
  
## <a name="remarks"></a>Comentários  
 Você pode configurar seu [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] procurar atualizações após a inicialização do aplicativo para verificar se há atualizações na inicialização, ou nunca verificar se há atualizações. Para verificar se há atualizações na inicialização, certifique-se de que o `beforeApplicationStartup` elemento existe sob o `update` elemento. Para verificar se há atualizações após a inicialização, certifique-se de que o `expiration` elemento existe sob o `update` elemento e que os intervalos de atualização são fornecidos.  
  
 Para desabilitar a verificação de atualizações, remova o `subscription` elemento. Quando você especifica no manifesto de implantação para nunca verificar se há atualizações, você pode ainda verificar manualmente as atualizações usando o <xref:System.Deployment.Application.ApplicationDeployment.CheckForUpdate%2A> método.  
  
 Para obter mais informações sobre como deploymentProvider está relacionado a atualizações, consulte [escolhendo uma estratégia de atualização do ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md).  
  
## <a name="examples"></a>Exemplos  
 O exemplo de código a seguir ilustra uma `deployment` elemento em um [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] o manifesto de implantação. O exemplo usa um `deploymentProvider` elemento para indicar o local da atualização preferencial.  
  
```  
<deployment install="true" minimumRequiredVersion="2.0.0.0" mapFileExtension="true" trustUrlParameters="true">  
    <subscription>  
      <update>  
        <expiration maximumAge="6" unit="hours" />  
      </update>  
    </subscription>  
    <deploymentProvider codebase="http://www.adatum.com/MyApplication.application" />  
  </deployment>  
```  
  
## <a name="see-also"></a>Consulte também  
 [Manifesto de implantação do ClickOnce](../deployment/clickonce-deployment-manifest.md)