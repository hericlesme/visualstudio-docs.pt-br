---
title: Anotando estruturas e Classes | Microsoft Docs
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
- _Field_size_bytes_part_
- _Field_size_bytes_full_opt_
- _Field_size_bytes_
- _Field_size_opt_
- _Field_size_part_
- _Field_size_bytes_part_opt_
- _Field_range_
- _Field_size_part_opt_
- _Field_size_
- _Field_size_bytes_opt_
- _Struct_size_bytes_
- _Field_size_bytes_full_
- _Field_size_full_
- _Field_size_full_opt_
ms.assetid: b8278a4a-c86e-4845-aa2a-70da21a1dd52
caps.latest.revision: 11
author: corob-msft
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 24ed559321bb63d5f9871193f312356466756429
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47465283"
---
# <a name="annotating-structs-and-classes"></a>Anotando estruturas e classes
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [anotando estruturas e Classes](https://docs.microsoft.com/visualstudio/code-quality/annotating-structs-and-classes).  
  
Você pode anotar os membros de classe e struct usando anotações que atuam como as invariáveis — elas são presumidos como verdadeiro em qualquer chamada de função ou entrada/saída da função que envolve a estrutura de inclusão como um parâmetro ou um valor de resultado.  
  
## <a name="struct-and-class-annotations"></a>Anotações de classe e struct  
  
-   `_Field_range_(low, high)`  
  
     O campo está no intervalo (inclusivo) de `low` para `high`.  Equivalente a `_Satisfies_(_Curr_ >= low && _Curr_ <= high)` aplicado ao objeto anotado usando as condições apropriadas de pré ou pós-implantação.  
  
-   `_Field_size_(size)`, `_Field_size_opt_(size)`, `_Field_size_bytes_(size)`, `_Field_size_bytes_opt_(size)`  
  
     Um campo que tem um tamanho gravável em elementos (ou bytes) como especificado pelo `size`.  
  
-   `_Field_size_part_(size, count)`, `_Field_size_part_opt_(size, count)`,         `_Field_size_bytes_part_(size, count)`, `_Field_size_bytes_part_opt_(size, count)`  
  
     Um campo que tem um tamanho gravável em elementos (ou bytes) como especificado pelo `size`e o `count` desses elementos (bytes) que são legíveis.  
  
-   `_Field_size_full_(size)`, `_Field_size_full_opt_(size)`, `_Field_size_bytes_full_(size)`, `_Field_size_bytes_full_opt_(size)`  
  
     Um campo que tem o tamanho legível e gravável em elementos (ou bytes) como especificado pelo `size`.  
  
-   `_Struct_size_bytes_(size)`  
  
     Um campo que tem o tamanho legível e gravável em elementos (ou bytes) como especificado pelo `size`.  
  
     Aplica-se a declaração de classe ou struct.  Indica que um objeto válido desse tipo pode ser maior do que o tipo declarado, com o número de bytes especificado pela `size`.  Por exemplo:  
  
    ```cpp  
  
    typedef _Struct_size_bytes_(nSize)  
    struct MyStruct {  
        size_t nSize;  
        …  
    };  
  
    ```  
  
     O tamanho do buffer em bytes de um parâmetro `pM` do tipo `MyStruct *` , em seguida, será tomado como:  
  
    ```cpp  
    min(pM->nSize, sizeof(MyStruct))  
    ```  
  
## <a name="see-also"></a>Consulte também  
 [Usando anotações de SAL para reduzir defeitos de código C/C++](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)   
 [Noções básicas de SAL](../code-quality/understanding-sal.md)   
 [Anotando parâmetros de função e valores de retorno](../code-quality/annotating-function-parameters-and-return-values.md)   
 [Anotando o comportamento da função](../code-quality/annotating-function-behavior.md)   
 [Anotando o comportamento de bloqueio](../code-quality/annotating-locking-behavior.md)   
 [Especificando quando e onde uma anotação se aplica](../code-quality/specifying-when-and-where-an-annotation-applies.md)   
 [Funções intrínsecas](../code-quality/intrinsic-functions.md)   
 [Práticas recomendadas e exemplos](../code-quality/best-practices-and-examples-sal.md)



