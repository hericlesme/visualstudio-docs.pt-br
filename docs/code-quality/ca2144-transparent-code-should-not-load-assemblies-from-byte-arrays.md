---
title: 'CA2144: o código transparente não deve carregar assemblies a partir de matrizes de bytes'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2144
ms.assetid: 777b1310-6e16-4413-b4ee-5f3136304f82
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6b0357d6fc0c0cbfdd59c7718d58181e4d58b3a3
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="ca2144-transparent-code-should-not-load-assemblies-from-byte-arrays"></a>CA2144: o código transparente não deve carregar assemblies a partir de matrizes de bytes
|||
|-|-|
|NomeDoTipo|TransparentMethodsShouldNotLoadAssembliesFromByteArrays|
|CheckId|CA2144|
|Categoria|Microsoft.Security|
|Alteração Significativa|Quebra|

## <a name="cause"></a>Causa
 Um método transparente carrega um assembly de uma matriz de bytes usando um dos seguintes métodos:

-   <xref:System.Reflection.Assembly.Load%2A>

-   <xref:System.Reflection.Assembly.Load%2A>

-   <xref:System.Reflection.Assembly.Load%2A>

## <a name="rule-description"></a>Descrição da Regra
 A revisão de segurança para o código transparente não é tão completo quanto a revisão de segurança para o código crítico porque o código transparente não pode realizar ações confidenciais de segurança. Os assemblies carregados a partir de uma matriz de bytes podem não ser observados no código transparente e essa matriz de bytes pode conter código crítico ou código crítico de segurança mais importante, que precisa ser auditado. Portanto, o código transparente não deve carregar assemblies de uma matriz de bytes.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir uma violação desta regra, marque o método que está carregando o assembly com o <xref:System.Security.SecurityCriticalAttribute> ou <xref:System.Security.SecuritySafeCriticalAttribute> atributo.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 Não suprima um aviso nessa regra.

## <a name="example"></a>Exemplo
 A regra é disparada com o código a seguir porque um método transparente carrega um assembly de uma matriz de bytes.

 [!code-csharp[FxCop.Security.CA2144.TransparentMethodsShouldNotLoadAssembliesFromByteArrays#1](../code-quality/codesnippet/CSharp/ca2144-transparent-code-should-not-load-assemblies-from-byte-arrays_1.cs)]