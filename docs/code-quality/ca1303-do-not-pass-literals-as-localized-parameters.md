---
title: "CA1303: Não passar literais como localizados parâmetros | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- Do not pass literals as localized parameters
- DoNotPassLiteralsAsLocalizedParameters
- CA1303
helpviewer_keywords:
- DoNotPassLiteralsAsLocalizedParameters
- CA1303
ms.assetid: 904d284e-76d0-4b8f-a4df-0094de8d7aac
caps.latest.revision: "22"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: ce6ed64a6991342b4dc1506b8384f7691cc90b8f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="ca1303-do-not-pass-literals-as-localized-parameters"></a>CA1303: não passar literais como parâmetros localizados
|||  
|-|-|  
|NomeDoTipo|DoNotPassLiteralsAsLocalizedParameters|  
|CheckId|CA1303|  
|Categoria|Microsoft.Globalization|  
|Alteração Significativa|Não separáveis|  
  
## <a name="cause"></a>Causa  
 Um método passa uma cadeia de caracteres literal como um parâmetro para um construtor ou método de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] biblioteca de classes e que a cadeia de caracteres deve ser localizável.  
  
 Esse aviso é gerado quando uma cadeia de caracteres literal é passada como um valor para um parâmetro ou uma propriedade e uma ou mais das seguintes situações forem verdadeira:  
  
-   O <xref:System.ComponentModel.LocalizableAttribute> atributo do parâmetro ou propriedade é definido como true.  
  
-   O nome de parâmetro ou a propriedade contém "Text", "Mensagem" ou "Legenda".  
  
-   O nome do parâmetro de cadeia de caracteres que é passado para um método Write ou console. WriteLine é "valor" ou "formato".  
  
## <a name="rule-description"></a>Descrição da Regra  
 Literais de cadeia de caracteres que são inseridos no código-fonte são difíceis de localizar.  
  
## <a name="how-to-fix-violations"></a>Como Corrigir Violações  
 Para corrigir uma violação desta regra, substitua a cadeia de caracteres literal com uma cadeia de caracteres recuperada por meio de uma instância do <xref:System.Resources.ResourceManager> classe.  
  
## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos  
 É seguro suprimir um aviso de que essa regra se a biblioteca de código não será localizada, ou se a cadeia de caracteres não é exposta ao usuário final ou um desenvolvedor usando a biblioteca de código.  
  
 Os usuários podem eliminar o ruído em métodos que não devem ser passados cadeias de caracteres localizadas renomeando o parâmetro ou a propriedade chamada ou marcando esses itens como condicional.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra um método que gera uma exceção quando qualquer um dos dois argumentos estiver fora do intervalo. Para o primeiro argumento, o construtor de exceção é passado uma cadeia de caracteres literal, o que viola essa regra. Para o segundo argumento, o construtor é passado corretamente uma cadeia de caracteres recuperada por meio de um <xref:System.Resources.ResourceManager>.  
  
 [!code-cpp[FxCop.Globalization.DoNotPassLiterals#1](../code-quality/codesnippet/CPP/ca1303-do-not-pass-literals-as-localized-parameters_1.cpp)]
 [!code-vb[FxCop.Globalization.DoNotPassLiterals#1](../code-quality/codesnippet/VisualBasic/ca1303-do-not-pass-literals-as-localized-parameters_1.vb)]
 [!code-csharp[FxCop.Globalization.DoNotPassLiterals#1](../code-quality/codesnippet/CSharp/ca1303-do-not-pass-literals-as-localized-parameters_1.cs)]  
  
## <a name="see-also"></a>Consulte também  
 [Recursos em aplicativos de área de trabalho](/dotnet/framework/resources/index)