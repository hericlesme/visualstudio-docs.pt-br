---
title: Avisos de facilidade de manutenção
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- vs.codeanalysis.maintainabilityrules
helpviewer_keywords:
- warnings, maintainability
- managed code analysis warnings, maintainability warnings
- maintainability warnings
ms.assetid: 537e70ca-a88c-49df-bfc7-0ee63bbe4f16
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 058dca04aba85a8c00e5f587deccf0940f71d4c5
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31919997"
---
# <a name="maintainability-warnings"></a>Avisos de facilidade de manutenção
Avisos de facilidade de manutenção suporte à manutenção de biblioteca e o aplicativo.

## <a name="in-this-section"></a>Nesta seção

|Regra|Descrição|
|----------|-----------------|
|[CA1500: os nomes de variável não devem corresponder aos nomes de campo](../code-quality/ca1500-variable-names-should-not-match-field-names.md)|Um método de instância declara um parâmetro ou uma variável local cujo nome corresponda a um campo de instância do tipo declarativo, que leva a erros.|
|[CA1501: evitar herança excessiva](../code-quality/ca1501-avoid-excessive-inheritance.md)|Um tipo está mais de quatro níveis abaixo na hierarquia de herança. As hierarquias de tipo profundamente aninhado podem ser difíceis de seguir, compreender e manter.|
|[CA1502: evitar complexidade excessiva](../code-quality/ca1502-avoid-excessive-complexity.md)|Esta regra mede o número de caminhos linearmente independentes por meio do método, o que é determinado pelo número e pela complexidade das ramificações condicionais.|
|[CA1504: examinar nomes de campo confusos](../code-quality/ca1504-review-misleading-field-names.md)|O nome de um campo de instância começa com "s _", ou o nome de um estático (compartilhado no [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) campo começa com "m _".|
|[CA1505: evitar código que não possa ser mantido](../code-quality/ca1505-avoid-unmaintainable-code.md)|Um tipo ou um método tem um baixo valor de índice de facilidade de manutenção. Um baixo índice de facilidade de manutenção indica que um tipo ou um método é provavelmente difícil de manter e seria um bom candidato para um novo design.|
|[CA1506: evitar acoplamento de classes excessivo](../code-quality/ca1506-avoid-excessive-class-coupling.md)|Esta regra mede o acoplamento de classes contando o número de referências de tipo exclusivas que um tipo ou um método contém.|

## <a name="see-also"></a>Consulte também
 [Medindo complexidade e facilidade de manutenção do código gerenciado](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)