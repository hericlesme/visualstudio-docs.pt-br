---
title: 'CA1809: Evitar locais excessivos | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1809
- AvoidExcessiveLocals
helpviewer_keywords:
- AvoidExcessiveLocals
- CA1809
ms.assetid: 5c81ea43-cb49-448f-980f-a1dd9764043c
caps.latest.revision: "19"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 8a21f6f7b24151bc1696c409c940cf8e017f9569
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ca1809-avoid-excessive-locals"></a>CA1809: evitar locais excessivos
|||  
|-|-|  
|NomeDoTipo|AvoidExcessiveLocals|  
|CheckId|CA1809|  
|Categoria|Microsoft.Performance|  
|Alteração Significativa|Não recentes|  
  
## <a name="cause"></a>Causa  
 Um membro contém mais de 64 variáveis locais, alguns dos quais podem ser geradas pelo compilador.  
  
## <a name="rule-description"></a>Descrição da Regra  
 É uma otimização de desempenho comuns para armazenar um valor em um registro de processador, em vez de na memória, o que é conhecido como *registro* o valor. O common language runtime considera até 64 variáveis locais para enregistration. Variáveis que não estão registrado são colocadas na pilha e devem ser movidas para um registro antes de manipulação. Para permitir a chance de que todas as variáveis locais obter registrado, limitar o número de variáveis locais a 64.  
  
## <a name="how-to-fix-violations"></a>Como Corrigir Violações  
 Para corrigir uma violação desta regra, Refatore a implementação para usar não mais do que 64 variáveis locais.  
  
## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos  
 É seguro para suprimir um aviso dessa regra, ou para desabilitar a regra, se o desempenho não for um problema.  
  
## <a name="related-rules"></a>Regras relacionadas  
 [CA1804: remover locais não usados](../code-quality/ca1804-remove-unused-locals.md)