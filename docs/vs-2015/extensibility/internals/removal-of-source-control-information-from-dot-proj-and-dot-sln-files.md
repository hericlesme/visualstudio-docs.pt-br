---
title: Remoção de informações de controle do código-fonte. PROJ e. Arquivos sln | Microsoft Docs
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
- source control plug-ins, .sln and .proj files
ms.assetid: 7b06883f-35de-41e2-9a9e-d3edba236f17
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7c6709d7808eba229455805ecb2b4a8d0c8af525
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47475722"
---
# <a name="removal-of-source-control-information-from-proj-and-sln-files"></a>Remoção de informações de controle do código-fonte de arquivos .Proj e .Sln
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [remoção do controle de informações da origem. PROJ e. Arquivos sln](https://docs.microsoft.com/visualstudio/extensibility/internals/removal-of-source-control-information-from-dot-proj-and-dot-sln-files).  
  
Na versão 1.2 do que a API de plug-in de controle do código-fonte SCC informações são armazenadas em um MSSCCPRJ. Arquivos SCC. A vantagem do MSSCCPRJ. Arquivos SCC é que as informações de SCC é fonte não - controlado, como se fosse nos arquivos PROJ e. sln.  
  
## <a name="version-12-changes"></a>Alterações da versão 1.2  
 No código-fonte plug-ins de controle se baseiam na API de plug-in de controle do código-fonte versão 1.1, informações sobre o controle do código-fonte são armazenadas no projeto (. proj) e arquivos de solução (. sln). O local do banco de dados das informações de controle de origem é especificado pelo AuxPath, e o local específico no banco de dados é especificado pelo NomeDoProjeto. Esse comportamento pode causar problemas após a ramificação, bifurcação ou operações de cópia porque o NomeDoProjeto normalmente seriam inválido após qualquer uma dessas operações.  
  
 Na API de plug-in de controle de origem versão 1.1, o IDE usada ~ arquivos SAK para detectar se um plug-in com suporte a MSSCCPRJ. Método SCC armazenar informações de controle do código-fonte. A API de plug-in de controle do código-fonte versão 1.2 fornece uma nova funcionalidade para detectar o suporte para MSSCCPRJ. Arquivos SCC sem usar um ~ arquivo SAK. Para obter mais informações, consulte [eliminação de ~ SAK arquivos](../../extensibility/internals/elimination-of-tilde-sak-files.md).  
  
## <a name="see-also"></a>Consulte também  
 [Novidades na Versão 1.2 da API do plug-in de controle de código-fonte](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)

