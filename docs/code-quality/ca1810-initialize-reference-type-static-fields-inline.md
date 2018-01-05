---
title: "CA1810: Tipo de referência inicializar campos estáticos embutido | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- InitializeReferenceTypeStaticFieldsInline
- CA1810
helpviewer_keywords:
- InitializeReferenceTypeStaticFieldsInline
- CA1810
ms.assetid: e9693118-a914-4efb-9550-ec659d8d97d2
caps.latest.revision: "21"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 4b3a6ffe04be6116fddc225d0820d3709644fe52
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ca1810-initialize-reference-type-static-fields-inline"></a>CA1810: inicializar campos estáticos de tipo de referência embutido
|||  
|-|-|  
|NomeDoTipo|InitializeReferenceTypeStaticFieldsInline|  
|CheckId|CA1810|  
|Categoria|Microsoft.Performance|  
|Alteração Significativa|Não recentes|  
  
## <a name="cause"></a>Causa  
 Um tipo de referência declara um construtor estático explícito.  
  
## <a name="rule-description"></a>Descrição da Regra  
 Quando um tipo declara um construtor estático explícito, o compilador JIT (just-in-time) adiciona uma verificação a cada método estático e construtor de instância do tipo para garantir que o construtor estático tenha sido chamado anteriormente. Inicialização estática é acionada quando qualquer membro estático é acessado ou quando uma instância do tipo é criada. No entanto, a inicialização estática não será disparada se você declara uma variável do tipo, mas não usá-la, que pode ser importante se a inicialização altera o estado global.  
  
 Quando todos os dados estáticos são inicializado embutido e não está declarado como um construtor estático explícito, compiladores do Microsoft intermediate language (MSIL) adiciona a `beforefieldinit` sinalizador e um construtor estático implícito, que inicializa os dados estáticos, para o tipo MSIL definição. Quando o compilador JIT encontra o `beforefieldinit` sinalizador, na maioria das vezes, as verificações de construtor estático não são adicionadas. Inicialização estática é garantida para ocorrer a qualquer momento antes de todos os campos estáticos são acessados, mas não antes de um construtor estático de instância ou método é invocado. Observe que a inicialização estática pode ocorrer a qualquer momento depois que uma variável do tipo é declarada.  
  
 As verificações de construtor estático podem diminuir o desempenho. Geralmente, um construtor estático é usado apenas para inicializar campos estáticos, na qual o caso, você deve apenas certifique-se que a inicialização estática ocorre antes do primeiro acesso de um campo estático. O `beforefieldinit` comportamento é apropriado para esses e a maioria dos outros tipos. Só é inadequado quando inicialização estática afeta o estado global e uma das seguintes opções for verdadeira:  
  
-   O efeito sobre o estado global é caro e não será necessário se o tipo não é usado.  
  
-   Os efeitos de estado global podem ser acessados sem acessar todos os campos do tipo estáticos.  
  
## <a name="how-to-fix-violations"></a>Como Corrigir Violações  
 Para corrigir uma violação dessa regra, inicialize todos os dados estáticos quando declarados e remova o construtor estático.  
  
## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos  
 É seguro suprimir um aviso de que essa regra se o desempenho não for uma preocupação; ou se as alterações de estado global que são causadas por inicialização estática são caras ou devem ser garantido ocorrer antes que um método estático do tipo é chamado ou uma instância do tipo é criada.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra um tipo `StaticConstructor`, que viola a regra e um tipo, `NoStaticConstructor`, que substitui o construtor estático com a inicialização embutido para satisfazer a regra.  
  
 [!code-csharp[FxCop.Performance.RefTypeStaticCtor#1](../code-quality/codesnippet/CSharp/ca1810-initialize-reference-type-static-fields-inline_1.cs)]
 [!code-vb[FxCop.Performance.RefTypeStaticCtor#1](../code-quality/codesnippet/VisualBasic/ca1810-initialize-reference-type-static-fields-inline_1.vb)]  
  
 Observe a adição do `beforefieldinit` sinalizador na definição do MSIL para o `NoStaticConstructor` classe.  
  
 **. class pública automática ansi StaticConstructor**  
 **estende [mscorlib]System.Object**  
**{**  
**} / / fim da classe StaticConstructor**  
**. class pública automática ansi beforefieldinit NoStaticConstructor**  
 **estende [mscorlib]System.Object**  
**{**  
**} / / fim da classe NoStaticConstructor**   
## <a name="related-rules"></a>Regras relacionadas  
 [CA2207: inicializar campos estáticos de tipo de valor embutido](../code-quality/ca2207-initialize-value-type-static-fields-inline.md)