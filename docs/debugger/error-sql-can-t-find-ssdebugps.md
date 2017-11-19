---
title: 'Erro: SQL pode &#39; t localizar SSDEBUGPS | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.error.sqlde_cant_find_ssdebugps
dev_langs:
- CSharp
- VB
- FSharp
- C++
- SQL
ms.assetid: 596425c8-14c7-4c05-8823-e1c52f420f5e
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 43a437cfc4be1c9168b16e4b9d1a46e2eadcb2e6
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="error-sql-can39t-find-ssdebugps"></a>Erro: SQL pode &#39; t localizar SSDEBUGPS
SSDEBUGPS.dll é o componente do host de depuração do SQL Server.  
  
 Esse erro ocorre quando você está tentando iniciar a depuração e indica que o arquivo especificado não está presente no computador do [!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)]. As causas possíveis são que a instalação da Depuração Remota nunca foi executada ou que de alguma forma esse arquivo foi excluído.  
  
 Há duas maneiras de resolver esse erro: executando novamente a instalação de depuração remota e copiando o arquivo para o [!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)] máquina.  
  
 Para executar novamente a instalação de depuração remota, siga as instruções em [depuração remota](../debugger/remote-debugging.md).  
  
 Se você puder localizar uma cópia do ssdebugps.dll, você pode copiá-lo para o [!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)] máquina. Se houver, o arquivo estará no diretório \Arquivos de Programas\ Common Files\Microsoft Shared\SQL Debugging. Talvez você ache em outro [!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)] máquina, ou em um computador que tenha [!INCLUDE[vsprvslong](../code-quality/includes/vsprvslong_md.md)] instalado.  
  
### <a name="to-copy-ssdebugpsdll-onto-the-sql-server-2005-machine"></a>Para copiar o SSDEBUGPS.dll no computador do SQL Server 2005  
  
1.  Copie o arquivo para o diretório com o mesmo nome e caminho no [!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)] máquina.  
  
2.  Registre-o abrindo uma **Prompt de comando**e executando o seguinte comando:  
  
    ```  
    regsrv32 ssdebugps.dll  
    ```