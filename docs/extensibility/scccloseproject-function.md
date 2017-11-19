---
title: "Função SccCloseProject | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: SccCloseProject
helpviewer_keywords: SccCloseProject function
ms.assetid: 259c2069-d349-4814-810f-1c3151b7fb84
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d37dc9bff7652856109fb4ec29c8eaa52f1d2507
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="scccloseproject-function"></a>Função SccCloseProject
Essa função fecha um projeto, marca o final de uma sessão em particular.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
SCCRTN SccCloseProject (  
   LPVOID pvContext  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 pvContext  
 A estrutura de contexto de plug-in de controle de origem.  
  
## <a name="return-value"></a>Valor de retorno  
 A implementação de plug-in de controle de origem dessa função deve retornar um dos seguintes valores:  
  
|Valor|Descrição|  
|-----------|-----------------|  
|SCC_OK|O projeto foi fechado com êxito.|  
|SCC_E_PROJNOTOPEN|Nenhum projeto estiver aberto.|  
|SCC_E_NOTAUTHORIZED|O usuário não tem permissão para executar esta operação.|  
|SCC_E_NONSPECIFICERROR|Falha não específica.|  
  
## <a name="remarks"></a>Comentários  
 O [SccOpenProject](../extensibility/sccopenproject-function.md) é sempre chamado antes que essa função. Uma chamada para essa função é seguida por uma chamada para o `SccOpenProject` função ou o [SccUninitialize](../extensibility/sccuninitialize-function.md), que termina a conexão ao sistema de controle de origem completamente.  
  
## <a name="see-also"></a>Consulte também  
 [Funções de API de plug-in de controle de origem](../extensibility/source-control-plug-in-api-functions.md)   
 [SccOpenProject](../extensibility/sccopenproject-function.md)   
 [SccInitialize](../extensibility/sccinitialize-function.md)