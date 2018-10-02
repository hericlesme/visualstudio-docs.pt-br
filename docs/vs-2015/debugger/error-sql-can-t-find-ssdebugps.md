---
title: 'Erro: SQL pode&#39;t consegue localizar SSDEBUGPS | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.error.sqlde_cant_find_ssdebugps
dev_langs:
- FSharp
- VB
- CSharp
- C++
- SQL
ms.assetid: 596425c8-14c7-4c05-8823-e1c52f420f5e
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1782412ded2c4edff0da29b13160107664170d20
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47474012"
---
# <a name="error-sql-can39t-find-ssdebugps"></a>Erro: SQL pode&#39;t consegue localizar SSDEBUGPS
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [erro: SQL pode&#39;t localizar SSDEBUGPS](https://docs.microsoft.com/visualstudio/debugger/error-sql-can-t-find-ssdebugps).  
  
SSDEBUGPS.dll é o componente do host de depuração do SQL Server.  
  
 Esse erro ocorre quando você está tentando iniciar a depuração e indica que o arquivo especificado não está presente no computador do [!INCLUDE[sqprsqlong](../includes/sqprsqlong-md.md)]. As causas possíveis são que a instalação da Depuração Remota nunca foi executada ou que de alguma forma esse arquivo foi excluído.  
  
 Há duas maneiras de resolver esse erro: executando novamente a instalação da depuração remota e copiando o arquivo para o [!INCLUDE[sqprsqlong](../includes/sqprsqlong-md.md)] máquina.  
  
 Para executar novamente a instalação da depuração remota, siga as instruções em [depuração remota](../debugger/remote-debugging.md).  
  
 Se você puder localizar uma cópia de ssdebugps. dll, você pode copiá-lo no [!INCLUDE[sqprsqlong](../includes/sqprsqlong-md.md)] máquina. Se houver, o arquivo estará no diretório \Arquivos de Programas\ Common Files\Microsoft Shared\SQL Debugging. Você pode encontrá-lo em outro [!INCLUDE[sqprsqlong](../includes/sqprsqlong-md.md)] computador, ou em um computador que tenha [!INCLUDE[vsprvslong](../includes/vsprvslong-md.md)] instalado.  
  
### <a name="to-copy-ssdebugpsdll-onto-the-sql-server-2005-machine"></a>Para copiar o SSDEBUGPS.dll no computador do SQL Server 2005  
  
1.  Copie o arquivo para o diretório com o mesmo nome e caminho no [!INCLUDE[sqprsqlong](../includes/sqprsqlong-md.md)] máquina.  
  
2.  Registre-o abrindo uma **Prompt de comando**e executando o seguinte comando:  
  
    ```  
    regsrv32 ssdebugps.dll  
    ```



