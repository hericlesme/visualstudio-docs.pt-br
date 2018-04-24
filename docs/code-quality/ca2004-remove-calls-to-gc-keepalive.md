---
title: 'CA2004: remover chamadas para GC.KeepAlive'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- RemoveCallsToGCKeepAlive
- CA2004
helpviewer_keywords:
- RemoveCallsToGCKeepAlive
- CA2004
ms.assetid: bc543b5b-23eb-4b45-abc2-9325cd254ac2
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e2f05764f5147a064815cdb744420686fb6a5a7c
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/19/2018
---
# <a name="ca2004-remove-calls-to-gckeepalive"></a>CA2004: remover chamadas para GC.KeepAlive
|||
|-|-|
|NomeDoTipo|RemoveCallsToGCKeepAlive|
|CheckId|CA2004|
|Categoria|Microsoft.Reliability|
|Alteração Significativa|Não recentes|

## <a name="cause"></a>Causa
 Uso de classes `SafeHandle` , mas ainda contêm chamadas para `GC.KeepAlive`.

## <a name="rule-description"></a>Descrição da Regra
 Se você estiver convertendo em `SafeHandle` uso, remova todas as chamadas para `GC.KeepAlive` (object). Nesse caso, não devem ter classes chamar `GC.KeepAlive`, supondo que eles não têm um finalizador, mas dependem `SafeHandle` para concluir o identificador de sistema operacional para eles.  Embora o custo de deixar em uma chamada para `GC.KeepAlive` podem ser muito importantes, conforme medido pelo desempenho, a percepção que uma chamada para `GC.KeepAlive` é necessário ou suficientes para resolver um problema que talvez não exista mais difícil para o código de tempo de vida Manter.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Remover chamadas ao `GC.KeepAlive`.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 Você pode suprimir esse aviso somente se não for tecnicamente correta converter em `SafeHandle` uso na sua classe.