---
title: 'CA2103: revisar segurança obrigatória'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2103
- ReviewImperativeSecurity
helpviewer_keywords:
- CA2103
- ReviewImperativeSecurity
ms.assetid: d24fde71-bdf6-46c0-8965-9a73dc33c1aa
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d107690e8835f118861832da99b4aef92e86a5cc
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/19/2018
---
# <a name="ca2103-review-imperative-security"></a>CA2103: revisar segurança obrigatória
|||
|-|-|
|NomeDoTipo|ReviewImperativeSecurity|
|CheckId|CA2103|
|Categoria|Microsoft.Security|
|Alteração Significativa|Quebra|

## <a name="cause"></a>Causa
 Um método usa segurança obrigatória e pode construir a permissão usando as informações de estado ou os valores de retorno que podem ser alterados desde que a demanda esteja ativa.

## <a name="rule-description"></a>Descrição da Regra
 Segurança obrigatória usa objetos gerenciados para especificar permissões e ações de segurança durante a execução de código, em comparação comparada a segurança declarativa, que usa atributos para armazenar permissões e ações nos metadados. Segurança obrigatória é muito flexível, porque você pode definir o estado de um objeto de permissão e selecione as ações de segurança usando as informações que não estão disponíveis até o tempo de execução. Junto com que a flexibilidade vem o risco de que as informações de tempo de execução que você pode usar para determinar que o estado de uma permissão não permanecem inalteradas desde que a ação está em vigor.

 Use a segurança declarativa sempre que possível. As solicitações declarativas são mais fáceis de entender.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Examine as demandas de segurança obrigatória para certificar-se de que o estado da permissão não se baseia em informações que podem ser alterados desde que a permissão está sendo usada.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 É seguro suprimir um aviso de que essa regra se a permissão não depende de alteração de dados. No entanto, é melhor alterar a demanda fundamental para seu equivalente declarativa.

## <a name="see-also"></a>Consulte também
 [Diretrizes de codificação segura](/dotnet/standard/security/secure-coding-guidelines) [dados e modelagem](/dotnet/framework/data/index)