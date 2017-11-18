---
title: "CA1053: Os tipos de espaços reservados estáticos não devem ter construtores | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- StaticHolderTypesShouldNotHaveConstructors
- CA1053
helpviewer_keywords:
- CA1053
- StaticHolderTypesShouldNotHaveConstructors
ms.assetid: 10302b9a-fa5e-4935-a06a-513d9600f613
caps.latest.revision: "15"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: a9e9d6272fbb21644daab96bb3ccd7d02b023840
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="ca1053-static-holder-types-should-not-have-constructors"></a>CA1053: os tipos de suporte estático não devem ter construtores
|||  
|-|-|  
|NomeDoTipo|StaticHolderTypesShouldNotHaveConstructors|  
|CheckId|CA1053|  
|Categoria|Microsoft.Design|  
|Alteração Significativa|Quebra|  
  
## <a name="cause"></a>Causa  
 Um tipo público ou público aninhado declara apenas membros estáticos e tem um construtor padrão público ou protegido.  
  
## <a name="rule-description"></a>Descrição da Regra  
 O construtor é desnecessário porque chamar membros estáticos não exige uma instância do tipo. Além disso, porque o tipo não tem membros não estáticos, criar uma instância não fornece acesso a qualquer um dos membros do tipo.  
  
## <a name="how-to-fix-violations"></a>Como Corrigir Violações  
 Para corrigir uma violação desta regra, remova o construtor padrão ou torná-lo particular.  
  
> [!NOTE]
>  Alguns compiladores cria automaticamente um construtor padrão público se o tipo não define nenhum construtor. Se esse for o caso com seu tipo, adicione um construtor privado padrão para eliminar a violação.  
  
## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos  
 Não suprima um aviso nessa regra. A presença do construtor sugere o tipo não é um tipo estático.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra um tipo que violam essa regra. Observe que não há nenhum construtor padrão no código-fonte. Quando esse código é compilado em um assembly, o compilador c# inserirá um construtor padrão, que será violam essa regra. Para corrigir isso, declare um construtor particular.  
  
 [!code-csharp[FxCop.Design.StaticTypes#1](../code-quality/codesnippet/CSharp/ca1053-static-holder-types-should-not-have-constructors_1.cs)]