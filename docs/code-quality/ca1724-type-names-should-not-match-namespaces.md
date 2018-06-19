---
title: 'CA1724: os nomes de tipo não devem corresponder a namespaces'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- TypeNamesShouldNotMatchNamespaces
- CA1724
helpviewer_keywords:
- TypeNamesShouldNotMatchNamespaces
- CA1724
ms.assetid: 329af3b5-5600-4101-831d-531ab3eb7060
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3944aba1a8b967e8da2bee007a4bbd4bacf4d6b1
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31915822"
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