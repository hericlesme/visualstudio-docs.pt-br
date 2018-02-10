---
title: "Usando sequências de Escape em modelos de texto | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.topic: article
helpviewer_keywords:
- text templates, escape sequences
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: f6ab5346ed82aadea339bc8ee45ac4a3bfb72c65
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/09/2018
---
# <a name="using-escape-sequences-in-text-templates"></a>Usando sequências de escape em modelos de texto
Você pode usar sequências de escape em modelos de texto para gerar marcas de modelo de texto e (em c# somente código) para caracteres de controle de escape e aspas.  
  
 Para imprimir marcas de abertura e fechamento de um bloco de código padrão para o arquivo de saída, retirar as marcas da seguinte maneira:  
  
```  
\<# ... \#>  
```  
  
 Você pode fazer o mesmo com marcas de bloco outro texto modelo diretiva e código.  
  
 Se um bloco de texto incluem cadeias de caracteres usadas para sair de marcas de modelo de texto, você pode usar sequências de escape a seguir:  
  
-   Se uma marca de modelo de texto é precedida por um número par de escape (\\) caracteres o modelo de analisador será inclui metade dos caracteres de escape e inclui a sequência como uma marca de modelo de texto. Por exemplo, se houver quatro caracteres de escape no modelo de texto, haverá dois "\\" caracteres no arquivo gerado.  
  
-   Se a marca de modelo de texto é precedida por um número ímpar de escape (\\) caracteres, o analisador de modelo incluirá metade do "\\" caracteres e a própria marca (\<# ou #>). A marca não é considerada para ser uma marca de modelo de texto.  
  
-   Se um escape (\\) caractere aparece em qualquer lugar em qualquer sequência diferente de onde ela ignora a um caractere de controle ou (em c# somente), o caractere será saído diretamente.  
  
## <a name="see-also"></a>Consulte também  
 [Como gerar modelos com base em modelos usando sequências de escape](../modeling/how-to-generate-templates-from-templates-by-using-escape-sequences.md)