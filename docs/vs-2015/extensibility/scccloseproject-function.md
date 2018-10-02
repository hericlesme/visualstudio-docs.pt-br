---
title: Função SccCloseProject | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- SccCloseProject
helpviewer_keywords:
- SccCloseProject function
ms.assetid: 259c2069-d349-4814-810f-1c3151b7fb84
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: aebc9d43ebf712d8add7e2aee4f7884ef2754da6
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47461970"
---
# <a name="scccloseproject-function"></a>Função SccCloseProject
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [função SccCloseProject](https://docs.microsoft.com/visualstudio/extensibility/scccloseproject-function).  
  
Essa função fecha um projeto, marca o final de uma determinada sessão.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
SCCRTN SccCloseProject (  
   LPVOID pvContext  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 pvContext  
 A estrutura de contexto de plug-in de controle de origem.  
  
## <a name="return-value"></a>Valor de retorno  
 A implementação de plug-in de controle do código-fonte desta função deve retornar um dos seguintes valores:  
  
|Valor|Descrição|  
|-----------|-----------------|  
|SCC_OK|O projeto foi fechado com êxito.|  
|SCC_E_PROJNOTOPEN|Nenhum projeto estiver aberto no momento.|  
|SCC_E_NOTAUTHORIZED|O usuário não tem permissão para executar esta operação.|  
|SCC_E_NONSPECIFICERROR|Falha não específica.|  
  
## <a name="remarks"></a>Comentários  
 O [SccOpenProject](../extensibility/sccopenproject-function.md) é sempre chamado antes que essa função. Uma chamada para essa função é seguida por uma chamada para o `SccOpenProject` função ou o [SccUninitialize](../extensibility/sccuninitialize-function.md), que termina a conexão para o sistema de controle do código-fonte completamente.  
  
## <a name="see-also"></a>Consulte também  
 [Funções de API de plug-in de controle do código-fonte](../extensibility/source-control-plug-in-api-functions.md)   
 [SccOpenProject](../extensibility/sccopenproject-function.md)   
 [SccInitialize](../extensibility/sccinitialize-function.md)

