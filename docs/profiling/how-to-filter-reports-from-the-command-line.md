---
title: Como filtrar relatórios da linha de comando | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 6e9b140f-b44f-4a5c-bd65-d868ddc94023
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0591b646c8311004d9c08b2fb1a9fcdf2ab1908a
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/19/2018
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