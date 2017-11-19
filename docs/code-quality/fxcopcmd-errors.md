---
title: Erros de FxCopCmd | Microsoft Docs
ms.custom: 
ms.date: 10/19/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: FxCopCmd errors
ms.assetid: bb614ed0-1b7c-4b56-99ae-da50ef6cfef9
caps.latest.revision: "12"
ms.author: gewarren
author: gewarren
manager: ghogen
ms.openlocfilehash: 2439b04c921de6e06b98bd1bb5a9fc0af3ea56d1
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="fxcopcmd-errors"></a>Erros (FxCopCmd)
FxCopCmd não considera todos os erros para ser fatal. Se FxCopCmd tem informações suficientes para executar uma análise parcial, ele executa as análise e relatórios de erros que ocorreram. O código de erro, que é um inteiro de 32 bits, contém uma combinação bit a bit de valores numéricos que correspondem a erros.  
  
 A tabela a seguir descreve os códigos de erro retornados por FxCopCmd:  
  
|Erro|Valor numérico|  
|-----------|-------------------|  
|Sem erros|0x0|  
|Erro de análise|0x1|  
|Exceções de regra|0x2|  
|Erro ao carregar projeto|0x4|  
|Erro ao carregar assembly|0x8|  
|Erro ao carregar biblioteca regra|0x10|  
|Erro de carregamento do relatório de importação|0x20|  
|Erro de saída|0x40|  
|Erro de chave de linha de comando|0x80|  
|Erro de inicialização|0x100|  
|Erro de referências de assembly|0x200|  
|BuildBreakingMessage|0x400|  
|Erro desconhecido|0x1000000|  
  
 O erro de análise será retornado para erros fatais. Ele indica que não foi possível concluir a análise. Quando aplicável, o código de erro também contém a causa do erro fatal. As condições a seguir geram erros fatais:  
  
-   Não foi possível executar a análise causado pela entrada insuficiente.  
  
-   A análise gerou uma exceção não tratada pelo FxCopCmd.  
  
-   O arquivo de projeto especificado não pôde ser encontrado ou está corrompido.  
  
-   A opção de saída não foi especificada ou não foi possível gravar o arquivo.  
  
    > [!NOTE]
    >  Código de retorno ao FxCopCmd "Erro de referências de Assembly" 0x200 por si só é um aviso em vez de um erro. O código de retorno indica que as referências indiretas ausentes foram encontradas, mas que FxCopCmd foi capaz de lidar com eles. É um aviso de que há uma possibilidade de que alguns resultados de análise podem ter sido comprometidos. Considere o código de retorno de "Erro de referências de Assembly" como um erro quando ele é combinado com qualquer outro código de retorno.  
  
## <a name="see-also"></a>Consulte também  
 [Erros de aplicativo de análise de código](../code-quality/code-analysis-application-errors.md)