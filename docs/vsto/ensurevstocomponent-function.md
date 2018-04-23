---
title: Função EnsureVSTOComponent | Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 5561d3c046c083c1495b858d36f6c867050ed842
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="ensurevstocomponent-function"></a>Função EnsureVSTOComponent
  Essa API dá suporte à infraestrutura do Office e não se destina a ser usado diretamente no seu código.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT EnsureVSTOComponent(  
    IVSTProject *pProject  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
  
|Parâmetro|Descrição|  
|---------------|-----------------|  
|*pProject*|Não use.|  
  
## <a name="return-value"></a>Valor de retorno  
 Se a função tiver êxito, ele retorna **S_OK**. Se a função falhar, ele retorna um código de erro.  
  
  