---
title: IDebugExpressionEvaluator2::GetService | Microsoft Docs
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
- IDebugExpressionEvaluator2::GetService
- GetService
ms.assetid: f8988a9e-9d18-42af-84a7-55f41e9adf63
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7e8ef02bee0f716194f1d37d619f070e00ecadbe
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47468033"
---
# <a name="idebugexpressionevaluator2getservice"></a>IDebugExpressionEvaluator2::GetService
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [IDebugExpressionEvaluator2::GetService](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugexpressionevaluator2-getservice).  
  
Recupera um objeto de serviço recebe seu identificador exclusivo.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT GetService (  
   GUID        uid,  
   IUnknown ** ppService  
);  
```  
  
```csharp  
int GetService (  
   Guid       uid,  
   out object ppService  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `uid`  
 [in] Identificador exclusivo do serviço a ser recuperado.  
  
 `ppService`  
 [out] Retorna um objeto que representa o serviço.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Isso pode ser consumido por um avaliador de expressão de terceiros para obter serviços de outro avaliador de expressão. Por exemplo, esse método pode ser usado para obter a interface para o serviço de visualização simultânea do avaliador de expressão padrão. Avaliadores de expressão de terceiros provavelmente não precisará implementar essa interface.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md)

