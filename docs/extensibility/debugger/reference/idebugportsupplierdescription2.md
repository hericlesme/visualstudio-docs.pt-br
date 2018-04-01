---
title: IDebugPortSupplierDescription2 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IDebugPortSupplierDescription2 interface
ms.assetid: dd19b9d6-0703-44b3-9498-cedffa0ce5b7
caps.latest.revision: 8
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: d4fe70f9d0ef5273f30f16e99524247a2e45843c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="idebugportsupplierdescription2"></a>IDebugPortSupplierDescription2
Permite que o [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] interface do usuário para exibir o texto dentro de **informações de transporte** seção do **anexar ao processo** caixa de diálogo.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
IDebugPortSupplierDescription2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Observações para implementadores  
 Essa interface é implementada por fornecedores de porta.  
  
## <a name="methods"></a>Métodos  
 A tabela a seguir mostra os métodos de `IDebugPortSupplierDescription2`.  
  
|Método|Descrição|  
|------------|-----------------|  
|[GetDescription](../../../extensibility/debugger/reference/idebugportsupplierdescription2-getdescription.md)|Recupera a descrição e a descrição de metadados para o fornecedor de porta.|  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: Msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll