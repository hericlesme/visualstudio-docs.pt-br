---
title: Cadeias de caracteres usadas como chaves para localizar um controle de fonte plug-in | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- source control plug-ins, strings used for finding
ms.assetid: c1e31f76-42a1-4c3d-afb2-664044ef12fd
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1e2a663f11834a063faa0017cd37f6f542ab98ad
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47465831"
---
# <a name="strings-used-as-keys-for-finding-a-source-control-plug-in"></a>Cadeias de caracteres usadas como chaves para localizar um plug-in de controle do código-fonte
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [cadeias de caracteres usadas como chaves para localizar um plug-in de controle do código-fonte](https://docs.microsoft.com/visualstudio/extensibility/strings-used-as-keys-for-finding-a-source-control-plug-in).  
  
As cadeias de caracteres a seguir são as chaves para acessar o registro para localizar informações sobre o controle de fonte plug-in.  
  
 `STR_SCC_PROVIDER_REG_LOCATION`, `STR_PROVIDERREGKEY`, `STR_SCCPROVIDERPATH`, e `STR_SCCPROVIDERNAME` são as chaves do registro ou valores usados para registrar uma DLL como um plug-in de controle do código-fonte para o Visual Studio.  
  
 `SCC_PROJECTNAME_KEY`, `SCC_PROJECTAUX_KEY`, `SCC_KEY, SCC_FILE_SIGNATURE`, e `SCC_STATUS_FILE` são usados para descrever o formato do MSSCCPRJ. Arquivos SCC.  
  
## <a name="string-keys-and-values"></a>Chaves de cadeia de caracteres e valores  
  
|Chave|Valor|  
|---------|-----------|  
|`STR_SCC_PROVIDER_REG_LOCATION`|Software\SourceCodeControlProvider|  
|`STR_PROVIDERREGKEY`|ProviderRegKey|  
|`STR_SCCPROVIDERPATH`|SCCServerPath|  
|`STR_SCCPROVIDERNAME`|SCCServerName|  
|`STR_SCC_INI_SECTION`|Controle do código fonte|  
|`STR_SCC_INI_KEY`|SourceCodeControlProvider|  
|`SCC_PROJECTNAME_KEY`|SCC_Project_Name|  
|`SCC_PROJECTAUX_KEY`|SCC_Aux_Path|  
|`SCC_STATUS_FILE`|MSSCCPRJ. SCC|  
|`SCC_KEY`|SCC|  
|`SCC_FILE_SIGNATURE`|Um arquivo de controle do código-fonte|  
|`SCC_NSE`|Extensão do Namespace|  
|`SCC_NSE_PREFIX`|Prefixo de protocolo|  
|`SCC_NSE_DisableOpenSCC`|DisableOpenFromSourceControl|  
|`STR_SCCHELPCOLLECTION`|HelpCollection|  
|`STR_UI_LANGUAGE`|UILanguage|  
|`STR_SRCSAFE_ROOT_KEY`|Software\Microsoft\SourceSafe|  
  
## <a name="see-also"></a>Consulte também  
 [Plug-ins de controle de origem](../extensibility/source-control-plug-ins.md)   
 [Como: instalar um plug-in de controle do código-fonte](../extensibility/internals/how-to-install-a-source-control-plug-in.md)   
 [Arquivo MSSCCPRJ.SCC](../extensibility/mssccprj-scc-file.md)

