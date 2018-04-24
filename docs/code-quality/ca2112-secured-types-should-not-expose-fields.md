---
title: 'CA2112: os tipos seguros não devem expor campos'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2112
- SecuredTypesShouldNotExposeFields
helpviewer_keywords:
- SecuredTypesShouldNotExposeFields
- CA2112
ms.assetid: 9eb13a78-3487-49f2-81d1-3c3866db132f
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e3fd94add5a2fbb1d77025f44f35bc9456ab1e55
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/19/2018
---
# <a name="ca2112-secured-types-should-not-expose-fields"></a>CA2112: os tipos seguros não devem expor campos
|||
|-|-|
|NomeDoTipo|SecuredTypesShouldNotExposeFields|
|CheckId|CA2112|
|Categoria|Microsoft.Security|
|Alteração Significativa|Quebra|

## <a name="cause"></a>Causa
 Um tipo público ou protegido contém campos públicos e é protegido por um [demandas de Link](/dotnet/framework/misc/link-demands).

## <a name="rule-description"></a>Descrição da Regra
 Se tiver acesso a uma instância de um tipo protegido por uma exigência de vínculo, o código não precisará atender à exigência de vínculo para acessar os campos do tipo.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir uma violação desta regra, verifique os campos confidenciais e adicione as propriedades públicas nem os métodos que retornam os dados do campo. Verificações de segurança LinkDemand em tipos de protegem o acesso às propriedades e os métodos do tipo. No entanto, segurança de acesso de código não se aplica aos campos.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 Para problemas de segurança e para um bom design, você deve corrigir violações, tornando o confidenciais campos públicos. Você pode suprimir um aviso de que essa regra se o campo não contém informações que devem permanecer protegidas e você não confiar no conteúdo do campo.

## <a name="example"></a>Exemplo
 O exemplo a seguir é composto de um tipo de biblioteca (`SecuredTypeWithFields`) com campos não seguras, um tipo (`Distributor`) que você pode criar instâncias do tipo biblioteca e instâncias de passagens incorreta para tipos não tem permissão para criá-los e código de aplicativo pode ler os campos de uma instância mesmo que ele não tem a permissão que protege o tipo.

 O seguinte código de biblioteca viola a regra.

 [!code-csharp[FxCop.Security.LinkDemandOnField#1](../code-quality/codesnippet/CSharp/ca2112-secured-types-should-not-expose-fields_1.cs)]

## <a name="example"></a>Exemplo
 O aplicativo não é possível criar uma instância devido a demanda de link que protege o tipo seguro. A seguinte classe permite que o aplicativo para obter uma instância do tipo seguro.

 [!code-csharp[FxCop.Security.LDOnFieldsDistributor#1](../code-quality/codesnippet/CSharp/ca2112-secured-types-should-not-expose-fields_2.cs)]

## <a name="example"></a>Exemplo
 O aplicativo a seguir ilustra como fazer isso, sem permissão para acessar os métodos do tipo um protegido, o código pode acessar seus campos.

 [!code-csharp[FxCop.Security.TestLinkDemandOnFields#1](../code-quality/codesnippet/CSharp/ca2112-secured-types-should-not-expose-fields_3.cs)]

 Este exemplo gerencia a seguinte saída.

 **Criando uma instância de SecuredTypeWithFields. ** 
 **Campos de tipo segura: 22, 33**
**alterar o campo do tipo seguro... ** 
 **Campos de objeto armazenado em cache: 99, 33**
## <a name="related-rules"></a>Regras relacionadas
 [CA1051: não declarar campos de instância visíveis](../code-quality/ca1051-do-not-declare-visible-instance-fields.md)

## <a name="see-also"></a>Consulte também
 [Demandas de link](/dotnet/framework/misc/link-demands) [dados e modelagem](/dotnet/framework/data/index)