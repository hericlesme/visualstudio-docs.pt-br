---
title: "Como filtrar relatórios da linha de comando | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6e9b140f-b44f-4a5c-bd65-d868ddc94023
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 27309a459128e6ed9ebb17d295bc39c6c621dcd3
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-filter-reports-from-the-command-line"></a>Como filtrar relatórios a partir da linha de comando
Ao usar as opções para o comando **VSPerfReport**, você pode filtrar relatórios para um segmento de tempo específico do arquivo de dados de criação de perfil ou restringir os dados a um ou mais processos ou threads. Para obter mais informações sobre esse comando, consulte [VSPerfReport](../profiling/vsperfreport.md).  
  
|Opções|Descrição|  
|-------------|-----------------|  
|**StartTime:**[*Value*]|Mostrar somente dados coletados após o valor (em milésimos de segundos.)|  
|**EndTime:**[*Value*]|Mostrar apenas dados coletados antes do valor (em milésimos de segundos.)|  
|**FilterFile:** `VSPFFile`|Especifica o local de um arquivo de filtro que foi gerado da janela **Relatório de desempenho do Visual Studio**.|  
|**MsFilter:**[*StartTime,Duration*]|Mostrar somente os dados de `StartTime` até a duração de `Duration` (em milésimos de segundos).|  
|**Process:**[*Pid*]|Mostrar somente os dados do processo especificado.|  
|**Thread:**[*ThreadID*]|Mostrar somente os dados do thread especificado.|  
|**Thread:**[*ThreadID,ProcessID*]|Mostrar somente os dados do thread especificado associados ao processo especificado.|