---
title: IDebugExpressionEvaluator2::SetCallback | Microsoft Docs
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
- IDebugExpressionEvaluator2::SetCallback
- SetCallback
ms.assetid: 31e3a99e-e784-44a3-8b19-cc5ef31ed546
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 44761820b510f87a8ac007dba4a45837c7915afd
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47467568"
---
# <a name="idebugexpressionevaluator2setcallback"></a>IDebugExpressionEvaluator2::SetCallback
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [IDebugExpressionEvaluator2::SetCallback](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugexpressionevaluator2-setcallback).  
  
Permite que o avaliador de expressão (EE) especificar a interface de retorno de chamada que o mecanismo do depurador (DES) usará para ler as configurações de métrica.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT SetCallback (  
   IDebugSettingsCallback2* pCallback  
);  
```  
  
```csharp  
int SetCallback (  
   IDebugSettingsCallback2 pCallback  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pCallback`  
 [in] Interface a ser usado para o retorno de chamada de configurações.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Esse método fornece uma interface para o Gerenciador de depuração de sessão que um avaliador de expressão pode usar para ler configurações de métrica. Ele é útil para depuração remota para ler a métrica a [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] computador.  
  
## <a name="example"></a>Exemplo  
 Os exemplos a seguir mostra como implementar esse método para um **CEE** objeto que expõe a [IDebugSettingsCallback2](../../../extensibility/debugger/reference/idebugsettingscallback2.md) interface.  
  
```cpp#  
HRESULT CEE::SetCallback(IDebugSettingsCallback2* in_pCallback)  
{  
    // precondition  
    INVARIANT( this );  
  
    // function body  
    if (NULL != this->m_LanguageSpecificUseCases.pfSetCallback)  
    {  
        EEDomain::fSetCallback DomainVal =  
        {  
            in_pCallback  
        };  
  
        BOOL bSuccess = (*this->m_LanguageSpecificUseCases.pfSetCallback)(DomainVal);  
        ENSURE( bSuccess );  
    }  
  
    // postcondition  
    INVARIANT( this );  
  
    return S_OK;  
}  
```  
  
## <a name="see-also"></a>Consulte também  
 [IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md)

