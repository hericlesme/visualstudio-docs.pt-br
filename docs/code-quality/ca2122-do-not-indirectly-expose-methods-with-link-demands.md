---
title: 'CA2122: não expor indiretamente métodos com demandas de link'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2122
- DoNotIndirectlyExposeMethodsWithLinkDemands
helpviewer_keywords:
- DoNotIndirectlyExposeMethodsWithLinkDemands
- CA2122
ms.assetid: 3eda58e7-c6ec-41c3-8112-ae0841109c6a
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c43cfc1a448d9073a8bbe493d75c7c117f57d737
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31915550"
---
# <a name="ca2122-do-not-indirectly-expose-methods-with-link-demands"></a>CA2122: não expor indiretamente métodos com demandas de link
|||
|-|-|
|NomeDoTipo|DoNotIndirectlyExposeMethodsWithLinkDemands|
|CheckId|CA2122|
|Categoria|Microsoft.Security|
|Alteração Significativa|Não separáveis|

## <a name="cause"></a>Causa
 Um membro público ou protegido tem um [demandas de Link](/dotnet/framework/misc/link-demands) e é chamado por um membro que não executa nenhuma verificação de segurança.

## <a name="rule-description"></a>Descrição da Regra
 Uma exigência de vínculo verifica as permissões apenas do chamador imediato. Se um membro `X` exige nenhuma segurança de seus chamadores e chama o código protegido por uma demanda de link, um chamador sem a permissão necessária pode usar `X` para acessar o membro protegido.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Adicionar uma segurança [dados e modelagem](/dotnet/framework/data/index) ou link demanda para que ele não fornece acesso inseguro para o membro protegido por demanda de link do membro.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 Para suprimir com segurança um aviso dessa regra, você deve garantir que seu código não concede a seus chamadores acesso a operações ou recursos que podem ser usados de forma destrutivas.

## <a name="example"></a>Exemplo
 Os exemplos a seguir mostram uma biblioteca que viola a regra e um aplicativo que demonstra o problema da biblioteca. A biblioteca de exemplo fornece dois métodos que juntos violam a regra. O `EnvironmentSetting` método protegido por uma demanda de link para acesso irrestrito a variáveis de ambiente. O `DomainInformation` método não faz nenhum demandas de segurança dos chamadores antes de chamar `EnvironmentSetting`.

 [!code-csharp[FxCop.Security.UnsecuredDoNotCall#1](../code-quality/codesnippet/CSharp/ca2122-do-not-indirectly-expose-methods-with-link-demands_1.cs)]

## <a name="example"></a>Exemplo
 O aplicativo a seguir chama o membro de biblioteca não segura.

 [!code-csharp[FxCop.Security.TestUnsecuredDoNot1#1](../code-quality/codesnippet/CSharp/ca2122-do-not-indirectly-expose-methods-with-link-demands_2.cs)]

 Este exemplo gerencia a seguinte saída.

 **O valor do membro não seguro: seattle.corp.contoso.com**
## <a name="see-also"></a>Consulte também
 [Diretrizes de codificação segura](/dotnet/standard/security/secure-coding-guidelines) [demandas de Link](/dotnet/framework/misc/link-demands) [dados e modelagem](/dotnet/framework/data/index)