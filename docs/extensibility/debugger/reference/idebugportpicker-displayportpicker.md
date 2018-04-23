---
title: IDebugPortPicker::DisplayPortPicker | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- DisplayPortPicker
- IDebugPortPicker::DisplayPortPicker
ms.assetid: 08511ef5-be64-4069-b169-a569cc94bc64
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: bb43ac1bdf173de8e7224f154ecb57cca53abd8c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="idebugportpickerdisplayportpicker"></a>IDebugPortPicker::DisplayPortPicker
Exibe a caixa de diálogo especificada que permite que o usuário selecione uma porta.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT DisplayPortPicker(  
   HWND hwndParentDialog,  
   BSTR* pbstrPortId  
);  
```  
  
```csharp  
public int DisplayPortPicker(  
   int hwndParentDialog,  
   out string pbstrPortId  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `hwndParentDialog`  
 [in] Identificador para a caixa de diálogo pai.  
  
 `pbstrPortId`  
 [out] Cadeia de caracteres de identificador de porta.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retorna `S_OK`; caso contrário, retorna um código de erro. Um valor de retorno `S_FALSE` (ou um valor de retorno `S_OK` com o `BSTR` definida como `NULL`) indica que o usuário clicou **Cancelar**.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugPortPicker](../../../extensibility/debugger/reference/idebugportpicker.md)