---
title: Função GetVstoSolutionMetadata
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
ms.openlocfilehash: d21b0d2b90441f0b9be543933e7243dd41440b02
ms.sourcegitcommit: 1466ac0f49ebf7448ea4507ae3f79acb25d51d3e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/22/2018
---
# <a name="getvstosolutionmetadata-function"></a>Função GetVstoSolutionMetadata
  Essa API dá suporte à infraestrutura do Office e não se destina a ser usado diretamente no seu código.  
  
## <a name="syntax"></a>Sintaxe  
  
```c  
HRESULT WINAPI GetVstoSolutionMetadata(  
    LPCWSTR lpwszSolutionMetadataKey,  
    ISolutionMetadata** ppSolutionInfo  
);  
```  
  
### <a name="parameters"></a>Parâmetros  
  
|Parâmetro|Descrição|  
|---------------|-----------------|  
|*lpwszSolutionMetadataKey*|Não use.|  
|*ppSolutionInfo*|Não use.|  
  
## <a name="return-value"></a>Valor retornado  
 Se a função tiver êxito, ele retorna **S_OK**. Se a função falhar, ele retorna um código de erro.  
  
  