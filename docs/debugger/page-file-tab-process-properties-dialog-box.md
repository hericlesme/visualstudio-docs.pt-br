---
title: "Guia do arquivo de paginação, caixa de diálogo de propriedades do processo | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: Process properties for Windows NT
ms.assetid: daf41a06-8a55-48f6-95f5-49a8416bd308
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 12cf35a2043764a4b174b5e45fcbe1bc83a72a52
ms.sourcegitcommit: 9e6ff74da1afd8bd2f0e69387ce81f2a74619182
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/04/2018
---
# <a name="page-file-tab-process-properties-dialog-box"></a>Guia Arquivo de Paginação, Caixa de diálogo Propriedades do Processo
Use o **arquivo de paginação** guia para examinar o arquivo de paginação de um processo. Para exibir o [caixa de diálogo de propriedades do processo](../debugger/process-properties-dialog-box.md), mova o foco para um [exibição processos](../debugger/processes-view.md) janela. Selecione qualquer nó de processo na árvore e escolha **propriedades** do **exibição** menu.  
  
 As configurações a seguir estão disponíveis no **arquivo de paginação** guia:  
  
|Entrada|Descrição|  
|-----------|-----------------|  
|**Bytes de arquivo de paginação**|O número atual de páginas que esse processo está usando o arquivo de paginação. O arquivo de paginação armazena as páginas de dados usada pelo processo, mas não contidas em outros arquivos. O arquivo de paginação é usado por todos os processos e falta de espaço no arquivo de paginação pode causar erros durante a execução de outros processos.|  
|**Máximo de Bytes de arquivo de paginação**|O número máximo de páginas que este processo usou no arquivo de paginação.|  
|**Falhas de página**|O número de falhas de página por segmentos em execução neste processo. Uma falha de página ocorre quando um thread faz referência a uma página de memória virtual que não está no conjunto de trabalho na memória principal. Portanto, a página não será recuperada do disco se ele estiver na lista de espera e, portanto, já na memória principal, ou se ele está sendo usado por outro processo com o qual a página é compartilhada.|