---
title: "Segurança dos modelos de texto | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: text templates, security
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 327d56447d434f1122a16b9c3edf6a4d3b66c97f
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/13/2018
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