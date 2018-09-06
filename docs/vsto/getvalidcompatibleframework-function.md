---
title: Função GetValidCompatibleFramework
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
ms.openlocfilehash: 18ef1d61d0e203744cc6436d884c37339a4a1ef0
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2018
ms.locfileid: "35669770"
---
# <a name="getvalidcompatibleframework-function"></a>Função GetValidCompatibleFramework
  Essa API dá suporte à infraestrutura do Office e não se destina a ser usado diretamente do seu código.  
  
## <a name="syntax"></a>Sintaxe  
  
```csharp 
HRESULT WINAPI GetValidCompatibleFramework(  
    LPCWSTR lpwszCompatibleFrameworksXML,  
    BSTR* pbstrValidFrameworkTag  
);  
```  
  
### <a name="parameters"></a>Parâmetros  
|Parâmetro|Descrição|  
|---------------|-----------------|  
|*lpwszCompatibleFrameworksXML*|Não use.|  
|*pbstrValidFrameworkTag*|Não use.|  
  
## <a name="return-value"></a>Valor retornado  
 Se a função obtiver êxito, retorna **S_OK**. Se a função falhar, ele retornará um código de erro.  
  
  