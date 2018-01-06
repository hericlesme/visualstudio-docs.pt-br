---
title: 'VsgDbg:: ~ VsgDbg (destruidor) | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7a3b97fb-d344-4df7-b195-9347d1edfcf7
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 16fce161dc1c01797a67fe8d104c26ce603a4b76
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="vsgdbgvsgdbg-destructor"></a>VsgDbg::~VsgDbg (Destruidor)
Destrói a uma instância do `VsgDbg` classe. Se as informações de gráficos ativamente está sendo registradas, o arquivo de log do gráfico é finalizado e fechado, e os recursos que foram usados durante a captura ativamente informações de gráficos são liberados.  
  
## <a name="syntax"></a>Sintaxe  
  
```C++  
~VsgDbg();  
```  
  
## <a name="see-also"></a>Consulte também  
 [VsgDbg::VsgDbg (Construtor)](vsgdbg-vsgdbg-constructor.md)