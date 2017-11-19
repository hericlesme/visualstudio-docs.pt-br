---
title: "CA1058: Os tipos não devem estender certos tipos base | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- TypesShouldNotExtendCertainBaseTypes
- CA1058
helpviewer_keywords:
- CA1058
- TypesShouldNotExtendCertainBaseTypes
ms.assetid: 8446ee40-beb1-49fa-8733-4d8e813471c0
caps.latest.revision: "24"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 45cddd908c53d129a230b998c6dad03196a31c49
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="ca1058-types-should-not-extend-certain-base-types"></a>CA1058: os tipos não devem estender determinados tipos base
|||  
|-|-|  
|NomeDoTipo|TypesShouldNotExtendCertainBaseTypes|  
|CheckId|CA1058|  
|Categoria|Microsoft.Design|  
|Alteração Significativa|Quebra|  
  
## <a name="cause"></a>Causa  
 Um tipo visível externamente estende determinados tipos de base. No momento, esta regra relata tipos que derivam de tipos a seguir:  
  
-   <xref:System.ApplicationException?displayProperty=fullName>  
  
-   <xref:System.Xml.XmlDocument?displayProperty=fullName>  
  
-   <xref:System.Collections.CollectionBase?displayProperty=fullName>  
  
-   <xref:System.Collections.DictionaryBase?displayProperty=fullName>  
  
-   <xref:System.Collections.Queue?displayProperty=fullName>  
  
-   <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>  
  
-   <xref:System.Collections.SortedList?displayProperty=fullName>  
  
-   <xref:System.Collections.Stack?displayProperty=fullName>  
  
## <a name="rule-description"></a>Descrição da Regra  
 Para [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] versão 1, era recomendado para derivar novas exceções de <xref:System.ApplicationException>. A recomendação foi alterado e novas exceções devem derivar de <xref:System.Exception?displayProperty=fullName> ou uma de suas subclasses de <xref:System> namespace.  
  
 Não crie uma subclasse de <xref:System.Xml.XmlDocument> se você deseja criar uma exibição XML de uma fonte de dados ou modelo de objeto subjacente.  
  
### <a name="non-generic-collections"></a>Coleções não genéricas  
 Usar e/ou estender coleções genéricas, sempre que possível. Não estenda coleções não genéricas no seu código, a menos que você enviou anteriormente.  
  
 **Exemplos de uso incorreto**  
  
```csharp  
public class MyCollection : CollectionBase  
{  
}  
  
public class MyReadOnlyCollection : ReadOnlyCollectionBase  
{  
}  
```  
  
 **Exemplos de uso correto**  
  
```csharp  
public class MyCollection : Collection<T>  
{  
}  
  
public class MyReadOnlyCollection : ReadOnlyCollection<T>  
{  
}  
```  
  
## <a name="how-to-fix-violations"></a>Como Corrigir Violações  
 Para corrigir uma violação desta regra, derive o tipo de um tipo base diferente ou uma coleção genérica.  
  
## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos  
 Não suprimir um aviso dessa regra para violações sobre <xref:System.ApplicationException>. É seguro suprimir um aviso dessa regra para violações sobre <xref:System.Xml.XmlDocument>. É seguro suprimir um aviso sobre uma coleção não genérica, se o código foi lançado anteriormente.