---
title: Guia memória, caixa de diálogo de propriedades do processo | Microsoft Docs
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
- Process properties for Windows NT
ms.assetid: a70785f2-5997-40ec-a90f-80a52449768b
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 45d7933b70555a3c80a094ea8cd3f982e232f5de
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47462327"
---
# <a name="memory-tab-process-properties-dialog-box"></a>Guia Memória, Caixa de diálogo Propriedades do Processo
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [guia de memória, caixa de diálogo de propriedades do processo](https://docs.microsoft.com/visualstudio/debugger/memory-tab-process-properties-dialog-box).  
  
Use o **memória** guia para mostrar como um processo usa memória. Para exibir o [caixa de diálogo de propriedades do processo](../debugger/process-properties-dialog-box.md), mova o foco para um [exibição de processos](../debugger/processes-view.md) janela. Selecione qualquer nó de processo na árvore e escolha **propriedades** da **exibição** menu.  
  
 As seguintes configurações estão disponíveis sobre o **memória** guia:  
  
|Entrada|Descrição|  
|-----------|-----------------|  
|**Bytes virtuais**|O tamanho atual (em bytes) de espaço de endereço virtual que o processo está usando. O uso do espaço de endereço virtual não implica necessariamente o uso correspondente de disco ou páginas de memória principal. No entanto, o espaço virtual é finito e muito usando pode limitar a capacidade do processo de carregar bibliotecas.|  
|**Bytes virtuais de pico**|O número máximo de bytes de espaço de endereço virtual o processo usou a qualquer momento.|  
|**Conjunto de trabalho**|O conjunto de páginas de memória utilizadas recentemente pelos threads no processo. Se a memória livre no computador está acima do limite, páginas são deixadas no conjunto de trabalho de um processo, mesmo se eles não estão em uso. Quando a memória livre fica abaixo do limite, as páginas serão retiradas do conjunto de trabalho. Se forem necessários, eles serão ser reinseridas no conjunto de trabalho antes de sair da memória principal.|  
|**Conjunto de trabalho de pico**|O número máximo de páginas no conjunto de trabalho desse processo em qualquer ponto no tempo.|  
|**Bytes de Pool paginável**|A quantidade atual de pool paginável que o processo alocou. Pool paginado é uma área de memória do sistema em que componentes do sistema operacional adquirem espaço conforme eles realizam suas tarefas indicadas. Páginas de memória paginável podem ser paginadas para o arquivo de paginação quando não são acessados pelo sistema para períodos de tempo toleráveis.|  
|**Bytes de Pool não paginável**|O número atual de bytes de pool não paginável alocada pelo processo. O pool não-paginável é uma área de memória do sistema onde o espaço é adquirido por componentes do sistema operacional conforme eles realizam suas tarefas indicadas. Páginas de pool não paginável não podem ser paginadas para o arquivo de paginação; eles permanecem na memória principal enquanto estiverem alocados.|  
|**Bytes particulares**|O número atual de bytes, alocada ao processo que não pode ser compartilhado com outros processos.|  
|**Bytes livres**|O espaço total de endereço virtual não utilizado desse processo.|  
|**Bytes reservados**|A quantidade total de memória virtual reservada para uso futuro por esse processo.|  
|**Bytes de imagens livres**|A quantidade de espaço de endereço virtual que não está em uso ou reservada por imagens no processo.|  
|**Bytes de imagens reservadas**|A soma de toda a memória virtual reservada por imagens executadas dentro do processo.|



