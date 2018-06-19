---
title: Descendentes (propriedade dinâmica de XElement)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-designers
ms.topic: reference
ms.assetid: 9611d00f-23bf-444b-ab0c-f30701bfc13d
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7c1b0aa0c55c0da2a6f9af58f5d54ff607a409ce
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31925395"
---
# <a name="descendants-xelement-dynamic-property"></a>Descendentes (propriedade dinâmica de XElement)

Obtém um indexador usado para recuperar todos os elementos descendentes do elemento atual que corresponde ao nome especificado expandido.

## <a name="syntax"></a>Sintaxe

```
elem.Descendants[{namespaceName}localName]
```

## <a name="property-valuereturn-value"></a>Valor da propriedade/valor de retorno

Um indicador de tipo `IEnumerable<XElement> Item(String expandedName)`. Esse marcador utiliza o nome expandido de elementos especificados descendente e retorna os elementos filho correspondentes em uma coleção de <xref:System.Collections.IEnumerable>`<`<xref:System.Xml.Linq.XElement>`>` .

## <a name="remarks"></a>Comentários

Esta propriedade é equivalente ao método de <xref:System.Xml.Linq.XContainer.Descendants(System.Xml.Linq.XName)?displayProperty=fullName> da classe de <xref:System.Xml.Linq.XContainer> .

Os elementos na coleção retornada estão na ordem de documento-fonte XML.

Esta propriedade usa a execução adiada.

## <a name="see-also"></a>Consulte também

- [Propriedades dinâmicas da classe XElement](../designers/xelement-class-dynamic-properties.md)
- [Elementos](../designers/elements-xelement-dynamic-property.md)