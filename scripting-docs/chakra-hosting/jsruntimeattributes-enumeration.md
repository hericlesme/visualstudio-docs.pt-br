---
title: Enumeração JsRuntimeAttributes | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- jsrt/JsRuntimeAttributes
helpviewer_keywords:
- JsRuntimeAttributes enumeration
ms.assetid: f76d82e9-a695-4d6a-96c1-b3a4d27fed68
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3a7917ad5468b8d2924526f953ae444c5d8381eb
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24569056"
---
# <a name="jsruntimeattributes-enumeration"></a>Enumeração JsRuntimeAttributes
Atributos de um tempo de execução.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
enum JsRuntimeAttributes;  
```  
  
## <a name="members"></a>Membros  
  
### <a name="values"></a>Valores  
  
|Nome|Descrição|  
|----------|-----------------|  
|`JsRuntimeAttributeAllowScriptInterrupt`|O tempo de execução deve dar suporte a interrupção de script confiável. Isso aumenta o número de locais em que o tempo de execução verifica se há uma solicitação de interrupção de script, às custas de uma pequena quantidade de desempenho de tempo de execução.|  
|`JsRuntimeAttributeDisableBackgroundWork`|O tempo de execução não fará nenhum trabalho (como coleta de lixo) em threads em segundo plano.|  
|`JsRuntimeAttributeDisableEval`|Usar o construtor `eval` ou `function` lançará uma exceção.|  
|`JsRuntimeAttributeDisableNativeCodeGeneration`|O tempo de execução não gerará código nativo.|  
|`JsRuntimeAttributeEnableExperimentalFeatures`|Tempo de execução habilitará todos os recursos experimentais.|  
|`JsRuntimeAttributeEnableIdleProcessing`|O host chamará `JsIdle`, portanto, habilite o processamento ocioso. Caso contrário, o tempo de execução gerenciará a memória de maneira um pouco mais agressiva.|  
|`JsRuntimeAttributeDispatchSetExceptionsToDebugger`|Chamar `JsSetException` também enviará a exceção para o depurador de script (se houver), dando ao depurador a oportunidade de interromper a exceção.|  
|`JsRuntimeAttributeNone`|Nenhum atributo especial.|  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** jsrt.h  
  
## <a name="see-also"></a>Consulte também  
 [Referência (Tempo de Execução do JavaScript)](../chakra-hosting/reference-javascript-runtime.md)