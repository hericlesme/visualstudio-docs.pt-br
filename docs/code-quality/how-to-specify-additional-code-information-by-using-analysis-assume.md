---
title: Como especificar informações de código adicionais usando __analysis_assume
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- __analysis_assume
helpviewer_keywords:
- __analysis_assume
ms.assetid: 51205d97-4084-4cf4-a5ed-3eeaf67deb1b
author: mikeblome
ms.author: mblome
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: 181f9fb4a1f9f5d653d64fb813b974bad898fe13
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-specify-additional-code-information-by-using-analysisassume"></a>Como especificar informações de código adicionais usando __analysis_assume
Você pode fornecer dicas para a ferramenta de análise de código para código C/C++ que ajudarão o processo de análise e reduzir avisos. Para fornecer informações adicionais, use a seguinte função:

 `__analysis_assume(`  `expr`  `)`

 `expr` -qualquer expressão que deve ser avaliada como true.

 A ferramenta de análise de código pressupõe que a condição representada pela expressão for verdadeira no ponto em que a função é exibida e permanece válido até que a expressão for alterada, por exemplo, por atribuição a uma variável.

> [!NOTE]
>  `__analysis_assume` não afeta a otimização de código. Fora a ferramenta de análise de código, `__analysis_assume` é definido como não operacional.

## <a name="example"></a>Exemplo
 O código a seguir usa `__analysis_assume` para corrigir o aviso de análise de código [C6388](../code-quality/c6388.md):

```
#include<windows.h>
#include<codeanalysis\sourceannotations.h>

using namespace vc_attributes;

// calls free and sets ch to null
void FreeAndNull(char* ch);

//requires pc to be null
void f([Pre(Null=Yes)] char* pc);

void test( )
{
  char *pc = (char*)malloc(5);
  FreeAndNull(pc);
  __analysis_assume(pc == NULL);
  f(pc);
}
```

## <a name="see-also"></a>Consulte também
 [__assume](/cpp/intrinsics/assume)