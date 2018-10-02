---
title: Exibição de Linhas – Dados de Amostragem | Microsoft Docs
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
- Lines view
ms.assetid: 46497249-c797-42c5-a02c-3e4bb3b4ee60
caps.latest.revision: 16
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 07ad23e1b7b466965efe16c23f92adc6b9f676dc
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47462966"
---
# <a name="lines-view---sampling-data"></a>Exibição de linhas – Dados de Amostragem
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [exibição de linhas - dados de amostragem](https://docs.microsoft.com/visualstudio/profiling/lines-view-sampling-data).  
  
A visualização Linhas de dados de amostragem lista os dados de desempenho das instruções que estavam em execução quando os exemplos foram coletados na criação de perfil.  
  
> [!NOTE]
>  Os recursos de segurança aprimorados no Windows 8 e no Windows Server 2012 exigiram alterações significativas na maneira como o criador de perfil do Visual Studio coleta dados nessas plataformas. Os aplicativos da Windows Store também requerem novas técnicas de coleta. Consulte [Ferramentas de desempenho em aplicativos do Windows 8 e do Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
 Em um arquivo de origem, uma instrução pode abranger mais de uma linha em um arquivo de origem, e uma única linha pode incluir mais de uma instrução. Uma instrução é identificada pelo seguinte:  
  
-   O arquivo de origem que contém a instrução da função.  
  
-   A função que contém a instrução.  
  
-   A linha de origem em que a instrução se inicia.  
  
-   O caractere na linha de origem em que a instrução se inicia.  
  
-   A linha de origem em que a instrução termina.  
  
-   O caractere na linha de origem em que a instrução termina.  
  
 A coluna de Nome de Linha fornece uma concatenação classificável dos dados do identificador.  
  
 Por definição, uma instrução não chama outras funções. Portanto, apenas valores exclusivos são listados.  
  
|Column|Descrição|  
|------------|-----------------|  
|**ID do Processo**|A ID de processo (PID) da criação de perfil.|  
|**Nome do Processo**|O nome do processo.|  
|**Nome do Módulo**|O nome do módulo que contém a linha de função.|  
|**Caminho do Módulo**|O caminho do módulo que contém a linha de função.|  
|**Arquivo de Origem**|O arquivo de origem que contém a linha de função.|  
|**Nome da Função**|O nome da função.|  
|**Número de linha da função**|O número de linha do início dessa função no arquivo de origem.|  
|**Endereço da Função**|O endereço inicial da função.|  
|**Início da Linha de Origem**|O número de linha inicial no arquivo de origem em que esse exemplo foi coletado.|  
|**Final da Linha de Origem**|O número de linha final no arquivo de origem em que esse exemplo foi coletado.|  
|**Início do Caractere de Origem**|O deslocamento do caractere inicial na linha do arquivo de origem em que esse exemplo foi coletado.|  
|**Final do Caractere de Origem**|O deslocamento do caractere final na linha do arquivo de origem em que esse exemplo foi coletado.|  
|**Nome da Linha**|Um identificador gerado pelo criador de perfil da linha com a seguinte sintaxe: `Source File`**;[**`Line Number Start`**,**`Character Start`**]->;[**`Line Number End`**,**`Character End`**]**|  
|**Amostras Exclusivas**|O número total de amostras coletadas durante a execução da linha de função.|  
|**% de Amostras Exclusivas**|O percentual de todas as amostras coletadas na criação de perfil durante a execução da linha de função.|  
  
## <a name="see-also"></a>Consulte também  
 [Exibição de Linhas – Amostragem](../profiling/lines-view-dotnet-memory-sampling-data.md)



