---
title: Operadores lógicos em expressões de pesquisa | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Help Viewer 2.0, logical operators in search
- logical operators in search [Help Viewer 2.0]
ms.assetid: 0c38ae7d-3e20-4d47-a020-9677cd285916
caps.latest.revision: 11
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 0cf55bbdc025b4aabd13f7ded72c2ea69386a61b
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47462149"
---
# <a name="logical-operators-in-search-expressions"></a>Operadores lógicos em expressões de pesquisa
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [operadores lógicos em expressões de pesquisa](https://docs.microsoft.com/visualstudio/ide/logical-operators-in-search-expressions).  
  
Usando operadores lógicos, você pode refinar a pesquisa de conteúdo criando expressões de pesquisa mais complicadas desde mais simples. Como mostra a tabela a seguir, os operadores lógicos especificam como vários termos de pesquisa devem ser combinados em uma consulta de pesquisa.  
  
> [!IMPORTANT]
>  Você deve inserir os operadores lógicos em letras maiúsculas para o mecanismo de pesquisa reconhecê-los.  
  
|Para pesquisar|Use|Exemplo|Resultado|  
|-------------------|---------|-------------|------------|  
|Ambos os termos no mesmo tópico|AND|dib AND paleta|Tópicos que contêm "dib" e "paleta".|  
|Um dos dois termos em um tópico|OU|varredura OR vetor|Tópicos que contêm "varredura" ou "vetor".|  
|Primeiro termo sem um segundo termo no mesmo tópico|NOT|"operating system" NOT DOS|Tópicos que contêm "sistema operacional", mas não "DOS".|  
|Os dois termos, próximos em um tópico|PRÓXIMO|usuário NEAR kernel|Tópicos que contêm "usuário" bastante próximo de "kernel".|  
  
## <a name="see-also"></a>Consulte também  
 [Dicas de pesquisa de texto completo](../ide/full-text-search-tips.md)   
 [Localizar informações](../ide/locate-information.md)



