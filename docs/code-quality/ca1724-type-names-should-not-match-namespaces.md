---
title: "CA1724: Os nomes de tipo não devem corresponder a Namespaces | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- TypeNamesShouldNotMatchNamespaces
- CA1724
helpviewer_keywords:
- TypeNamesShouldNotMatchNamespaces
- CA1724
ms.assetid: 329af3b5-5600-4101-831d-531ab3eb7060
caps.latest.revision: "17"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: f138958ce2dc83b7d258fbdb16986841e92d3484
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ca1724-type-names-should-not-match-namespaces"></a>CA1724: os nomes de tipo não devem corresponder a namespaces
|||  
|-|-|  
|NomeDoTipo|TypeNamesShouldNotMatchNamespaces|  
|CheckId|CA1724|  
|Categoria|Microsoft.Naming|  
|Alteração Significativa|Quebra|  
  
## <a name="cause"></a>Causa  
 Corresponde a um nome de tipo um [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] nomes de namespace em uma comparação que diferencia maiusculas de minúsculas.  
  
## <a name="rule-description"></a>Descrição da Regra  
 Os nomes de tipo não devem corresponder aos nomes de namespaces definidos na biblioteca de classes do [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]. A violação dessa regra pode reduzir a usabilidade da biblioteca.  
  
## <a name="how-to-fix-violations"></a>Como Corrigir Violações  
 Selecione um nome de tipo que não coincide com o nome de um [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] namespace da biblioteca de classe.  
  
## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos  
 Para novos desenvolvimentos, nenhum conhecidos situações ocorrer onde você deve suprimir um aviso dessa regra. Antes de você suprimir o aviso, considere cuidadosamente como os usuários da sua biblioteca podem ser confuso com o nome correspondente. Para bibliotecas de envio, você talvez precise suprimir um aviso dessa regra.