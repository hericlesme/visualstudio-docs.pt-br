---
title: "CA1711: Os identificadores não devem ter sufixo incorreto | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1711
- IdentifiersShouldNotHaveIncorrectSuffix
helpviewer_keywords:
- CA1711
- IdentifiersShouldNotHaveIncorrectSuffix
ms.assetid: a63359ab-386d-44ae-b381-ee3a983aca29
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 6cde73eeec2b6a73f25f714c41976d3d0513e939
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ca1711-identifiers-should-not-have-incorrect-suffix"></a>CA1711: os identificadores não devem ter sufixo incorreto
|||  
|-|-|  
|NomeDoTipo|IdentifiersShouldNotHaveIncorrectSuffix|  
|CheckId|CA1711|  
|Categoria|Microsoft.Naming|  
|Alteração Significativa|Quebra|  
  
## <a name="cause"></a>Causa  
 Um identificador possuem um sufixo incorreto.  
  
## <a name="rule-description"></a>Descrição da Regra  
 Por convenção, somente os nomes dos tipos que estendem determinados tipos de base ou que implementam determinadas interfaces, ou tipos derivados desses tipos, devem terminar com sufixos reservados específicos. Outros nomes de tipo não devem usar esses sufixos reservados.  
  
 A tabela a seguir lista os sufixos reservados e os tipos base e interfaces às quais eles estão associados.  
  
|Sufixo|Interface/tipo de base|  
|------------|--------------------------|  
|Atributo|<xref:System.Attribute?displayProperty=fullName>|  
|Coleção|<xref:System.Collections.ICollection?displayProperty=fullName><br /><br /> <xref:System.Collections.IEnumerable?displayProperty=fullName><br /><br /> <xref:System.Collections.Queue?displayProperty=fullName><br /><br /> <xref:System.Collections.Stack?displayProperty=fullName><br /><br /> <xref:System.Collections.Generic.ICollection%601?displayProperty=fullName><br /><br /> <xref:System.Data.DataSet?displayProperty=fullName><br /><br /> <xref:System.Data.DataTable?displayProperty=fullName>|  
|Dicionário|<xref:System.Collections.IDictionary?displayProperty=fullName><br /><br /> <xref:System.Collections.Generic.IDictionary%602?displayProperty=fullName>|  
|EventArgs|<xref:System.EventArgs?displayProperty=fullName>|  
|EventHandler|Um representante do manipulador de eventos|  
|Exceção|<xref:System.Exception?displayProperty=fullName>|  
|Permissão|<xref:System.Security.IPermission?displayProperty=fullName>|  
|Fila|<xref:System.Collections.Queue?displayProperty=fullName>|  
|Pilha|<xref:System.Collections.Stack?displayProperty=fullName>|  
|Fluxo|<xref:System.IO.Stream?displayProperty=fullName>|  
  
 Além disso, os seguintes sufixos devem **não** ser usado:  
  
-   delegado  
  
-   Enum  
  
-   Implementação - use 'Core' em vez disso  
  
-   Ex ou sufixo semelhante para distingui-lo de uma versão anterior do mesmo tipo  
  
 Convenções de nomenclatura fornecem uma aparência comum para bibliotecas de destino do common language runtime. Isso reduz a curva de aprendizado que é necessário para novas bibliotecas de software e aumenta a confiança do cliente que a biblioteca foi desenvolvida por uma pessoa com experiência em desenvolvimento de código gerenciado.  
  
## <a name="how-to-fix-violations"></a>Como Corrigir Violações  
 Remova o sufixo de nome de tipo.  
  
## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos  
 Não suprima um aviso dessa regra, a menos que o sufixo tem um significado ambíguo no domínio do aplicativo.  
  
## <a name="related-rules"></a>Regras relacionadas  
 [CA1710: os identificadores devem ter o sufixo correto](../code-quality/ca1710-identifiers-should-have-correct-suffix.md)  
  
## <a name="see-also"></a>Consulte também  
 [Atributos](/dotnet/standard/design-guidelines/attributes)   
 [Manipulando e acionando eventos](/dotnet/standard/events/index)  