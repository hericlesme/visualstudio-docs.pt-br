---
title: XML (propriedade dinâmica de XElement)| Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
api_name:
- XElement.Xml
ms.assetid: 69ab2a33-4fe7-4cfa-97f8-eaf063decb18
caps.latest.revision: 4
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 74fdfa59e791fb8e0262df04b1e45f3b867fbd02
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47464711"
---
# <a name="xml-xelement-dynamic-property"></a>XML (propriedade dinâmica de XElement)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [Xml (propriedade dinâmica de XElement)](https://docs.microsoft.com/visualstudio/designers/xml-xelement-dynamic-property).  
  
Obtém o conteúdo sem formatação XML do elemento.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
elem.Xml  
```  
  
## <a name="property-valuereturn-value"></a>Valor da propriedade/valor de retorno  
 <xref:System.String> que representa o conteúdo sem formatação XML do elemento.  
  
## <a name="remarks"></a>Comentários  
 Esta propriedade é equivalente ao método de <xref:System.Xml.Linq.XNode.ToString%28System.Xml.Linq.SaveOptions%29> da classe de <xref:System.Xml.Linq.XNode?displayProperty=fullName> , com o parâmetro de `SaveOptions` definido como <xref:System.Xml.Linq.SaveOptions>.  
  
## <a name="see-also"></a>Consulte também  
 [Propriedades Dinâmicas da Classe XElement](../designers/xelement-class-dynamic-properties.md)   
 [Value](../designers/value-xelement-dynamic-property.md)



