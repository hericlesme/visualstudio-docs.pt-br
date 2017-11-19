---
title: "Suporte ao serviço de linguagem para depuração | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugger, language support
- language services, debugging support
ms.assetid: 7a44067f-a410-4a6a-84d2-bda5184140bc
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: cb57f7efa13a31ee4c68340936955624189e285d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="language-service-support-for-debugging"></a>Suporte ao serviço de linguagem para depuração
Um serviço de idioma pode fornecer recursos que oferecem suporte a um depurador a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageDebugInfo> interface. Esses recursos incluem validar os pontos de interrupção e fornecer uma lista de expressões para o **Autos** janela.  
  
 No entanto, você precisa ter um avaliador de expressão para depurar seu idioma. O avaliador de expressão é responsável por avaliar expressões para gerar valores de durante a depuração. Para obter informações sobre como implementar avaliadores de expressão do CLR, consulte:  
  
-   [Avaliadores de expressão de CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)  
  
-   [Amostra do avaliador de expressão gerenciado](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)  
  
## <a name="compiler-output"></a>Saída do compilador  
 O tipo de compilador determina o que você precisa fazer para implementar a depuração para o seu idioma. Se o compilador tem como alvo o sistema operacional Windows e grava um arquivo. PDB, você pode depurar programas com o código nativo que é integrado ao Visual Studio do mecanismo de depuração. Se o compilador gera Microsoft intermediate language (MSIL), você pode depurar programas com o código gerenciado depuração engine, que também é integrado no Visual Studio. Se o compilador tem como alvo um sistema operacional proprietário ou em um ambiente de tempo de execução diferente, você precisa gravar seu próprio mecanismo de depuração.  
  
 Para obter mais informações sobre a implementação de depuração para o seu idioma, consulte [Introdução](../../extensibility/debugger/getting-started-with-debugger-extensibility.md) no SDK do Visual Studio de depuração.