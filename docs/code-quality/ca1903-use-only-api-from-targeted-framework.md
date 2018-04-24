---
title: 'CA1903: usar apenas a API da estrutura de destino'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- UseOnlyAPIFromTargetedFramework
- CA1903
helpviewer_keywords:
- UseOnlyApiFromTargetedFramework
- CA1903
ms.assetid: efdb5cc7-bbd8-4fa7-9fff-02b91e59350e
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a5d8fa2d2580d27e0bdbc45ae0098f432f919eec
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/19/2018
---
# <a name="ca1903-use-only-api-from-targeted-framework"></a>CA1903: usar apenas a API da estrutura de destino
|||
|-|-|
|NomeDoTipo|UseOnlyApiFromTargetedFramework|
|CheckId|CA1903|
|Categoria|Microsoft.Portability|
|Alteração Significativa|Quebra - quando disparado em relação à assinatura de um tipo ou membro visível externamente.<br /><br /> Não separáveis - quando acionado no corpo de um método.|

## <a name="cause"></a>Causa
 Um membro ou tipo está usando um membro ou um tipo que foi introduzido em um service pack não foi incluído com o framework de destino do projeto.

## <a name="rule-description"></a>Descrição da Regra
 Tipos e membros novos foram incluídos no .NET Framework 2.0 Service Pack 1 e 2, o .NET Framework 3.0 Service Pack 1 e 2 e o .NET Framework 3.5 Service Pack 1. Projetos destinados as versões principais do .NET Framework, inadvertidamente, podem levar dependências sobre essas novas APIs. Para evitar essa dependência, esta regra é disparada em usos de quaisquer novos membros e tipos que não foram incluídos por padrão com o framework de destino do projeto.

 **Estrutura de destino e dependências do pacote de serviço**

|||
|-|-|
|Quando é a estrutura de destino|É acionado em usos de membros introduzidos no|
|.NET Framework 2.0|.NET framework 2.0 SP1, .NET Framework 2.0 SP2|
|.NET Framework 3.0|.NET framework 2.0 SP1, .NET Framework 2.0 SP2, .NET Framework 3.0 SP1, .NET Framework 3.0 SP2|
|.NET Framework 3,5|.NET Framework 3,5 SP1|
|.NET Framework 4|N/D|

 Para alterar a estrutura de destino do projeto, consulte [direcionar uma versão específica do .NET Framework](../ide/targeting-a-specific-dotnet-framework-version.md).

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para remover a dependência no service pack, remova todos os usos do novo membro ou tipo. Se esta for uma dependência deliberada, suprimir o aviso ou desativar esta regra.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 Não suprima um aviso dessa regra se esta não for uma dependência deliberada no pacote de serviço especificado. Nessa situação, seu aplicativo pode falhar ao executar em sistemas sem este service pack instalado. Suprimir o aviso ou desative essa regra se esta for uma dependência deliberada.

## <a name="example"></a>Exemplo
 O exemplo a seguir mostra uma classe que usa o tipo DateTimeOffset só está disponível no .NET 2.0 Service Pack 1. Este exemplo requer que o .NET Framework 2.0 foi selecionada na lista suspensa do Framework de destino nas propriedades do projeto.

 [!code-csharp[FxCop.Portability.UseOnlyApiFromTargetedFramework#1](../code-quality/codesnippet/CSharp/ca1903-use-only-api-from-targeted-framework_1.cs)]

## <a name="example"></a>Exemplo
 O exemplo a seguir corrige a violação descrita anteriormente, substituindo os usos do tipo DateTimeOffset com o tipo de DateTime.

 [!code-csharp[FxCop.Portability.UseOnlyApiFromTargetedFramework2#1](../code-quality/codesnippet/CSharp/ca1903-use-only-api-from-targeted-framework_2.cs)]

## <a name="see-also"></a>Consulte também
 [Avisos de portabilidade](../code-quality/portability-warnings.md) [direcionar uma versão específica do .NET Framework](../ide/targeting-a-specific-dotnet-framework-version.md)