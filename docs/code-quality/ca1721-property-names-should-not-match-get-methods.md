---
title: "Ca1721 os: Nomes de propriedade não devem corresponder a métodos get | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1721
- PropertyNamesShouldNotMatchGetMethods
helpviewer_keywords:
- CA1721
- PropertyNamesShouldNotMatchGetMethods
ms.assetid: 45a0e853-1f06-4688-af1b-cc634409e295
caps.latest.revision: "17"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: eb0a1b45276e6563ab645100377dec25a9060e06
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ca1721-property-names-should-not-match-get-methods"></a>CA1721: os nomes de propriedade não devem corresponder a métodos get
|||  
|-|-|  
|NomeDoTipo|PropertyNamesShouldNotMatchGetMethods|  
|CheckId|CA1721|  
|Categoria|Microsoft.Naming|  
|Alteração Significativa|Quebra|  
  
## <a name="cause"></a>Causa  
 O nome de um membro público ou protegido começa com 'Get' e, caso contrário, corresponde ao nome de uma propriedade pública ou protegida. Por exemplo, um tipo que contém um método chamado 'GetColor' e uma propriedade denominada 'Color' viola essa regra.  
  
## <a name="rule-description"></a>Descrição da Regra  
 Propriedades e métodos get devem ter nomes que distinguem claramente sua função.  
  
 Convenções de nomenclatura fornecem uma aparência comum para bibliotecas de destino do common language runtime. Isso reduz o tempo que é necessário para aprender uma nova biblioteca de software e aumenta a confiança do cliente que a biblioteca foi desenvolvida por uma pessoa com experiência em desenvolvimento de código gerenciado.  
  
## <a name="how-to-fix-violations"></a>Como Corrigir Violações  
 Altere o nome para que ele não coincide com o nome de um método que é prefixado com 'Get'.  
  
## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos  
 Não suprima um aviso nessa regra.  
  
> [!NOTE]
>  Esse aviso pode ser excluído se o método Get é causado pela implementação de interface IExtenderProvider.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir contém um método e a propriedade que violam essa regra.  
  
 [!code-csharp[FxCop.Naming.GetMethod#1](../code-quality/codesnippet/CSharp/ca1721-property-names-should-not-match-get-methods_1.cs)]
 [!code-vb[FxCop.Naming.GetMethod#1](../code-quality/codesnippet/VisualBasic/ca1721-property-names-should-not-match-get-methods_1.vb)]  
  
## <a name="related-rules"></a>Regras relacionadas  
 [CA1024: usar propriedades quando apropriado](../code-quality/ca1024-use-properties-where-appropriate.md)