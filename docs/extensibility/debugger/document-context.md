---
title: Contexto de documento | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: debugging [Debugging SDK], contexts
ms.assetid: 8e8b5702-5c16-4988-953d-69dd807d8b84
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5a38d0ad28ad01b9e106cf06127b934dedfe5bba
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="document-context"></a>Contexto de documento
Em [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] depuração, um **contexto de documento**:  
  
-   Representa uma posição em um arquivo de origem. Para os idiomas em que o arquivo de origem não pode estar presente, um contexto de documento identifica uma posição em um documento gerado normalmente pelo ambiente de tempo de execução. Por exemplo, um mecanismo de script pode gerar um documento de script. Para obter mais informações, consulte [posição do documento](../../extensibility/debugger/document-position.md).  
  
-   Descreve uma posição em um documento de origem que corresponde a um contexto de código. O manipulador de símbolo mapeia um contexto de código para o contexto de documentação, usando informações geradas por um compilador ou interpretador.  
  
-   É implementado por um [IDebugDocumentContext2](../../extensibility/debugger/reference/idebugdocumentcontext2.md) interface.  
  
## <a name="see-also"></a>Consulte também  
 [Contexto de código](../../extensibility/debugger/code-context.md)   
 [Provedor de símbolo](../../extensibility/debugger/symbol-provider.md)   
 [Interfaces de provedor de símbolo](../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [Contextos do depurador](../../extensibility/debugger/debugger-contexts.md)