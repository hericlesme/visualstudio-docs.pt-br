---
title: "Função GetValidCompatibleFramework | Microsoft Docs"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
ms.assetid: dfb365c0-5ffc-4290-ab8b-bd347e0f0db9
caps.latest.revision: "7"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 33c917f30ca7c5d42dc85036ef410519e6f0a721
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="getvalidcompatibleframework-function"></a>Função GetValidCompatibleFramework
  Essa API dá suporte à infraestrutura do Office e não se destina a ser usado diretamente no seu código.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT WINAPI GetValidCompatibleFramework(  
    LPCWSTR lpwszCompatibleFrameworksXML,  
    BSTR* pbstrValidFrameworkTag  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
  
|Parâmetro|Descrição|  
|---------------|-----------------|  
|*lpwszCompatibleFrameworksXML*|Não use.|  
|*pbstrValidFrameworkTag*|Não use.|  
  
## <a name="return-value"></a>Valor de retorno  
 Se a função tiver êxito, ele retorna **S_OK**. Se a função falhar, ele retorna um código de erro.  
  
  