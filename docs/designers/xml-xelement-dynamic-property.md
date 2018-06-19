---
title: XML (propriedade dinâmica de XElement)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-designers
ms.topic: reference
apiname:
- XElement.Xml
ms.assetid: 69ab2a33-4fe7-4cfa-97f8-eaf063decb18
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4b895865485ca3ac110670cd9d123d9a8c18ee8e
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31925606"
---
# <a name="xml-xelement-dynamic-property"></a>XML (propriedade dinâmica de XElement)

Obtém o conteúdo sem formatação XML do elemento.

## <a name="syntax"></a>Sintaxe

```
elem.Xml
```

## <a name="property-valuereturn-value"></a>Valor da propriedade/valor de retorno

<xref:System.String> que representa o conteúdo sem formatação XML do elemento.

## <a name="remarks"></a>Comentários

Esta propriedade é equivalente ao método de <xref:System.Xml.Linq.XNode.ToString(System.Xml.Linq.SaveOptions)> da classe de <xref:System.Xml.Linq.XNode?displayProperty=fullName> , com o parâmetro de `SaveOptions` definido como <xref:System.Xml.Linq.SaveOptions>.

## <a name="see-also"></a>Consulte também

- [Propriedades dinâmicas da classe XElement](../designers/xelement-class-dynamic-properties.md)
- [Value](../designers/value-xelement-dynamic-property.md)