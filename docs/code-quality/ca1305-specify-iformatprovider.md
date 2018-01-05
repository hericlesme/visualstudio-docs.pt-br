---
title: 'CA1305: Especificar IFormatProvider | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SpecifyIFormatProvider
- CA1305
helpviewer_keywords:
- CA1305
- SpecifyIFormatProvider
ms.assetid: fb34ed9a-4eab-47cc-8eef-3068a4a1397e
caps.latest.revision: "22"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 8bb3d993cc79ebf683f0a2622628bfc87d7c065a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ca1305-specify-iformatprovider"></a>CA1305: especificar IFormatProvider
|||  
|-|-|  
|NomeDoTipo|SpecifyIFormatProvider|  
|CheckId|CA1305|  
|Categoria|Microsoft.Globalization|  
|Alteração Significativa|Não recentes|  
  
## <a name="cause"></a>Causa  
 Um método ou construtor chama um ou mais membros que têm sobrecargas que aceitam um <xref:System.IFormatProvider?displayProperty=fullName> parâmetro e o método ou construtor não chama a sobrecarga que utiliza o <xref:System.IFormatProvider> parâmetro. Essa regra ignora chamadas para [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] métodos documentados como ignorar o <xref:System.IFormatProvider> parâmetro e além dos seguintes métodos:  
  
-   <xref:System.Activator.CreateInstance%2A?displayProperty=fullName>  
  
-   <xref:System.Resources.ResourceManager.GetObject%2A?displayProperty=fullName>  
  
-   <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=fullName>  
  
## <a name="rule-description"></a>Descrição da Regra  
 Quando um <xref:System.Globalization.CultureInfo?displayProperty=fullName> ou <xref:System.IFormatProvider> objeto não for fornecido, o valor padrão fornecido pelo membro sobrecarregado não pode ter o efeito desejado em todas as localidades. Além disso, [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] membros escolhem a cultura padrão e formatação com base em pressuposições que podem não estar corretas para seu código. Para certificar-se de que o código funciona conforme o esperado para os cenários, você deve fornecer informações específicas de cultura de acordo com as seguintes diretrizes:  
  
-   Se o valor será exibido para o usuário, use a cultura atual. Consulte <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName>.  
  
-   Se o valor será armazenado e acessado pelo software (mantido em um arquivo ou banco de dados), use a cultura invariável. Consulte <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=fullName>.  
  
-   Se você não souber o destino do valor, ter o consumidor de dados ou provedor de especificar a cultura.  
  
 Observe que <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> é usado somente para recuperar recursos localizados por meio de uma instância do <xref:System.Resources.ResourceManager?displayProperty=fullName> classe.  
  
 Mesmo que o comportamento padrão do membro sobrecarregado é adequado às suas necessidades, é melhor chamar a sobrecarga específica da cultura explicitamente para que seu código autodocumentados e mais fácil manutenção.  
  
## <a name="how-to-fix-violations"></a>Como Corrigir Violações  
 Para corrigir uma violação desta regra, use a sobrecarga que utiliza um <xref:System.Globalization.CultureInfo> ou <xref:System.IFormatProvider> e especifique o argumento de acordo com as diretrizes que foram listados anteriormente.  
  
## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos  
 É seguro suprimir um aviso dessa regra quando você tiver certeza de que o provedor de cultura/formato padrão é a opção correta e em que a facilidade de manutenção de código não é uma prioridade de desenvolvimento importantes.  
  
## <a name="example"></a>Exemplo  
 No exemplo a seguir, `BadMethod` faz com que dois violações desta regra. `GoodMethod`corrige a violação primeiro, passando a cultura invariável para <xref:System.String.Compare%2A>e corrige a violação de segundo, passando a cultura atual como <xref:System.String.ToLower%2A> porque `string3` é exibido ao usuário.  
  
 [!code-csharp[FxCop.Globalization.CultureInfo#1](../code-quality/codesnippet/CSharp/ca1305-specify-iformatprovider_1.cs)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra o efeito da cultura atual o padrão <xref:System.IFormatProvider> que é selecionada pelo <xref:System.DateTime> tipo.  
  
 [!code-csharp[FxCop.Globalization.IFormatProvider#1](../code-quality/codesnippet/CSharp/ca1305-specify-iformatprovider_2.cs)]  
  
 Este exemplo gerencia a seguinte saída.  
  
 **6/4/1900 12:15:12 PM**  
**06/04/1900 12:15:12**   
## <a name="related-rules"></a>Regras relacionadas  
 [CA1304: especificar CultureInfo](../code-quality/ca1304-specify-cultureinfo.md)  
  
## <a name="see-also"></a>Consulte também  
[Usando a classe CultureInfo](/dotnet/standard/globalization-localization/globalization#Cultures)  