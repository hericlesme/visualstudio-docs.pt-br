---
title: 'CA1304: Especificar CultureInfo | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SpecifyCultureInfo
- CA1304
helpviewer_keywords:
- SpecifyCultureInfo
- CA1304
ms.assetid: b912d76a-54fd-4c93-b25d-16491e0ae319
caps.latest.revision: "20"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 932ac7e8f731974896991cea5ae504e452e9a036
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ca1304-specify-cultureinfo"></a>CA1304: especificar CultureInfo
|||  
|-|-|  
|NomeDoTipo|SpecifyCultureInfo|  
|CheckId|CA1304|  
|Categoria|Microsoft.Globalization|  
|Alteração Significativa|Não recentes|  
  
## <a name="cause"></a>Causa  
 Um método ou construtor chama um membro que tem uma sobrecarga que aceita um <xref:System.Globalization.CultureInfo?displayProperty=fullName> parâmetro e o método ou construtor não chama a sobrecarga que utiliza o <xref:System.Globalization.CultureInfo> parâmetro. Essa regra ignora as chamadas para os métodos a seguir:  
  
-   <xref:System.Activator.CreateInstance%2A?displayProperty=fullName>  
  
-   <xref:System.Resources.ResourceManager.GetObject%2A?displayProperty=fullName>  
  
-   <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=fullName>  
  
## <a name="rule-description"></a>Descrição da Regra  
 Quando um <xref:System.Globalization.CultureInfo> ou <xref:System.IFormatProvider?displayProperty=fullName> objeto não for fornecido, o valor padrão fornecido pelo membro sobrecarregado não pode ter o efeito desejado em todas as localidades. Além disso, [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] membros escolhem a cultura padrão e formatação com base em pressuposições que podem não estar corretas para seu código. Para garantir que o código funciona conforme o esperado para os cenários, você deve fornecer informações específicas de cultura de acordo com as seguintes diretrizes:  
  
-   Se o valor será exibido para o usuário, use a cultura atual. Consulte <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName>.  
  
-   Se o valor será armazenado e acessado pelo software, ou seja, persistente em um arquivo ou banco de dados, use a cultura invariável. Consulte <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=fullName>.  
  
-   Se você não souber o destino do valor, ter o consumidor de dados ou provedor de especificar a cultura.  
  
 Observe que <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> é usado somente para recuperar recursos localizados por meio de uma instância do <xref:System.Resources.ResourceManager?displayProperty=fullName> classe.  
  
 Mesmo que o comportamento padrão do membro sobrecarregado é adequado às suas necessidades, é melhor chamar a sobrecarga específica da cultura explicitamente para que seu código autodocumentados e mais fácil manutenção.  
  
## <a name="how-to-fix-violations"></a>Como Corrigir Violações  
 Para corrigir uma violação desta regra, use a sobrecarga que utiliza um <xref:System.Globalization.CultureInfo> ou <xref:System.IFormatProvider> e especifique o argumento de acordo com as diretrizes que foram listados anteriormente.  
  
## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos  
 É seguro suprimir um aviso dessa regra quando você tiver certeza de que o provedor de cultura/formato padrão é a escolha correta e facilidade de manutenção de código não é uma prioridade de desenvolvimento importantes.  
  
## <a name="example"></a>Exemplo  
 No exemplo a seguir, `BadMethod` faz com que dois violações desta regra. `GoodMethod`corrige a violação primeiro, passando a cultura invariável para System.String.Compare e corrige a violação de segundo, passando a cultura atual como <xref:System.String.ToLower%2A> porque `string3` é exibido ao usuário.  
  
 [!code-csharp[FxCop.Globalization.CultureInfo#1](../code-quality/codesnippet/CSharp/ca1304-specify-cultureinfo_1.cs)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra o efeito da cultura atual o padrão <xref:System.IFormatProvider> que é selecionada pelo <xref:System.DateTime> tipo.  
  
 [!code-csharp[FxCop.Globalization.IFormatProvider#1](../code-quality/codesnippet/CSharp/ca1304-specify-cultureinfo_2.cs)]  
  
 Este exemplo gerencia a seguinte saída.  
  
 **6/4/1900 12:15:12 PM**  
**06/04/1900 12:15:12**   
## <a name="related-rules"></a>Regras relacionadas  
 [CA1305: especificar IFormatProvider](../code-quality/ca1305-specify-iformatprovider.md)  
  
## <a name="see-also"></a>Consulte também  
[Usando a classe CultureInfo](/dotnet/standard/globalization-localization/globalization#Cultures)  