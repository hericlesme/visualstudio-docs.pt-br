---
title: 'CA1903: Usar somente API da estrutura de destino | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- UseOnlyAPIFromTargetedFramework
- CA1903
helpviewer_keywords:
- UseOnlyApiFromTargetedFramework
- CA1903
ms.assetid: efdb5cc7-bbd8-4fa7-9fff-02b91e59350e
caps.latest.revision: "8"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 7caff553adfd812e671a2d8643b2352d9868ca43
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
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
 [Avisos de portabilidade](../code-quality/portability-warnings.md)   
 [Direcionamento de uma versão específica do .NET Framework](../ide/targeting-a-specific-dotnet-framework-version.md)