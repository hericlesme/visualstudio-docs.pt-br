---
title: IDebugProgramPublisher2::PublishProgram | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProgramPublisher2::PublishProgram
helpviewer_keywords:
- IDebugProgramPublisher2::PublishProgram
ms.assetid: 92ff63f0-e869-4040-b3ae-b2c899e708ff
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 67ac5bad37ad5df85022ba6572da44d32de39736
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="idebugprogrampublisher2publishprogram"></a>IDebugProgramPublisher2::PublishProgram
Este método faz com que um programa disponível para mecanismos de depuração (DEs) e o Gerenciador de sessão de depuração.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT PublishProgram(  
   CONST_GUID_ARRAY Engines,  
   LPCOLESTR        szFriendlyName,  
   IUnknown*        pDebuggeeInterface  
);  
```  
  
```csharp  
int PublishProgram(  
   CONST_GUID_ARRAY Engines,  
   string           szFriendlyName,  
   object           pDebuggeeInterface  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `Engines`  
 [in] Uma matriz de GUIDs para DEs que podem iniciar ou conectar a este programa.  
  
 `szFriendlyName`  
 [in] Nome amigável para o programa (isso aparece nos menus ou caixas de diálogo apresentadas ao usuário).  
  
 `pDebuggeeInterface`  
 [in] `IUnknown` interface para o programa (esse valor é usado como um cookie para identificar exclusivamente o programa; esse mesmo valor é usado para o programa "Cancelar")  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retorna `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Para tornar um programa não está disponível para depuração, chame [UnpublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-unpublishprogram.md).  
  
## <a name="see-also"></a>Consulte também  
 [IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)   
 [UnpublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-unpublishprogram.md)