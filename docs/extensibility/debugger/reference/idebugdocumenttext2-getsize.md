---
title: IDebugDocumentText2::GetSize | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugDocumentText2::GetSize
helpviewer_keywords: IDebugDocumentText2::GetSize
ms.assetid: bf515a8f-dcee-4004-8f81-543d547ceaae
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 25bf0a7c570c2c11e09c9e6d98d1f4be05d7adb5
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="idebugdocumenttext2getsize"></a>IDebugDocumentText2::GetSize
Recupera o tamanho do texto nessa posição no documento.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetSize(   
   ULONG* pcNumLines,  
   ULONG* pcNumChars  
);  
```  
  
```csharp  
int GetSize(   
   ref uint pcNumLines,  
   ref uint pcNumChars  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pcNumLines`  
 [out] Retorna o número de linhas de texto.  
  
 `pcNumChars`  
 [out] Retorna o número de caracteres de texto.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retorna `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 [C++] Se um valor específico não for desejado, passe um NULL para o parâmetro.  
  
 [Apenas c#] Ambos os parâmetros devem ser especificados.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)