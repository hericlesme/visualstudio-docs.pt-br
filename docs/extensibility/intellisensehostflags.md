---
title: IntelliSenseHostFlags | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IntellisenseHostFlags
helpviewer_keywords:
- IntelliSense, IntellisenseHostFlags enumeration
- IntellisenseHostFlags enumeration
ms.assetid: 0930640b-eb84-48ef-a8f7-d4268f55c99c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a096e79a64168f74150103a5f3ba3a8683fe184e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="intellisensehostflags"></a>IntelliSenseHostFlags
Especifica os sinalizadores de host do IntelliSense.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
enum IntellisenseHostFlags  
{  
    IHF_READONLYCONTEXT      = 0x00000001  
    IHF_NOSEPARATESUBJECT    = 0x00000002  
    IHF_SINGLELINESUBJECT    = 0x00000004  
    IHF_FORCECOMMITTOCONTEXT = 0x00000008  
    IHF_OVERTYPE             = 0x00000010  
};  
```  
  
#### <a name="parameters"></a>Parâmetros  
  
|Membros|Descrição|  
|-------------|-----------------|  
|`IHF_READONLYCONTEXT`|Buffer de contexto é somente leitura.|  
|`IHF_NOSEPARATESUBJECT`|Nenhum texto de assunto. Buffer de contexto contém o destino do IntelliSense (implica `!IHF_READONLYCONTEXT`).|  
|`IHF_SINGLELINESUBJECT`|Texto de assunto não tem multi-linha capacidade.|  
|`IHF_FORCECOMMITTOCONTEXT`|Mesmo que `CanCommitIntoReadOnlyBuffer`.|  
|`IHF_OVERTYPE`|Edição (no assunto ou contexto) deve ser feito no modo sobrescrever.|  
  
## <a name="requirements"></a>Requisitos  
 SingleFileeditor.idl  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualStudio.TextManager.Interop>