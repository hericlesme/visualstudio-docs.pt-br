---
title: Enumerador de código de Status de diretório | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- directory status code enumerator
- source control plug-ins, directory status enumeration
ms.assetid: 616026b5-f529-40ef-90c1-1836e116d797
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ea8abd11f3af8be510e88579651fb0a7f92e075b
ms.sourcegitcommit: 06db1892fff22572f0b0a11994dc547c2b7e2a48
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/08/2018
ms.locfileid: "39638460"
---
# <a name="directory-status-code-enumerator"></a>Enumerador de código de status do diretório
O `SccDirStatus` enumerador contém valores constantes nomeados que especificam o estado de um diretório no sistema de controle de origem. Essa enumeração é usada pelo [SccDirQueryInfo](../extensibility/sccdirqueryinfo-function.md). Essa foi introduzida na versão 1.2 do que a API de plug-in de controle do código-fonte.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
enum SccDirStatus {  
   SCC_DIRSTATUS_INVALID       = -1L,  
   SCC_DIRSTATUS_NOTCONTROLLED = 0x0000L,  
   SCC_DIRSTATUS_CONTROLLED    = 0x0001L,  
   SCC_DIRSTATUS_EMPTYPROJ     = 0x0002L  
};  
```  
  
## <a name="members"></a>Membros  
 SCC_DIRSTATUS_INVALID  
 Não foi possível obter o status; Não confie nele.  
  
 SCC_DIRSTATUS_NOTCONTROLLED  
 Diretório não está sob controle do código-fonte.  
  
 SCC_DIRSTATUS_CONTROLLED  
 Diretório está sob controle de origem.  
  
 SCC_DIRSTATUS_EMPTYPROJ  
 Projeto correspondente a esse diretório está vazio.  
  
## <a name="see-also"></a>Consulte também  
 [Plug-ins de controle de origem](../extensibility/source-control-plug-ins.md)   
 [SccDirQueryInfo](../extensibility/sccdirqueryinfo-function.md)