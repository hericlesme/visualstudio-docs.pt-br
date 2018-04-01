---
title: Função SccGetExtendedCapabilities | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- SccGetExtendedCapabilities
helpviewer_keywords:
- SccGetExtendedCapabilities function
ms.assetid: 588c6a92-2147-4d8b-a357-96ca7da0a092
caps.latest.revision: 16
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 870d793a11cccdaae9657deabb0e3b08c4d8c6f5
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="sccgetextendedcapabilities-function"></a>Função SccGetExtendedCapabilities
Esta função retorna o plug-in de controle de origem com suporte de recursos adicionais.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
SCCRTN SccGetExtendedCapabilities(  
   LPVOID pContext,  
   LONG lSccExCaps,  
   LPBOOL pbSupported  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 pContext  
 [in] O ponteiro de contexto de plug-in de controle de origem.  
  
 lSccExCaps  
 [in] Um sinalizador que especifica uma funcionalidade estendida para o qual testar (consulte a tabela código funcionalidade estendida [sinalizadores de recursos](../extensibility/capability-flags.md) para os sinalizadores de possíveis).  
  
 pbSupported  
 [out] Retorna diferente de zero (`TRUE`) se houver suporte para o recurso especificado; caso contrário, retorna zero (`FALSE`).  
  
## <a name="return-value"></a>Valor de retorno  
 A implementação de plug-in de controle de origem dessa função deve retornar um dos seguintes valores:  
  
|Valor|Descrição|  
|-----------|-----------------|  
|SCC_OK|A operação de recurso get foi concluída com êxito.|  
|SCC_E_UNKNOWNERROR<br /><br /> SCC_E_NONSPECIFICERROR|Ocorreu erro desconhecido ou não especificado.|  
  
## <a name="remarks"></a>Comentários  
 Este método é chamado por demanda. ou seja, quando um recurso precisa ser testado, este método é chamado para determinar se funcionalidade com suporte. Sinalizador de apenas uma por vez é especificado.  
  
## <a name="see-also"></a>Consulte também  
 [Funções de API de plug-in de controle de origem](../extensibility/source-control-plug-in-api-functions.md)   
 [Códigos de erro](../extensibility/error-codes.md)   
 [Sinalizadores de recurso](../extensibility/capability-flags.md)