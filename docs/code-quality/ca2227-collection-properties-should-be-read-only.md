---
title: 'CA2227: as propriedades de coleção devem ser somente leitura'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2227
- CollectionPropertiesShouldBeReadOnly
helpviewer_keywords:
- CA2227
- CollectionPropertiesShouldBeReadOnly
ms.assetid: 26967aaf-6fbe-438a-b4d3-ac579b5dc0f9
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5a3fd69bccdfdc1c08bbc62f6534b40b746d6d49
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="ca2227-collection-properties-should-be-read-only"></a>CA2227: as propriedades de coleção devem ser somente leitura
|||
|-|-|
|NomeDoTipo|CollectionPropertiesShouldBeReadOnly|
|CheckId|CA2227|
|Categoria|Microsoft.Usage|
|Alteração Significativa|Quebra|

## <a name="cause"></a>Causa
 Uma propriedade gravável visível externamente é um tipo que implementa <xref:System.Collections.ICollection?displayProperty=fullName>. Matrizes, indexadores (propriedades com o nome 'Item') e conjuntos de permissões são ignorados pela regra.

## <a name="rule-description"></a>Descrição da Regra
 Uma propriedade de coleção gravável permite que um usuário substituir a coleção com uma coleção completamente diferente. Uma propriedade somente leitura evita que a coleção seja substituída, mas ainda permite que membros individuais sejam definidos. Se substituir a coleção é uma meta, o padrão de design preferencial é incluir um método para remover todos os elementos da coleção e um método para preencher a coleção. Consulte o <xref:System.Collections.ArrayList.Clear%2A> e <xref:System.Collections.ArrayList.AddRange%2A> métodos de <xref:System.Collections.ArrayList?displayProperty=fullName> classe para obter um exemplo desse padrão.

 Binário e serialização XML dão suporte a propriedades somente leitura que são coleções. O <xref:System.Xml.Serialization.XmlSerializer?displayProperty=fullName> classe tem requisitos específicos para os tipos que implementam <xref:System.Collections.ICollection> e <xref:System.Collections.IEnumerable?displayProperty=fullName> para ser serializável.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir uma violação desta regra, verifique a propriedade somente leitura e se exigir o design, adicione métodos para limpar e preencher a coleção.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 Não suprima um aviso nessa regra.

## <a name="example"></a>Exemplo
 O exemplo a seguir mostra um tipo com uma propriedade de coleção gravável e mostra como a coleção pode ser substituída diretamente. Além disso, a maneira preferida de substituição de uma propriedade de coleção somente leitura usando `Clear` e `AddRange` métodos é mostrado.

 [!code-csharp[FxCop.Usage.PropertiesReturningCollections#1](../code-quality/codesnippet/CSharp/ca2227-collection-properties-should-be-read-only_1.cs)]
 [!code-vb[FxCop.Usage.PropertiesReturningCollections#1](../code-quality/codesnippet/VisualBasic/ca2227-collection-properties-should-be-read-only_1.vb)]
 [!code-cpp[FxCop.Usage.PropertiesReturningCollections#1](../code-quality/codesnippet/CPP/ca2227-collection-properties-should-be-read-only_1.cpp)]

## <a name="related-rules"></a>Regras relacionadas
 [CA1819: as propriedades não devem retornar matrizes](../code-quality/ca1819-properties-should-not-return-arrays.md)