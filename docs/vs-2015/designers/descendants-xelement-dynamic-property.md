---
title: Descendants (propriedade dinâmica de XElement)| Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9611d00f-23bf-444b-ab0c-f30701bfc13d
caps.latest.revision: 4
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 29f73bb664e9664ac2a3c56942c86949c9e2bba2
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47461747"
---
# <a name="descendants-xelement-dynamic-property"></a>Descendentes (propriedade dinâmica de XElement)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [descendentes (propriedade dinâmica de XElement)](https://docs.microsoft.com/visualstudio/designers/descendants-xelement-dynamic-property).  
  
Obtém um indexador usado para recuperar todos os elementos descendentes do elemento atual que corresponde ao nome especificado expandido.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
elem.Descendants[{namespaceName}localName]  
```  
  
## <a name="property-valuereturn-value"></a>Valor da propriedade/valor de retorno  
 Um indicador de tipo `IEnumerable<XElement> Item(String expandedName)`. Esse marcador utiliza o nome expandido de elementos especificados descendente e retorna os elementos filho correspondentes em uma coleção de <xref:System.Collections.IEnumerable>`<`<xref:System.Xml.Linq.XElement>`>` .  
  
## <a name="remarks"></a>Comentários  
 Esta propriedade é equivalente ao método de <xref:System.Xml.Linq.XContainer.Descendants%28System.Xml.Linq.XName%29?displayProperty=fullName> da classe de <xref:System.Xml.Linq.XContainer> .  
  
 Os elementos na coleção retornada estão na ordem de documento-fonte XML.  
  
 Esta propriedade usa a execução adiada.  
  
## <a name="see-also"></a>Consulte também  
 [Propriedades Dinâmicas da Classe XElement](../designers/xelement-class-dynamic-properties.md)   
 [Elementos](../designers/elements-xelement-dynamic-property.md)



