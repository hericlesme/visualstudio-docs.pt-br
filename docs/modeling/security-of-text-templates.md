---
title: Segurança de modelos de texto
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, security
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 97827a9219edbed08554aaedf1ebb8c0397606d5
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/20/2018
---
# <a name="security-of-text-templates"></a>Segurança de modelos de texto
Modelos de texto têm as seguintes questões de segurança:

-   Modelos de texto são vulneráveis a inserções de um código arbitrário.

-   Se o mecanismo que o host usa para encontrar um processador de diretiva não estiver protegido, um processador de diretiva mal-intencionado poderia ser executado.

## <a name="arbitrary-code"></a>Código arbitrário
 Quando você escreve um modelo, você pode colocar qualquer código dentro do \<# # > marcas. Isso permite que um código arbitrário ser executado a partir de um modelo de texto.

 Certifique-se de que obter modelos de fontes confiáveis. Certifique-se de avisar os usuários finais do seu aplicativo para não executar modelos que não vêm de fontes confiáveis.

## <a name="malicious-directive-processor"></a>Processador de diretiva mal-intencionado
 O mecanismo do modelo de texto interage com um host de transformação e um ou mais processadores de diretiva para transformar o texto do modelo para um arquivo de saída. Para obter mais informações, consulte [o processo de transformação de modelo de texto](../modeling/the-text-template-transformation-process.md).

 Se o mecanismo que o host usa para encontrar um processador de diretiva não estiver protegido, ele é executado o risco de execução de um processador de diretiva mal-intencionado. O processador de diretiva mal-intencionado pode fornecer código que é executado em `FullTrust` modo quando o modelo é executado. Se você criar um host de transformação de modelo de texto personalizado, você deve usar um mecanismo seguro, como o registro, para o mecanismo localizar os processadores de diretivas.