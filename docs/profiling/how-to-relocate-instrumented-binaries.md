---
title: "Como realocar binários instrumentados | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.performance.property.binaries
helpviewer_keywords:
- binaries, instrumented
- instrumentation, instrumented binaries
- instrumented binaries and relocating
- profiling tools, instrumented binaries
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 364d6695738cb646397895cead518d640497652f
ms.sourcegitcommit: 36ab8429333b31f03992a9fe8fc669db8e09c968
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/21/2018
---
# <a name="how-to-relocate-instrumented-binaries"></a>Como realocar binários instrumentados

Durante a instrumentação, as investigações são inseridas no binário para medir o desempenho do aplicativo. Ao escolher realocar o binário instrumentado, uma cópia do binário original é instrumentada e colocada no local especificado. Essa opção será útil se você não quiser que o criador de perfil renomeie o binário original. Se o binário não for realocado, a versão original do binário será substituída.

## <a name="to-relocate-instrumented-binary"></a>Para realocar binários instrumentados

1. No **Gerenciador de Desempenho**, clique com o botão direito do mouse na sessão de desempenho e, em seguida, clique em **Propriedades**.

2. Nas **Páginas de propriedades**, clique nas propriedades do **Binário**.

3. Selecione a caixa de seleção **Realocar binários instrumentados**.

4. Especifique o local para o binário instrumentado.

## <a name="see-also"></a>Consulte também

[Configurando sessões de desempenho](../profiling/configuring-performance-sessions.md)  
[VSInstr](../profiling/vsinstr.md)
