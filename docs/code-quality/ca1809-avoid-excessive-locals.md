---
title: 'CA1809: evitar locais excessivos'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1809
- AvoidExcessiveLocals
helpviewer_keywords:
- AvoidExcessiveLocals
- CA1809
ms.assetid: 5c81ea43-cb49-448f-980f-a1dd9764043c
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ea0d1d27f583e86a62e9c0ff524d9d623253d007
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31917334"
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