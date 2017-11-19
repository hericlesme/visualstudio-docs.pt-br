---
title: 'Como: suprimir avisos usando o Item de Menu | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- warnings, suppressing
- code analysis, suppressing warnings
ms.assetid: 36bd1850-dcde-4ed0-9bc3-0b83df434362
caps.latest.revision: "24"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: a197170285a8f8a9d3f0cc01638557f30fd1f126
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-suppress-warnings-by-using-the-menu-item"></a>Como suprimir avisos usando o item de menu
> [!NOTE]
>  Na fonte de supressão não tem suporte para projetos de site.  
  
 Você pode usar a janela de análise de código para suprimir avisos da análise de código. Suprimir um aviso não é igual a desabilitá-lo. Quando você suprimir um aviso, ele se aplica somente a uma instância específica da violação. Outras violações do aviso mesmo ainda serão relatadas na janela lista de erros.  
  
 Depois de executar a análise de código, você pode determinar que um ou mais avisos da análise de código que são exibidos na janela análise de código não são aplicáveis ao seu aplicativo. Por exemplo, você pode determinar que o código está correto, como está. Ou então, pode ser o caso que alguns violações são de baixa prioridade e não serão corrigidas no ciclo de desenvolvimento atual. Independentemente do motivo, é muito útil indicar que o aviso não aplicável para permitir que os membros da equipe saber que o código foi revisado e que foi determinado que o aviso pode ser suprimido. Na fonte supressão é útil porque ela permite que você coloque uma supressão perto de onde o aviso é gerado.  
  
 Você pode escolher se a supressão aparecerá no código-fonte ou no arquivo de supressão global. Alguns supressões devem ser colocadas no arquivo de supressão global. Se esse for o caso, o **na origem** opção será desabilitada.  
  
### <a name="to-suppress-a-warning-by-using-menu-item"></a>Para suprimir um aviso usando o item de menu  
  
1.  Sobre o **analisar** menu, escolha **Windows** e, em seguida, escolha **análise de código**.  
  
2.  No **análise de código** janela, selecione suprimir o aviso.  
  
3.  Escolha ações, em seguida, escolha **suprimir mensagem (NS)**e, em seguida, escolha **na origem** ou **no arquivo de supressão do projeto**.  
  
     O aviso específico é suprimido e o aviso é exibido na janela análise de código com um tachado.  
  
> [!NOTE]
>  As supressões que não têm um destino aparecem no arquivo de supressão global.