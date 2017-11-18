---
title: "CA1044: As propriedades não devem ser somente gravação | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- PropertiesShouldNotBeWriteOnly
- CA1044
helpviewer_keywords:
- CA1044
- PropertiesShouldNotBeWriteOnly
ms.assetid: 8386bf3a-b161-4841-bf8b-92591595aea9
caps.latest.revision: "15"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: c81c76fc20262d781e89e8ec786f7a640f6ee026
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="ca1044-properties-should-not-be-write-only"></a>CA1044: as propriedades não devem ser somente leitura
|||  
|-|-|  
|NomeDoTipo|PropertiesShouldNotBeWriteOnly|  
|CheckId|CA1044|  
|Categoria|Microsoft.Design|  
|Alteração Significativa|Quebra|  
  
## <a name="cause"></a>Causa  
 A propriedade pública ou protegida tem um acessador set, mas não tem um acessador get.  
  
## <a name="rule-description"></a>Descrição da Regra  
 Obter acessadores fornecem acesso de leitura a uma propriedade e acessadores set fornecem acesso de gravação. Embora seja aceitável e normalmente necessário ter uma propriedade somente leitura, as diretrizes de design proíbem o uso de propriedades somente gravação. Isso ocorre porque, permitindo que um usuário defina um valor e, em seguida, impedindo que o usuário exibir o valor não oferece segurança. Além disso, sem acesso de leitura, o estado de objetos compartilhados não pode ser exibido, o que limita sua utilidade.  
  
## <a name="how-to-fix-violations"></a>Como Corrigir Violações  
 Para corrigir uma violação desta regra, adicione um acessador get para a propriedade. Como alternativa, se o comportamento de uma propriedade somente gravação for necessário, considere converter essa propriedade para um método.  
  
## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos  
 É altamente recomendável que você não suprimir um aviso dessa regra.  
  
## <a name="example"></a>Exemplo  
 No exemplo a seguir, `BadClassWithWriteOnlyProperty` é um tipo com uma propriedade somente gravação. `GoodClassWithReadWriteProperty`contém o código corrigido.  
  
 [!code-vb[FxCop.Design.PropertiesNotWriteOnly#1](../code-quality/codesnippet/VisualBasic/ca1044-properties-should-not-be-write-only_1.vb)]
 [!code-csharp[FxCop.Design.PropertiesNotWriteOnly#1](../code-quality/codesnippet/CSharp/ca1044-properties-should-not-be-write-only_1.cs)]