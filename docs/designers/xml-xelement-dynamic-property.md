---
title: "XML (propriedade dinâmica de XElement)| Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-designers
ms.tgt_pltfrm: 
ms.topic: article
apiname: XElement.Xml
ms.assetid: 69ab2a33-4fe7-4cfa-97f8-eaf063decb18
caps.latest.revision: "2"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: b03c03ce5980b1c6042d1670d33d43fea6c7edc4
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
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
 [Propriedades Dinâmicas da Classe XElement](../designers/xelement-class-dynamic-properties.md)   
 [Value](../designers/value-xelement-dynamic-property.md)