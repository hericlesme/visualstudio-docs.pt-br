---
title: "Restrições em comprimentos de cadeia de caracteres | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: source control plug-ins, restrictions on string lengths
ms.assetid: 877173d2-ca27-43b3-b1f4-8379f7c5e268
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 99144288a4da2a27956a9dc065ba5f5fba03fdcb
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="restrictions-on-string-lengths"></a>Restrições em comprimentos de cadeia de caracteres
A API de plug-in de controle de origem limita os comprimentos das cadeias de caracteres usadas em várias funções.  
  
## <a name="string-length-values"></a>Valores de comprimento de cadeia de caracteres  
  
|Constante|Valor|  
|--------------|-----------|  
|`SCC_NAME_LEN`|31|  
|`SCC_AUXLABEL_LEN`|31|  
|`SCC_USER_LEN`|31|  
|`SCC_PRJPATH_LEN`|300|  
  
> [!NOTE]
>  Comprimento não inclui o encerramento do `null`. Outras constantes com um sufixo "_SIZE" em vez de "_LEN" incluir espaço para encerramento do `null`.  
  
|Constante|Valor|  
|--------------|-----------|  
|SCC_NAME_SIZE|32|  
|SCC_AUXLABEL_SIZE|32|  
|SCC_USER_SIZE|32|  
|SCC_PRJPATH_SIZE|301|  
  
## <a name="see-also"></a>Consulte também  
 [Plug-ins de controle do código-fonte](../extensibility/source-control-plug-ins.md)