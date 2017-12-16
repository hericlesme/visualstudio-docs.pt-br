---
title: "Análise de código para visão geral de código gerenciado | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.projectpropertypages.codeanalysis
helpviewer_keywords:
- code analysis, managed code
- managed code, code analysis
ms.assetid: 12ec0dab-46a4-43d8-984a-440730ef37a9
caps.latest.revision: "35"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 5d42d7c7a78d6bde2560f6e5cf5538a93585870b
ms.sourcegitcommit: f0ddee934713ea9126fa107018a57a94a05eafd3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/12/2017
---
# <a name="code-analysis-for-managed-code-overview"></a>Visão geral da análise de código para código gerenciado
Análise de código para código gerenciado analisa os assemblies gerenciados e relata informações sobre assemblies, como violações de programação e regras de design definidas as diretrizes de Design do Microsoft .NET Framework.  
  
 A ferramenta de análise representa as verificações de desempenho durante uma análise como mensagens de aviso. Mensagens de aviso identificam quaisquer problemas de programação e design relevantes e, quando for possíveis, forneça informações sobre como corrigir o problema.  
  
## <a name="ide-integrated-development-environment-integration"></a>Integração de IDE (ambiente de desenvolvimento integrado)  
 Como desenvolvedor, você pode executar a análise de código em seu projeto automaticamente ou você pode executá-lo manualmente.  
  
 Para executar análise de código toda vez que você compilar um projeto, você deve selecionar **habilitar análise de código no Build (define a constante CODE_ANALYSIS)** na página de propriedades do projeto. Para obter mais informações, consulte [como: habilitar e desabilitar análise de código automática](../code-quality/how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md).  
  
 Para executar análise de código manualmente em um projeto no **analisar** menu, clique em **executar análise de código em***ProjectName*. Para obter mais informações, consulte [como: habilitar e desabilitar análise de código automática](../code-quality/how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md).  
  
## <a name="rule-sets"></a>Conjuntos de regras  
 Regras de análise de código para código gerenciado são agrupadas em *conjuntos de regras*. Você pode usar um dos conjuntos de regra padrão Microsoft, ou você pode criar uma regra personalizada definida para atender uma necessidade específica. Para obter mais informações, consulte [usando conjuntos de regras para agrupar regras de análise de código](../code-quality/using-rule-sets-to-group-code-analysis-rules.md).  
  
## <a name="in-source-suppression"></a>Na supressão da fonte  
 Normalmente, é útil indicar que um aviso é não aplicável. Isso informará o desenvolvedor e outras pessoas que podem analisar o código mais tarde, que um aviso foi investigado e suprimido ou ignorado.  
  
 Supressão da fonte de avisos é implementado por meio de atributos personalizados. Para suprimir um aviso, adicione o atributo `SuppressMessage` para o código-fonte conforme mostrado no exemplo a seguir:  
  
 `[System.Diagnosis.CodeAnalysis.SuppressMessage("Microsoft.Design", "CA1039:ListsAreStrongTyped")]`  
  
 `Public class MyClass`  
  
 `{`  
  
 `// code`  
  
 `}`  
  
 Para obter mais informações, consulte [suprimir avisos usando o atributo SuppressMessage](../code-quality/suppress-warnings-by-using-the-suppressmessage-attribute.md).  
  
## <a name="run-code-analysis-as-part-of-check-in-policy"></a>Executar análise de código como parte da política de check-in  
 Como uma organização, você talvez queira exigem que todos os check-ins satisfazer certas políticas. Em particular, você deseja certificar-se de que você siga essas políticas:  
  
-   Não havia nenhum erro de compilação no código que está sendo feito check-in.  
  
-   Análise de código foi executada como parte da compilação mais recente.  
  
 Você pode fazer isso especificando políticas de check-in. Para obter mais informações, consulte [melhorando a qualidade do código com políticas de Check-in do projeto de equipe](../code-quality/enhancing-code-quality-with-team-project-check-in-policies.md).  
  
## <a name="team-build-integration"></a>Integração do Team Build  
 Você pode usar os recursos integrados de sistema de compilação para executar a ferramenta de análise como parte do processo de compilação. Para obter mais informações, consulte [Build e versão](/vsts/build-release/index).  
  
## <a name="see-also"></a>Consulte também  
 [Usando conjuntos de regras para agrupar regras de análise de código](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)   
 [Como: habilitar e desabilitar análise de código automática](../code-quality/how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md)