---
title: 'Como: especificar informações de código adicionais usando analysis_assume | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- __analysis_assume
helpviewer_keywords:
- __analysis_assume
ms.assetid: 51205d97-4084-4cf4-a5ed-3eeaf67deb1b
caps.latest.revision: 12
author: corob-msft
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: a08ca5a35d08f284062323f2e75648852debb7bf
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47465771"
---
# <a name="how-to-specify-additional-code-information-by-using-analysisassume"></a>Como especificar informações de código adicionais usando __analysis_assume
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [como: especificar informações de código adicionais usando analysis_assume](https://docs.microsoft.com/visualstudio/code-quality/how-to-specify-additional-code-information-by-using-analysis-assume).  
  
Você pode fornecer dicas para a ferramenta de análise de código para código C/C++ que ajudam no processo de análise e reduzir os avisos. Para fornecer informações adicionais, use a função a seguir:  
  
 `__analysis_assume(`  `expr`  `)`  
  
 `expr` -qualquer expressão supostamente avaliada como true.  
  
 A ferramenta de análise de código pressupõe que a condição representada pela expressão é verdadeira no ponto em que a função aparece e permanece verdadeira até que a expressão for alterada, por exemplo, por atribuição a uma variável.  
  
> [!NOTE]
>  `__analysis_assume` não afeta a otimização de código. Fora a ferramenta de análise de código, `__analysis_assume` é definido como inoperante.  
  
## <a name="example"></a>Exemplo  
 O seguinte código usa `__analysis_assume` para corrigir o aviso de análise de código [C6388](../code-quality/c6388.md):  
  
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
 [__assume](http://msdn.microsoft.com/library/d8565123-b132-44b1-8235-5a8c8bff85a7)



