---
title: "Elemento (Propriedade Dinâmica XElement) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-designers
ms.tgt_pltfrm: 
ms.topic: article
apiname: XElement.Element
apitype: Assembly
ms.assetid: c6c25b8d-a1da-41ff-aeff-867ff1dcf749
caps.latest.revision: "2"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: ec02b03188ea0fd1fa7c15ea03878bdec12890f6
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
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
 <xref:System.Xml.Linq.XContainer.Element%2A?displayProperty=fullName>   
 [Propriedades Dinâmicas da Classe XElement](../designers/xelement-class-dynamic-properties.md)   
 [Elementos](../designers/elements-xelement-dynamic-property.md)