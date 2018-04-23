---
title: Função SccEndBatch | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- SccEndBatch
helpviewer_keywords:
- SccEndBatch function
ms.assetid: 100e7833-fe0a-45c0-9fca-3e61fd1165b7
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ec549b5bb0a6c48946edf59f0ab1423cea0ac704
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="sccendbatch-function"></a>Função SccEndBatch
Essa função termina um lote de operações de controle de origem. Esses lotes não podem ser aninhados.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
SCCRTN SccEndBatch(void);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 nenhuma.  
  
## <a name="return-value"></a>Valor de retorno  
 A implementação de plug-in de controle de origem dessa função deve retornar um dos seguintes valores:  
  
|Valor|Descrição|  
|-----------|-----------------|  
|SCC_OK|Lote de operações concluídas com êxito.|  
|SCC_E_UNKNOWNERROR|Falha não específica.|  
  
## <a name="remarks"></a>Comentários  
 Lotes de controle do código-fonte são usados para executar as mesmas operações de controle do código-fonte entre vários projetos ou em vários contextos. Lotes podem ser usados para eliminar as caixas de diálogo redundantes da experiência do usuário durante uma operação em lote. O [SccBeginBatch](../extensibility/sccbeginbatch-function.md) e `SccEndBatch` função são usados como um par para indicar o início e término de uma operação. Eles não podem ser aninhados.  
  
## <a name="see-also"></a>Consulte também  
 [Funções de API de plug-in de controle de origem](../extensibility/source-control-plug-in-api-functions.md)   
 [SccBeginBatch](../extensibility/sccbeginbatch-function.md)