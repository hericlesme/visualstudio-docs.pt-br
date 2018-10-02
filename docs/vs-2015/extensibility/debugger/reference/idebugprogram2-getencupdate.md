---
title: IDebugProgram2::GetENCUpdate | Microsoft Docs
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
- IDebugProgram2::GetENCUpdate
helpviewer_keywords:
- IDebugProgram2::GetENCUpdate
ms.assetid: 9832aac8-6320-4fd8-91dd-2a0852febb00
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5b06716c2a9de2e2fb61a372c51f2f574065aefc
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47475049"
---
# <a name="idebugprogram2getencupdate"></a>IDebugProgram2::GetENCUpdate
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [IDebugProgram2::GetENCUpdate](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugprogram2-getencupdate).  
  
Esse método obtém a atualização de editar e continuar (ENC) para este programa. Um mecanismo de depuração personalizado sempre retorna `E_NOTIMPL`.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT GetENCUpdate(   
   IUnknown** ppUpdate  
);  
```  
  
```csharp  
int GetENCUpdate(  
   out object ppUpdate  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `ppUpdate`  
 [out] Retorna uma interface interna que pode ser usada para atualizar este programa.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.  
  
> [!NOTE]
>  Um mecanismo de depuração personalizado deve sempre retornar `E_NOTIMPL`.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)

