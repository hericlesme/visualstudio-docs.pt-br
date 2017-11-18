---
title: "Visão geral (Debug Interface Access SDK) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- user-defined types
- .dbg files
- modules
- interfaces [DIA SDK]
- DBG files
- procedures [DIA SDK]
- executable files
- COM objects, in DIA SDK
- compilands
- executable images
ms.assetid: 720b4479-a8bc-4fec-860e-80c1a0780405
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d4cd0206e402600cbe9002c931adb7ff6a2cc680
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="overview-debug-interface-access-sdk"></a>Visão geral (SDK de Acesso à Interface de Depuração)
Use o SDK do DIA para acessar as informações de depuração da Microsoft. O DIA SDK fornece uma COM baseado em conjunto de APIs que elimina a necessidade de reconfigurar seu código sempre que a Microsoft altera o formato das informações de depuração. O DIA SDK também permite que você ler um conjunto selecionado de versões anteriores de informações de depuração, localizado em arquivos. PDB e. dbg gerados por [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] versões 5.0 e versões posteriores.  
  
 Cada interface no DIA SDK representa um objeto COM diferentes, exceto quando indicado de outra forma. Interfaces adicionais e, portanto, objetos adicionais, são criados por meio de consultas explícitas, como [: Opensession](../../debugger/debug-interface-access/idiadatasource-opensession.md) ou [: Findchildren](../../debugger/debug-interface-access/idiasession-findchildren.md), em vez de chamar `QueryInterface` em ponteiros de interface existente.  
  
## <a name="see-also"></a>Consulte também  
 [: Opensession](../../debugger/debug-interface-access/idiadatasource-opensession.md)   
 [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)