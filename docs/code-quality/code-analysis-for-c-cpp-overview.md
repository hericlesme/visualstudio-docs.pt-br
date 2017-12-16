---
title: "Análise de código para visão geral do C/C++ | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- annotations, code analysis
- build integration, code analysis
- C/C++ code analysis
- IDE, code analysis
- pragma directive, code analysis
- code analysis, C/C++
- code analysis tool
- command line, code analysis
- C++, code analysis
- check-in policies, code analysis
- '#pragma directives, code analysis'
- C, code analysis
ms.assetid: 81f0c9e8-f471-4de5-aac4-99db336a8809
caps.latest.revision: "25"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: f1634250d97e83b21cccd3ada90933fc0806d35f
ms.sourcegitcommit: f0ddee934713ea9126fa107018a57a94a05eafd3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/12/2017
---
# <a name="code-analysis-for-cc-overview"></a>Análise de código para visão geral do C/C++
A ferramenta de análise de código C/C++ fornece informações para desenvolvedores sobre defeitos possíveis no seu código-fonte C/C++. Erros de codificação comuns relatados pela ferramenta estão estouros de buffer, memória não inicializada, desreferências de ponteiro nulo e perdas de memória e recursos.  
  
## <a name="ide-integrated-development-environment-integration"></a>Integração de IDE (ambiente de desenvolvimento integrado)  
 Para torná-lo natural para os desenvolvedores a usar a ferramenta de análise, ele é totalmente integrado dentro de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE. Durante o processo de compilação, todos os avisos gerados para o código-fonte aparecem na lista de erros. Você pode navegar para o código-fonte que causou o aviso, e você pode exibir informações adicionais sobre a causa e possíveis soluções do problema.  
  
## <a name="pragma-support"></a>#pragma suporte  
 Os desenvolvedores podem usar o `#pragma` diretiva para tratar avisos como erros; ativar ou desativar avisos e suprimir avisos para linhas individuais de código. Para obter mais informações, consulte [como: definir propriedades de análise de código para projetos do C/C++ ](how-to-set-code-analysis-properties-for-c-cpp-projects.md).  
  
## <a name="annotation-support"></a>Suporte de anotação  
 Anotações de melhorar a precisão da análise de código. As anotações fornecem informações adicionais sobre condições de pré e pós-em parâmetros de função e tipos de retorno. Para obter mais informações, consulte [como: especificar informações de código adicionais usando analysis_assume](../code-quality/how-to-specify-additional-code-information-by-using-analysis-assume.md)  
  
## <a name="run-analysis-tool-as-part-of-check-in-policy"></a>Execute a ferramenta de análise como parte da política de check-in  
 Você talvez queira exigem que o código de origem todos os check-ins satisfazer certas políticas. Em particular, você deseja certificar-se de que a análise foi executada como uma etapa de compilação local mais recente. Para obter mais informações sobre como habilitar uma política de check-in do analysis código, consulte [criando e usando análise de código de Check-In políticas](../code-quality/creating-and-using-code-analysis-check-in-policies.md)  
  
## <a name="team-build-integration"></a>Integração do Team Build  
 Você pode usar os recursos integrados de sistema de compilação para executar a ferramenta de análise de código como uma etapa do [!INCLUDE[esprtfs](../code-quality/includes/esprtfs_md.md)] do processo de compilação. Para obter mais informações, consulte [Compilar o aplicativo](http://msdn.microsoft.com/Library/a971b0f9-7c28-479d-a37b-8fd7e27ef692).  
  
## <a name="command-line-support"></a>Suporte de linha de comando  
 Além de integração total no ambiente de desenvolvimento, os desenvolvedores também podem usar a ferramenta de análise da linha de comando, conforme mostrado no exemplo a seguir:  
  
 `C:\>cl /analyze Sample.cpp`