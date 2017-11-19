---
title: "Como: habilitar e desabilitar análise de código automática para código gerenciado | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7c22d194-5fea-4f23-b02d-19344fa64a64
caps.latest.revision: "8"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: ad960a490d92e84efdfbd73e9aa23d7b41dc0dd1
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-enable-and-disable-automatic-code-analysis-for-managed-code"></a>Como habilitar e desabilitar análise de código automática para código gerenciado
Você pode configurar a análise de código para ser executado antes de cada compilação de um projeto de código gerenciado. Você pode definir propriedades de análise de código diferentes para cada [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] configuração.  
  
### <a name="to-enable-or-disable-automatic-code-analysis"></a>Para habilitar ou desabilitar a análise de código automática  
  
1.  Em **Solution Explorer**, clique com o botão direito e, em seguida, clique em **propriedades**.  
  
2.  Na caixa de diálogo Propriedades do projeto, clique em **análise de código**.  
  
3.  Especifique o tipo de compilação em **configuração** e a plataforma de destino em **plataforma**.  
  
4.  Para habilitar ou desabilitar análise de código automático, marque ou desmarque o **habilitar análise de código no Build (define a constante CODE_ANALYSIS)** caixa de seleção.