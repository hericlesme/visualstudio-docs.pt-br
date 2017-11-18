---
title: 'CA1019: Definir acessadores para argumentos de atributo | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1019
- DefineAccessorsForAttributeArguments
helpviewer_keywords:
- CA1019
- DefineAccessorsForAttributeArguments
ms.assetid: 197f2378-3c43-427e-80de-9ec25006c05c
caps.latest.revision: "19"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 9f04a49c8c68fcc597ecd98471b46932d467b365
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="ca1019-define-accessors-for-attribute-arguments"></a>CA1019: definir acessadores para argumentos de atributo
|||  
|-|-|  
|NomeDoTipo|DefineAccessorsForAttributeArguments|  
|CheckId|CA1019|  
|Categoria|Microsoft.Design|  
|Alteração Significativa|Não recentes|  
  
## <a name="cause"></a>Causa  
 No construtor, um atributo define os argumentos que não têm propriedades correspondentes.  
  
## <a name="rule-description"></a>Descrição da Regra  
 Os atributos podem definir argumentos obrigatórios que devem ser especificados quando você aplica o atributo a um destino. Eles também são conhecidos como argumentos posicionais porque são fornecidos a construtores de atributos como parâmetros posicionais. Para cada argumento obrigatório, o atributo também deve fornecer uma propriedade somente leitura correspondente de forma que o valor do argumento possa ser recuperado no tempo de execução. Esta regra verifica para cada parâmetro de construtor, você definiu a propriedade correspondente.  
  
 Os atributos também podem definir argumentos opcionais, que também são conhecidos como argumentos nomeados. Esses argumentos são fornecidos a construtores de atributo por nome e devem ter uma propriedade de leitura/gravação correspondente.  
  
 Para argumentos obrigatórios e opcionais, as propriedades correspondentes e os parâmetros do construtor devem usar o mesmo nome mas diferenciam maiusculas de minúsculas. Propriedades usam Pascal de maiusculas e minúsculas e maiusculas e minúsculas de concatenação de uso de parâmetros.  
  
## <a name="how-to-fix-violations"></a>Como Corrigir Violações  
 Para corrigir uma violação desta regra, adicione uma propriedade somente leitura para cada parâmetro de construtor que não tem um.  
  
## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos  
 Suprima um aviso de que essa regra se você não quiser que o valor do argumento obrigatório para ser recuperável.  
  
## <a name="custom-attributes-example"></a>Exemplo de atributos personalizados  
  
### <a name="description"></a>Descrição  
 O exemplo a seguir mostra dois atributos que definem um parâmetro (posicional) obrigatório. A primeira implementação do atributo está definida incorretamente. A implementação do segundo está correta.  
  
### <a name="code"></a>Código  
 [!code-csharp[FxCop.Design.AttributeAccessors#1](../code-quality/codesnippet/CSharp/ca1019-define-accessors-for-attribute-arguments_1.cs)]
 [!code-vb[FxCop.Design.AttributeAccessors#1](../code-quality/codesnippet/VisualBasic/ca1019-define-accessors-for-attribute-arguments_1.vb)]  
  
## <a name="positional-and-named-arguments"></a>Argumentos nomeados e posicionais  
  
### <a name="description"></a>Descrição  
 Argumentos nomeados e posicionais fazer claro para os consumidores de sua biblioteca, os argumentos são obrigatórios para o atributo e os argumentos são opcionais.  
  
 O exemplo a seguir mostra uma implementação de um atributo que tem argumentos posicionais e nomeados.  
  
### <a name="code"></a>Código  
 [!code-csharp[FxCop.Design.AttributeAccessorsNamed#1](../code-quality/codesnippet/CSharp/ca1019-define-accessors-for-attribute-arguments_2.cs)]  
  
### <a name="comments"></a>Comentários  
 O exemplo a seguir mostra como aplicar o atributo personalizado de duas propriedades.  
  
### <a name="code"></a>Código  
 [!code-csharp[FxCop.Design.AttributeAccessorsNamedApplied#1](../code-quality/codesnippet/CSharp/ca1019-define-accessors-for-attribute-arguments_3.cs)]  
  
## <a name="related-rules"></a>Regras relacionadas  
 [CA1813: evitar atributos não lacrados](../code-quality/ca1813-avoid-unsealed-attributes.md)  
  
## <a name="see-also"></a>Consulte também  
 [Atributos](/dotnet/standard/design-guidelines/attributes)