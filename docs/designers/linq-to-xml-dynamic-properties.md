---
title: Propriedades dinâmicas LINQ to XML
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: 0455f47c-4a68-4f2e-a3f8-dd1d85b99012
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: eab219b0babbb423c10a08f1f9c4888ad70aff12
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="linq-to-xml-dynamic-properties"></a>Propriedades dinâmicas LINQ to XML

Esta seção fornece informações de referência sobre as propriedades dinâmicas em LINQ to XML. Especificamente, essas propriedades são expostos por classes de <xref:System.Xml.Linq.XAttribute> e de <xref:System.Xml.Linq.XElement> , que estão no espaço de <xref:System.Xml.Linq> .

Conforme explicado no tópico [Visão geral de vinculação de dados de WPF com LINQ to XML](../designers/wpf-data-binding-with-linq-to-xml-overview.md), cada uma das propriedades dinâmicas é equivalente a uma propriedade pública ou método padrão na mesma classe. Esses membros padrão devem ser usados para a maioria das finalidades; as propriedades dinâmicas são fornecidas especificamente para cenários de associação de dados LINQ to XML. Para obter mais informações sobre membros padrão dessas classes, consulte os tópicos de referência de <xref:System.Xml.Linq.XAttribute> e de <xref:System.Xml.Linq.XElement> .

Em relação a seus valores resolvidos, as propriedades dinâmicas nesta seção se enquadram em duas categorias:

- O simples, como as propriedades de `Value` classes de <xref:System.Xml.Linq.XAttribute> e de <xref:System.Xml.Linq.XElement> , que são consideradas como um único valor.

- Valores indexados, como as propriedades [Elementos](../designers/elements-xelement-dynamic-property.md) e [Descendentes](../designers/descendants-xelement-dynamic-property.md) de <xref:System.Xml.Linq.XElement>, que são resolvidas em um tipo de indexador. Para que os tipos do indexador são resolvidos com o valor desejado ou à coleção, um parâmetro expandido do nome deve ser-lhes passado.

Todas as propriedades dinâmicas que retornam um valor indexado do tipo <xref:System.Collections.Generic.IEnumerable%601> usam a execução adiada. Para obter mais informações sobre a execução adiada, consulte [Introdução a Consultas de LINQ (C#)](/dotnet/csharp/programming-guide/concepts/linq/introduction-to-linq-queries).

## <a name="reference"></a>Referência

- <xref:System.Xml.Linq>
- <xref:System.Xml.Linq.XElement?displayProperty=fullName>
- <xref:System.Xml.Linq.XAttribute?displayProperty=fullName>

## <a name="see-also"></a>Consulte também

- [Vinculação de dados de WPF com LINQ to XML](../designers/wpf-data-binding-with-linq-to-xml-overview.md)
- [Visão geral da vinculação de dados do WPF com LINQ to XML](../designers/wpf-data-binding-with-linq-to-xml-overview.md)
- [Introdução a consultas LINQ (C#)](/dotnet/csharp/programming-guide/concepts/linq/introduction-to-linq-queries)
