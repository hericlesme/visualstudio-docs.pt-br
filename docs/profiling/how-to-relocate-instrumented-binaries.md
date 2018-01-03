---
title: "Como realocar binários instrumentados | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.performance.property.binaries
helpviewer_keywords:
- binaries, instrumented
- instrumentation, instrumented binaries
- instrumented binaries and relocating
- profiling tools, instrumented binaries
ms.assetid: 258f49e8-4b09-477e-a132-8fad685b66f4
caps.latest.revision: "18"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 72c15bfc5449a1dab516be217da4a76276312fd3
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-relocate-instrumented-binaries"></a>Como realocar binários instrumentados
Durante a instrumentação, as investigações são inseridas no binário para medir o desempenho do aplicativo. Ao escolher realocar o binário instrumentado, uma cópia do binário original é instrumentada e colocada no local especificado. Essa opção será útil se você não quiser que o criador de perfil renomeie o binário original. Se o binário não for realocado, a versão original do binário será substituída.  
  
 **Requisitos**  
  
-   [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)], [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]  
  
### <a name="to-relocate-instrumented-binary"></a>Para realocar binários instrumentados  
  
1.  No **Gerenciador de Desempenho**, clique com o botão direito do mouse na sessão de desempenho e, em seguida, clique em **Propriedades**.  
  
2.  Nas **Páginas de propriedades**, clique nas propriedades do **Binário**.  
  
3.  Selecione a caixa de seleção **Realocar binários instrumentados**.  
  
4.  Especifique o local para o binário instrumentado.  
  
## <a name="see-also"></a>Consulte também  
 [Configurando sessões de desempenho](../profiling/configuring-performance-sessions.md)   
 [VSInstr](../profiling/vsinstr.md)