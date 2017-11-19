---
title: IDebugGenericFieldDefinition | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: IDebugGenericFieldDefinition interface
ms.assetid: b5a853b7-221e-4d62-8948-07423089d75d
caps.latest.revision: "7"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5e0dd0b65b8b658f58f475e306cac42a118b8423
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="idebuggenericfielddefinition"></a>IDebugGenericFieldDefinition
Representa a definição de um campo de um tipo genérico de código gerenciado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
IDebugGenericFieldDefinition : IUnknown  
```  
  
## <a name="methods"></a>Métodos  
 Essa interface implementa os métodos a seguir:  
  
|Método|Descrição|  
|------------|-----------------|  
|[ConstructInstantiation](../../../extensibility/debugger/reference/idebuggenericfielddefinition-constructinstantiation.md)|Cria uma instância do campo recebe uma matriz de argumentos de tipo.|  
|[GetFormalTypeParams](../../../extensibility/debugger/reference/idebuggenericfielddefinition-getformaltypeparams.md)|Recupera os parâmetros de tipo dado o número de parâmetros.|  
|[TypeParamCount](../../../extensibility/debugger/reference/idebuggenericfielddefinition-typeparamcount.md)|Recupera o número de parâmetros de tipo associada ao campo genérico.|  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: Sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll