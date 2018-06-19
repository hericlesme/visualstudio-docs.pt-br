---
title: Elemento (propriedade dinâmica de XElement)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-designers
ms.topic: reference
apiname:
- XElement.Element
apitype: Assembly
ms.assetid: c6c25b8d-a1da-41ff-aeff-867ff1dcf749
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 82bc4566fbfa4a5801feb710f07d4391a11bde67
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31923518"
---
# <a name="element-xelement-dynamic-property"></a>Elemento (propriedade dinâmica de XElement)

Obtém um indexador usado para recuperar a instância do elemento filho que corresponde ao nome especificado expandido.

## <a name="syntax"></a>Sintaxe

```
elem.Element[{namespaceName}localName]
```

## <a name="property-valuereturn-value"></a>Valor da propriedade/valor de retorno

Um indicador de tipo `XElement Item(String expandedName)`. Esse marcador aceita um parâmetro expandido de nome e retorna <xref:System.Xml.Linq.XElement>correspondente, ou `null` se não houver nenhum elemento com o nome especificado.

## <a name="remarks"></a>Comentários

Esta propriedade é equivalente ao método de <xref:System.Xml.Linq.XContainer.Element%2A> da classe de <xref:System.Xml.Linq.XContainer?displayProperty=fullName> .

## <a name="see-also"></a>Consulte também

- <xref:System.Xml.Linq.XContainer.Element%2A?displayProperty=fullName>
- [Propriedades dinâmicas da classe XElement](../designers/xelement-class-dynamic-properties.md)
- [Elementos](../designers/elements-xelement-dynamic-property.md)