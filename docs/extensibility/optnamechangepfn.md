---
title: OPTNAMECHANGEPFN | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- OPTNAMECHANGEPFN
helpviewer_keywords:
- OPTNAMECHANGEPFN callback function
ms.assetid: 147303f3-c7f1-438a-81b7-db891ea3d076
caps.latest.revision: 11
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 2d067d5dd150dd026a2bd29a8933e8d9f72222b0
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="optnamechangepfn"></a>OPTNAMECHANGEPFN
Essa é uma função de retorno de chamada especificada em uma chamada para o [SccSetOption](../extensibility/sccsetoption-function.md) (usando a opção `SCC_OPT_NAMECHANGEPFN`) e é usada para comunicar nome alterações feitas pelo controle da fonte de plug-in para o IDE.  
  
## <a name="signature"></a>Assinatura  
  
```cpp  
typedef void (*OPTNAMECHANGEPFN)(  
   LPVOID pvCallerData,  
   LPCSTR pszOldName,  
   LPCSTR pszNewName  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 pvCallerData  
 [in] Valor de usuário especificado em uma chamada anterior para o [SccSetOption](../extensibility/sccsetoption-function.md) (usando a opção `SCC_OPT_USERDATA`).  
  
 pszOldName  
 [in] O nome original do arquivo.  
  
 pszNewName  
 [in] O nome do arquivo foi renomeado para.  
  
## <a name="return-value"></a>Valor de retorno  
 Nenhum.  
  
## <a name="remarks"></a>Comentários  
 Se um arquivo é renomeado durante uma operação de controle de origem, o plug-in de controle de origem pode notificar o IDE sobre a alteração do nome por esse retorno de chamada.  
  
 Se o IDE não oferece suporte a esse retorno de chamada, ele não chamará o [SccSetOption](../extensibility/sccsetoption-function.md) especificá-lo. Se o plug-in não suporta esse retorno de chamada, ela retornará `SCC_E_OPNOTSUPPORTED` do `SccSetOption` quando o IDE tenta definir o retorno de chamada de função.  
  
## <a name="see-also"></a>Consulte também  
 [Funções de retorno de chamada implementadas pelo IDE](../extensibility/callback-functions-implemented-by-the-ide.md)   
 [SccSetOption](../extensibility/sccsetoption-function.md)