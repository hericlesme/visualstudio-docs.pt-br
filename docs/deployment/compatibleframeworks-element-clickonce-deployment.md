---
title: "&lt;compatibleFrameworks&gt; elemento (implantação do ClickOnce) | Microsoft Docs"
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
helpviewer_keywords: <compatibleFrameworks> element [ClickOnce deployment manifest]
ms.assetid: f6c3ee55-9e65-403d-8664-3ebde872c7d4
caps.latest.revision: "15"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: bb8c31d37bd37f4e2db8415ef1815caec0ec185a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="ltcompatibleframeworksgt-element-clickonce-deployment"></a>&lt;compatibleFrameworks&gt; elemento (implantação do ClickOnce)
Identifica as versões do .NET Framework em que este aplicativo pode instalar e executar.  
  
> [!NOTE]
>  [MageUI.exe](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client) não oferece suporte a `compatibleFrameworks` elemento ao salvar um manifesto de aplicativo que já foi assinado com um certificado usando [MageUI.exe](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client). Em vez disso, você deve usar [Mage.exe](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool).  
  
## <a name="syntax"></a>Sintaxe  
  
```  
<compatibleFrameworks  
      SupportUrl>   
   <framework  
      targetVersion  
      profile  
      supportedRuntime  
   />   
</ compatibleFrameworks>  
```  
  
## <a name="elements-and-attributes"></a>Elementos e atributos  
 O `compatibleFrameworks` elemento é necessário para manifestos de implantação direcionados a [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] tempo de execução fornecido pelo [!INCLUDE[net_v40_short](../code-quality/includes/net_v40_short_md.md)] ou posterior. O `compatibleFrameworks` elemento contém um ou mais `framework` elementos que especificam as versões do .NET Framework em que esse aplicativo pode ser executado. O [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] tempo de execução será executado o aplicativo na primeira disponível `framework` nesta lista.  
  
 A tabela a seguir lista os atributos que o `compatibleFrameworks` oferece suporte ao elemento.  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`S` `upportUrl`|Opcional. Especifica uma URL em que a versão do .NET Framework compatível preferida pode ser baixada.|  
  
## <a name="framework"></a>estrutura  
 Necessário. A tabela a seguir lista os atributos que o `framework` oferece suporte ao elemento.  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`targetVersion`|Necessário. Especifica o número de versão do .NET Framework de destino.|  
|`profile`|Necessário. Especifica o perfil do .NET Framework de destino.|  
|`supportedRuntime`|Necessário. Especifica o número de versão do tempo de execução associada ao destino do .NET Framework.|  
  
## <a name="remarks"></a>Comentários  
  
## <a name="example"></a>Exemplo  
 O seguinte exemplo de código mostra uma `compatibleFrameworks` elemento em um [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] o manifesto de implantação. Esta implantação pode ser executado no [!INCLUDE[net_client_v40_long](../deployment/includes/net_client_v40_long_md.md)]. Ele também pode ser executado no [!INCLUDE[net_v40_short](../code-quality/includes/net_v40_short_md.md)] porque ele é um superconjunto do [!INCLUDE[net_client_v40_long](../deployment/includes/net_client_v40_long_md.md)].  
  
```  
<compatibleFrameworks xmlns="urn:schemas-microsoft-com:clickonce.v2">  
  <framework   
      targetVersion="4.0"   
      profile="Client"   
      supportedRuntime="4.0.30319" />  
</compatibleFrameworks>  
```  
  
## <a name="see-also"></a>Consulte também  
 [Manifesto de implantação do ClickOnce](../deployment/clickonce-deployment-manifest.md)