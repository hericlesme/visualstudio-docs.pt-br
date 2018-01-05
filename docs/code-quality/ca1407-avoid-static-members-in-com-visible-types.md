---
title: "CA1407: Evitar membros estáticos em tipos visíveis COM | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1407
- AvoidStaticMembersInComVisibleTypes
helpviewer_keywords:
- CA1407
- AvoidStaticMembersInComVisibleTypes
ms.assetid: bebd0776-ad04-453c-bca8-8c124c2d7840
caps.latest.revision: "23"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 9cb2b7a95772ddd95bf4379ea0749cf42419a182
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ca1407-avoid-static-members-in-com-visible-types"></a>CA1407: evitar membros estáticos em tipos visíveis COM
|||  
|-|-|  
|NomeDoTipo|AvoidStaticMembersInComVisibleTypes|  
|CheckId|CA1407|  
|Categoria|Microsoft.Interoperability|  
|Alteração Significativa|Não recentes|  
  
## <a name="cause"></a>Causa  
 Um tipo que está especificamente marcado como visível para COM Component Object Model () contém um `public``static` método.  
  
## <a name="rule-description"></a>Descrição da Regra  
 COM não oferece suporte `static` métodos.  
  
 Essa regra ignora a propriedade e acessadores de eventos, métodos ou métodos que são marcados como usando a sobrecarga de operador de <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName> atributo ou o <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName> atributo.  
  
 Por padrão, os seguintes são visíveis no COM: assemblies, tipos públicos, membros de instância pública em tipos públicos e todos os membros de tipos de valor público.  
  
 Para esta regra ocorrer, um nível de conjunto <xref:System.Runtime.InteropServices.ComVisibleAttribute> deve ser definido como `false` e classe - <xref:System.Runtime.InteropServices.ComVisibleAttribute> deve ser definido como `true`, como mostra o código a seguir.  
  
```csharp  
using System;  
using System.Runtime.InteropServices;   
  
[assembly: ComVisible(false)]   
namespace Samples  
{      
    [ComVisible(true)]  
    public class MyClass  
    {  
        public static void DoSomething()  
        {  
        }  
    }  
}  
```  
  
## <a name="how-to-fix-violations"></a>Como Corrigir Violações  
 Para corrigir uma violação desta regra, altere o design para usar um método de instância que fornece a mesma funcionalidade que o `static` método.  
  
## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos  
 É seguro suprimir um aviso dessa regra, se um cliente COM não exigir acesso à funcionalidade fornecida pelo `static` método.  
  
## <a name="example-violation"></a>Violação de exemplo  
  
### <a name="description"></a>Descrição  
 A exemplo a seguir mostra um `static` método que violam essa regra.  
  
### <a name="code"></a>Código  
 [!code-csharp[FxCop.Interoperability.ComVisibleStaticMembersViolation#1](../code-quality/codesnippet/CSharp/ca1407-avoid-static-members-in-com-visible-types_1.cs)]  
  
### <a name="comments"></a>Comentários  
 Neste exemplo, o **Book.FromPages** método não pode ser chamado de COM.  
  
## <a name="example-fix"></a>Correção de exemplo  
  
### <a name="description"></a>Descrição  
 Para corrigir a violação no exemplo anterior, você pode alterar o método para um método de instância, mas que não faz sentido nesta instância. É a melhor solução aplicar explicitamente `ComVisible(false)` para o método para torná-lo, desmarque para outros desenvolvedores que o método não pode ser visto no COM.  
  
 O exemplo a seguir aplica-se <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute> para o método.  
  
### <a name="code"></a>Código  
 [!code-csharp[FxCop.Interoperability.ComVisibleStaticMembersFixed#1](../code-quality/codesnippet/CSharp/ca1407-avoid-static-members-in-com-visible-types_2.cs)]  
  
## <a name="related-rules"></a>Regras relacionadas  
 [CA1017: marcar assemblies com ComVisibleAttribute](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)  
  
 [CA1406: evitar argumentos Int64 para clientes do Visual Basic 6](../code-quality/ca1406-avoid-int64-arguments-for-visual-basic-6-clients.md)  
  
 [CA1413: evitar campos não públicos em tipos de valor visíveis em COM](../code-quality/ca1413-avoid-non-public-fields-in-com-visible-value-types.md)  
  
## <a name="see-also"></a>Consulte também  
 [Interoperação com código não gerenciado](/dotnet/framework/interop/index)