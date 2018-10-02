---
title: IDebugProperty3::GetStringCharLength | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugProperty3::GetStringCharLength
helpviewer_keywords:
- IDebugProperty3::GetStringCharLength
ms.assetid: 89a8676b-6da9-4358-91c2-039bf33f99e4
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8371d86aed626ca9d7364e51b235b37f755f48be
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47475696"
---
# <a name="idebugproperty3getstringcharlength"></a>IDebugProperty3::GetStringCharLength
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [IDebugProperty3::GetStringCharLength](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugproperty3-getstringcharlength).  
  
Retorna o número de caracteres na cadeia de caracteres da propriedade associada.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetStringCharLength(  
   ULONG *pLen  
);  
```  
  
```csharp  
int GetStringCharLength(  
   out uint pLen  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
  
|Parâmetro|Descrição|  
|---------------|-----------------|  
|`pLen`|[out] Retorna o número de caracteres na cadeia de caracteres da propriedade.|  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retornará o código de erro.  
  
## <a name="remarks"></a>Comentários  
 Normalmente, esse método é usado como um prelúdio para alocar um buffer para uma chamada para o [GetStringChars](../../../extensibility/debugger/reference/idebugproperty3-getstringchars.md) método.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como implementar esse método para um **CProperty** objeto que expõe a [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) interface.  
  
```cpp#  
STDMETHODIMP CProperty::GetStringCharLength(ULONG *pLen)  
{  
    HRESULT hr = E_INVALIDARG;  
  
    EVALFLAGS oldEVALFLAGS = m_EVALFLAGS;  
  
    m_EVALFLAGS &= ~EVAL_NOFUNCEVAL;  
  
    if (pLen)  
    {  
        DEBUG_PROPERTY_INFO dpInfo;  
        dpInfo.bstrValue = NULL;  
        ULONG ulen = 0;  
        hr = GetPropertyInfo(DEBUGPROP_INFO_VALUE,10,DEFAULT_TIMEOUT,NULL,0,&dpInfo);  
        if (hr == S_OK && dpInfo.bstrValue)  
        {  
            if (wcscmp(dpInfo.bstrValue,L"Nothing") == 0)  
            {  
                ulen = 0;   //VSWhidbey#64815  
            }  
            else  
            {  
                ulen = ::SysStringLen(dpInfo.bstrValue);  
                if( ulen > 2 &&  
                    dpInfo.bstrValue[0] == L'"' &&  
                    dpInfo.bstrValue[ulen-1] == L'"')  
                {                      
                    ulen = ulen > 2 ? ulen - 2 : ulen;  //remove two double quotes  
                }  
            }  
        }  
        ::SysFreeString(dpInfo.bstrValue);  
        *pLen = ulen;  
    }  
    m_EVALFLAGS = oldEVALFLAGS;  
    return hr;  
}  
```  
  
## <a name="see-also"></a>Consulte também  
 [GetStringChars](../../../extensibility/debugger/reference/idebugproperty3-getstringchars.md)   
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)

