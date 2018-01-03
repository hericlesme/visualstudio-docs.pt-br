---
title: "Como criar um relatório ETW das ferramentas de criação de perfil | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bf5547b3-f6c7-4989-9d47-2fe4f1261444
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 30447d92c42afc48a02a7faac3baad6146858771
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-profiling-tools-etw-report"></a>Como criar um relatório ETW das ferramentas de criação de perfil
O Relatório de Rastreamento de Eventos para Windows (ETW) lista os eventos ETW que são registrados em uma sessão de desempenho de Ferramentas de Criação de Perfil [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Dados de ETW são coletados em um arquivo binário (.etl). Para obter mais informações sobre este relatório, consulte [Relatório de Rastreamento de Eventos para Windows (ETW)](../profiling/event-tracing-for-windows-etw-report.md).  
  
> [!NOTE]
>  Não é possível exibir relatórios ETW na interface para [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
-   Para obter informações sobre como coletar dados ETW por meio da interface de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], consulte [Como coletar dados de Rastreamento de Eventos para Windows (ETW)](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md).  
  
-   Para obter informações sobre como coletar dados de ETW de um prompt de comando, consulte [VSPerfCmd](../profiling/vsperfcmd.md) e [Eventos](../profiling/events-vsperfcmd.md).  
  
 O relatório de ETW é gerado usando o comando **VSReport/summary:etw**. O .etl que contém os dados de ETW deve estar no mesmo diretório que o arquivo com os dados de criação de perfil (.vsp ou .vsps). Por padrão, o relatório é gerado como um arquivo de valores separados por vírgula (.csv). Para obter mais informações, confira [VSPerfReport](../profiling/vsperfreport.md).  
  
### <a name="to-generate-an-etw-report"></a>Para criar um relatório ETW  
  
-   Em uma janela de **Prompt de Comando**, digite a seguinte linha de comando:  
  
     *ToolsPath* **VSPerfReport** *VSPFile*  **/Summary:ETW [/Xml]**  
  
    |||  
    |-|-|  
    |*ToolsPath*|O caminho do utilitário de Ferramentas de Criação de Perfil. Para obter mais informações, consulte [Especificando o caminho para ferramentas de linha de comando](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).|  
    |*VSPFile*|Os dados de criação de perfil (arquivo .vsp ou .vsps). Caminhos completos e parciais são aceitos.|  
    |Xml|Gera um relatório que é formatado em XML.|