---
title: 'CA2107: revisar uso de deny e permit only'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2107
- ReviewDenyAndPermitOnlyUsage
helpviewer_keywords:
- ReviewDenyAndPermitOnlyUsage
- CA2107
ms.assetid: 366f4a56-ae93-4882-81d0-bd0a55ebbc26
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d777379cdf5dc5d6be36989f95aadd80ca757e69
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31915676"
---
# <a name="ca2107-review-deny-and-permit-only-usage"></a>CA2107: revisar uso de deny e permit only
|||
|-|-|
|NomeDoTipo|ReviewDenyAndPermitOnlyUsage|
|CheckId|CA2107|
|Categoria|Microsoft.Security|
|Alteração Significativa|Quebra|

## <a name="cause"></a>Causa
 Um método contém uma verificação de segurança que especifica a ação de segurança PermitOnly ou Deny.

## <a name="rule-description"></a>Descrição da Regra
 O <xref:System.Security.CodeAccessPermission.Deny%2A?displayProperty=fullName> ação de segurança deve ser usada apenas por aqueles que têm um conhecimento avançado de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] segurança. O código que usa essas ações de segurança deve passar por uma revisão de segurança.

 Negar altera o comportamento padrão do exame da pilha que ocorre em resposta a uma exigência de segurança. Ele permite que você especifique as permissões que não devem ser concedidas para a duração do método negar, independentemente das permissões reais de chamadores na pilha de chamadas. Se a movimentação da pilha detecta um método que é protegido pelo Deny, e se a permissão exigida é incluída nas permissões negadas, a movimentação da pilha falhará. PermitOnly também altera o comportamento padrão do exame da pilha. Ele permite que o código especificar somente as permissões que podem ser concedidas, independentemente das permissões dos chamadores. Se a movimentação da pilha detecta um método que é protegido pelo PermitOnly, e se a permissão exigida não está incluído nas permissões que são especificadas pelo PermitOnly, a movimentação da pilha falhará.

 Código que dependa essas ações deve ser avaliado cuidadosamente quanto a vulnerabilidades de segurança devido a sua utilidade limitada e comportamento sutil. Considere o seguinte:

-   [Demandas de link](/dotnet/framework/misc/link-demands) não são afetados por Deny ou PermitOnly.

-   Se o Deny ou PermitOnly ocorre no quadro de pilha mesmo que a demanda que faz com que a movimentação da pilha, as ações de segurança não terão efeito.

-   Valores que são usados para construir permissões baseadas no caminho geralmente podem ser especificados de várias maneiras. Negar acesso a um formulário do caminho não nega acesso a todos os formulários. Por exemplo, se um compartilhamento de arquivos \\\Server\Share é mapeado para uma unidade de rede x:, para negar acesso a um arquivo no compartilhamento, você deve negar \\\Server\Share\File, X:\File e todos os outros caminho que acessa o arquivo.

-   Um <xref:System.Security.CodeAccessPermission.Assert%2A?displayProperty=fullName> pode encerrar um exame da pilha antes de atingir o Deny ou PermitOnly.

-   Se um Deny tiver qualquer efeito, ou seja, quando um chamador tiver uma permissão que está bloqueada por Deny, o chamador pode acessar o recurso protegido diretamente, ignorando a negar. Da mesma forma, se o chamador não tem a permissão negada, a movimentação da pilha falhará sem a negar.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Qualquer uso das seguintes ações de segurança fará com que uma violação. Para corrigir uma violação, não use essas ações de segurança.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 Suprima um aviso dessa regra somente depois de concluir uma revisão de segurança.

## <a name="example"></a>Exemplo
 O exemplo a seguir demonstra algumas limitações Deny.

 A biblioteca a seguir contém uma classe que tem dois métodos que são idênticos, exceto as demandas de segurança que protegem-los.

 [!code-csharp[FxCop.Security.PermitAndDeny#1](../code-quality/codesnippet/CSharp/ca2107-review-deny-and-permit-only-usage_1.cs)]

## <a name="example"></a>Exemplo
 O aplicativo a seguir demonstra os efeitos de negar sobre os métodos protegidos da biblioteca.

 [!code-csharp[FxCop.Security.TestPermitAndDeny#1](../code-quality/codesnippet/CSharp/ca2107-review-deny-and-permit-only-usage_2.cs)]

 Este exemplo gerencia a seguinte saída.

 **Demanda: Deny do chamador não tem efeito sob demanda com a permissão declarada. ** 
 **LinkDemand: Deny do chamador não tem nenhum efeito em LinkDemand com a permissão declarada.** 
 **LinkDemand: Deny do chamador não tem nenhum efeito com o código protegido LinkDemand.** 
 **LinkDemand: Negar este não tem nenhum efeito com o código protegido LinkDemand.**
## <a name="see-also"></a>Consulte também
 <xref:System.Security.CodeAccessPermission.PermitOnly%2A?displayProperty=fullName> <xref:System.Security.CodeAccessPermission.Assert%2A?displayProperty=fullName> <xref:System.Security.CodeAccessPermission.Deny%2A?displayProperty=fullName> <xref:System.Security.IStackWalk.PermitOnly%2A?displayProperty=fullName> [Diretrizes de codificação segura](/dotnet/standard/security/secure-coding-guidelines)

