---
title: "Referência de API não gerenciada do ClickOnce | Microsoft Docs"
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
- LaunchApplication [ClickOnce unmanaged]
- ClickOnce, unmanaged APIs
- CleanOnlineAppCache [ClickOnce unmanaged]
- CleanOnlineAppCacheW interface [ClickOnce unmanaged]
- GetDeploymentDataFromManifest [ClickOnce unmanaged]
ms.assetid: ec002138-4054-456d-bcc1-79ac2f4a4fd7
caps.latest.revision: "6"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: 11e10800ff51abd6f95447d85204a44f8367f551
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="clickonce-unmanaged-api-reference"></a>Referência de API não gerenciada do ClickOnce
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]APIs não gerenciadas públicos de dfshim.dll.  
  
## <a name="cleanonlineappcache"></a>CleanOnlineAppCache  
 Limpa ou desinstalar todos os aplicativos online de [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] cache do aplicativo.  
  
### <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará S_OK; Caso contrário, retorna um HRESULT que representa a falha. Se ocorrer uma exceção gerenciada, retorna 0x80020009 (DISP_E_EXCEPTION).  
  
### <a name="remarks"></a>Comentários  
 Chamar CleanOnlineAppCache iniciará o [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] serviço se ainda não estiver sendo executado.  
  
## <a name="getdeploymentdatafrommanifest"></a>GetDeploymentDataFromManifest  
 Recupera informações sobre a implantação da URL manifesto e ativação.  
  
### <a name="parameters"></a>Parâmetros  
  
|Parâmetro|Descrição|Tipo|  
|---------------|-----------------|----------|  
|`pcwzActivationUrl`|Um ponteiro para o `ActivationURL`.|LPCWSTR|  
|`pcwzPathToDeploymentManifest`|Um ponteiro para o `PathToDeploymentManifest`.|LPCWSTR|  
|`pwzApplicationIdentity`|Um ponteiro para um buffer para receber uma cadeia de caracteres terminada em nulo que especifica a identidade do aplicativo completo retornado.|LPWSTR|  
|`pdwIdentityBufferLength`|Um ponteiro para uma DWORD que é o comprimento do `pwzApplicationIdentity` buffer, em WCHARs. Isso inclui o espaço para o caractere NULL de terminação.|LPDWORD|  
|`pwzProcessorArchitecture`|Um ponteiro para um buffer para receber uma cadeia de caracteres terminada em nulo que especifica a arquitetura do processador da implantação do aplicativo do manifesto.|LPWSTR|  
|`pdwArchitectureBufferLength`|Um ponteiro para uma DWORD que é o comprimento do `pwzProcessorArchitecture` buffer, em WCHARs.|LPDWORD|  
|`pwzApplicationManifestCodebase`|Um ponteiro para um buffer para receber uma cadeia de caracteres terminada em nulo que especifica a base de código do manifesto do aplicativo do manifesto.|LPWSTR|  
|`pdwCodebaseBufferLength`|Um ponteiro para uma DWORD que é o comprimento do `pwzApplicationManifestCodebase` buffer, em WCHARs.|LPDWORD|  
|`pwzDeploymentProvider`|Um ponteiro para um buffer para receber uma cadeia de caracteres terminada em nulo que especifica o provedor de implantação do manifesto, se estiver presente. Caso contrário, uma cadeia de caracteres vazia é retornada.|LPWSTR|  
|`pdwProviderBufferLength`|Um ponteiro para uma DWORD que é o comprimento do `pwzProviderBufferLength`.|LPDWORD|  
  
### <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará S_OK; Caso contrário, retorna um HRESULT que representa a falha. Retorna HRESULTFROMWIN32(ERROR_INSUFFICIENT_BUFFER) se um buffer é muito pequeno.  
  
### <a name="remarks"></a>Comentários  
 Ponteiros não devem ser nulos. `pcwzActivationUrl`e `pcwzPathToDeploymentManifest` não deve estar vazio.  
  
 É responsabilidade do chamador para limpar a URL de ativação. Por exemplo, a adição de escape caracteres onde eles são necessários ou remover a cadeia de caracteres de consulta.  
  
 É responsabilidade do chamador para limitar o comprimento de entrada. Por exemplo, o tamanho máximo da URL é 2KB.  
  
## <a name="launchapplication"></a>LaunchApplication  
 Inicia ou instalar um aplicativo usando uma URL de implantação.  
  
### <a name="parameters"></a>Parâmetros  
  
|Parâmetro|Descrição|Tipo|  
|---------------|-----------------|----------|  
|`deploymentUrl`|Um ponteiro para uma cadeia de caracteres terminada em nulo que contém a URL do manifesto de implantação.|LPCWSTR|  
|`data`|Reservado para uso futuro. Deve ser NULL.|LPVOID|  
|`flags`|Reservado para uso futuro. Deve ser 0.|DWORD|  
  
### <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará S_OK; Caso contrário, retorna um HRESULT que representa a falha. Se ocorrer uma exceção gerenciada, retorna 0x80020009 (DISP_E_EXCEPTION).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Deployment.Application.DeploymentServiceCom.CleanOnlineAppCache%2A>