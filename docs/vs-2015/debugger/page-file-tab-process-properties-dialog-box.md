---
title: Guia arquivo de paginação, caixa de diálogo de propriedades do processo | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Process properties for Windows NT
ms.assetid: daf41a06-8a55-48f6-95f5-49a8416bd308
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2fa1eba7af60638d82c791958af6bf66a3272242
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47473471"
---
# <a name="page-file-tab-process-properties-dialog-box"></a>Guia Arquivo de Paginação, Caixa de diálogo Propriedades do Processo
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [guia arquivo de paginação, caixa de diálogo de propriedades do processo](https://docs.microsoft.com/visualstudio/debugger/page-file-tab-process-properties-dialog-box).  
  
Use o **arquivo de paginação** guia para examinar o arquivo de paginação de um processo. Para exibir o [caixa de diálogo de propriedades do processo](../debugger/process-properties-dialog-box.md), mova o foco para um [exibição de processos](../debugger/processes-view.md) janela. Selecione qualquer nó de processo na árvore e escolha **propriedades** da **exibição** menu.  
  
 As configurações a seguir estão disponíveis na **arquivo de paginação** guia:  
  
|Entrada|Descrição|  
|-----------|-----------------|  
|**Bytes de arquivo de paginação**|O número atual de páginas que esse processo está usando no arquivo de paginação. O arquivo de paginação armazena as páginas de dados usado pelo processo, mas não está contido em outros arquivos. O arquivo de paginação é usado por todos os processos e falta de espaço no arquivo de paginação pode causar erros durante a execução de outros processos.|  
|**Bytes de arquivo de paginação de pico**|O número máximo de páginas que esse processo tem usado no arquivo de paginação.|  
|**Falhas de página**|O número de falhas de página por segmentos em execução nesse processo. Uma falha de página ocorre quando um thread faz referência a uma página de memória virtual que não está no conjunto de trabalho na memória principal. Portanto, a página não será recuperada do disco se ele estiver na lista de espera e, portanto, já na memória principal, ou se ele está sendo usado por outro processo com a página é compartilhada.|



