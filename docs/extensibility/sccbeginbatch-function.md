---
title: Função SccBeginBatch | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- SccBeginBatch
helpviewer_keywords:
- SccBeginBatch function
ms.assetid: 33968183-2e15-4e0d-955b-ca12212d1c25
caps.latest.revision: 14
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: d6415953a350321cb13f2705fa2bb182c278faa3
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="sccbeginbatch-function"></a>Função SccBeginBatch
Essa função inicia uma sequência de lote de operações de controle de origem. O [SccEndBatch](../extensibility/sccendbatch-function.md) será chamada para finalizar o lote. Esses lotes não podem ser aninhados.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
SCCRTN SccBeginBatch(void);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 nenhuma.  
  
## <a name="return-value"></a>Valor de retorno  
 A implementação de plug-in de controle de origem dessa função deve retornar um dos seguintes valores:  
  
|Valor|Descrição|  
|-----------|-----------------|  
|SCC_OK|Lote de operações foi iniciado com êxito.|  
|SCC_E_UNKNOWNERROR|Falha não específica.|  
  
## <a name="remarks"></a>Comentários  
 Lotes de controle do código-fonte são usados para executar as mesmas operações em vários projetos ou em vários contextos. Lotes podem ser usados para eliminar as caixas de diálogo de projeto de redundância da experiência do usuário durante uma operação em lote. O `SccBeginBatch` função e o [SccEndBatch](../extensibility/sccendbatch-function.md) são usados como um par de função para indicar o início e término de uma operação. Eles não podem ser aninhados. `SccBeginBatch`define um sinalizador que indica que uma operação em lote está em andamento.  
  
 Enquanto uma operação em lote estiver em vigor, o plug-in de controle de origem deve apresentar uma caixa de diálogo para qualquer questão de no máximo para o usuário e aplicar a resposta da caixa de diálogo em todas as operações subsequentes.  
  
## <a name="see-also"></a>Consulte também  
 [Funções de API de plug-in de controle de origem](../extensibility/source-control-plug-in-api-functions.md)   
 [SccEndBatch](../extensibility/sccendbatch-function.md)