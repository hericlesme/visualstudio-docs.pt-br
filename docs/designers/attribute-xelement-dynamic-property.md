---
title: "Atributo (Propriedade Dinâmica XElement) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-designers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8440fc7d-b3b4-4726-8ec8-492e6af79642
caps.latest.revision: "2"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: e3f373f4732aa80ac0e72f044e7a6a7f08e8a9be
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="attribute-xelement-dynamic-property"></a>Atributo (propriedade dinâmica de XElement)
Obtém um indexador usado para recuperar a instância do atributo que corresponde ao nome especificado expandido.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
elem.Attribute[{namespaceName}attribName]  
```  
  
## <a name="property-valuereturn-value"></a>Valor da propriedade/valor de retorno  
 Um indicador de tipo `XAttribute Item(String expandedName)`. Esse marcador utiliza o nome do atributo especificado e retorna <xref:System.Xml.Linq.XAttribute>correspondente, ou `null` se não houver nenhum atributo com o nome especificado.  
  
## <a name="remarks"></a>Comentários  
 Esta propriedade é equivalente ao método de <xref:System.Xml.Linq.XElement.Attribute%2A> da classe de <xref:System.Xml.Linq.XElement?displayProperty=fullName> .  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Xml.Linq.XElement.Attribute%2A?displayProperty=fullName>   
 [Propriedades Dinâmicas da Classe XElement](../designers/xelement-class-dynamic-properties.md)   
 [Value](../designers/value-xattribute-dynamic-property.md)