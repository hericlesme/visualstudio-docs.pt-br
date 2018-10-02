---
title: Como realocar binários instrumentados | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.performance.property.binaries
helpviewer_keywords:
- binaries, instrumented
- instrumentation, instrumented binaries
- instrumented binaries and relocating
- profiling tools, instrumented binaries
ms.assetid: 258f49e8-4b09-477e-a132-8fad685b66f4
caps.latest.revision: 23
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3114ee88feefdbb409ed1a1e1ad025a18123c002
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47473700"
---
# <a name="how-to-relocate-instrumented-binaries"></a>Como realocar binários instrumentados
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [como: realocar binários instrumentados](https://docs.microsoft.com/visualstudio/profiling/how-to-relocate-instrumented-binaries).  
  
Durante a instrumentação, as investigações são inseridas no binário para medir o desempenho do aplicativo. Ao escolher realocar o binário instrumentado, uma cópia do binário original é instrumentada e colocada no local especificado. Essa opção será útil se você não quiser que o criador de perfil renomeie o binário original. Se o binário não for realocado, a versão original do binário será substituída.  
  
 **Requisitos**  
  
-   [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
### <a name="to-relocate-instrumented-binary"></a>Para realocar binários instrumentados  
  
1.  No **Gerenciador de Desempenho**, clique com o botão direito do mouse na sessão de desempenho e, em seguida, clique em **Propriedades**.  
  
2.  Nas **Páginas de propriedades**, clique nas propriedades do **Binário**.  
  
3.  Selecione a caixa de seleção **Realocar binários instrumentados**.  
  
4.  Especifique o local para o binário instrumentado.  
  
## <a name="see-also"></a>Consulte também  
 [Configurando sessões de desempenho](../profiling/configuring-performance-sessions.md)   
 [VSInstr](../profiling/vsinstr.md)



