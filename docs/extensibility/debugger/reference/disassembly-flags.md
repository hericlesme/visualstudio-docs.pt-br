---
title: DISASSEMBLY_FLAGS | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: DISASSEMBLY_FLAGS
helpviewer_keywords: DISASSEMBLY_FLAGS enumeration
ms.assetid: c1ec5a4d-5d42-4660-932c-7348550140cb
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1959b101ed5c2aca4c1d806781952ad4e4e6b1ad
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="disassemblyflags"></a>DISASSEMBLY_FLAGS
Especifica os sinalizadores para a desmontagem.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
enum enum_DISASSEMBLY_FLAGS {   
   DF_DOCUMENTCHANGE     = 0x00000001,  
   DF_DISABLED           = 0x00000002,  
   DF_INSTRUCTION_ACTIVE = 0x00000004,  
   DF_DATA               = 0x00000008,  
   DF_HASSOURCE          = 0x00000010,  
   DF_DOCUMENT_CHECKSUM  = 0x00000020  
};  
typedef DWORD DISASSEMBLY_FLAGS;  
```  
  
```csharp  
public enum enum_DISASSEMBLY_FLAGS {   
   DF_DOCUMENTCHANGE     = 0x00000001,  
   DF_DISABLED           = 0x00000002,  
   DF_INSTRUCTION_ACTIVE = 0x00000004,  
   DF_DATA               = 0x00000008,  
   DF_HASSOURCE          = 0x00000010,  
   DF_DOCUMENT_CHECKSUM  = 0x00000020  
};  
```  
  
## <a name="members"></a>Membros  
 DF_DOCUMENTCHANGE  
 Indica que essa instrução está em um documento diferente que o anterior.  
  
 DF_DISABLED  
 Indica que esta instrução não será executada.  
  
 DF_INSTRUCTION_ACTIVE  
 Indica que essa instrução é um das instruções próximas a ser executado (pode haver mais de um).  
  
 DF_DATA  
 Indica que essa instrução é realmente dados (não o código).  
  
 DF_HASSOURCE  
 Indica que esta instrução tem origem. Algumas instruções, como código de coleta de lixo ou de criação de perfil, não tem nenhuma fonte correspondente.  
  
 DF_DOCUMENT_CHECKSUM  
 Indica que `bstrDocumentUrl` campo contém dados de soma de verificação após a URL do documento. Consulte a seção comentários para o [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) estrutura para como os dados de soma de verificação são armazenados.  
  
## <a name="remarks"></a>Comentários  
 Usado como o `dwFlags` membro o [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) estrutura.  
  
 Esses sinalizadores podem ser combinados com um bit a bit `OR`.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Enumerações](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)