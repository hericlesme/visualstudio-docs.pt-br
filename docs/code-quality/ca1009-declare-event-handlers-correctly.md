---
title: 'CA1009: declarar manipuladores de eventos corretamente'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1009
- DeclareEventHandlersCorrectly
helpviewer_keywords:
- CA1009
- DeclareEventHandlersCorrectly
ms.assetid: ab65c471-1449-49d2-9896-7b9af74284b4
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ac922b2fcf34c3fceff5ad7f82675bac38fa4696
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31899280"
---
# <a name="ca1009-declare-event-handlers-correctly"></a>CA1009: declarar manipuladores de eventos corretamente
|||
|-|-|
|NomeDoTipo|DeclareEventHandlersCorrectly|
|CheckId|CA1009|
|Categoria|Microsoft.Design|
|Alteração Significativa|Quebra|

## <a name="cause"></a>Causa
 Um representante que manipula um evento público ou protegido não tem a assinatura correta, tipo de retorno, ou nomes de parâmetro.

## <a name="rule-description"></a>Descrição da Regra
 Os métodos de manipulador de eventos utilizam dois parâmetros. A primeira é do tipo <xref:System.Object?displayProperty=fullName> e é denominado 'remetente'. Este é o objeto que acionou o evento. O segundo parâmetro é do tipo <xref:System.EventArgs?displayProperty=fullName> e é chamado 'e'. Esses são os dados associados ao evento. Por exemplo, se o evento é gerado sempre que um arquivo é aberto, os dados de evento normalmente contém o nome do arquivo.

 Métodos do manipulador de eventos não devem retornar um valor. No c# linguagem de programação, isso é indicado pelo tipo de retorno `void`. Um manipulador de eventos pode chamar vários métodos em vários objetos. Se os métodos foram autorizados a retornar um valor, vários valores de retorno deve ocorrer para cada evento, e apenas o valor do último método chamado estaria disponível.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir uma violação desta regra, corrija a assinatura, tipo de retorno ou nomes de parâmetros do delegado. Para obter detalhes, consulte o exemplo a seguir.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 Não suprima um aviso nessa regra.

## <a name="example"></a>Exemplo
 O exemplo a seguir mostra um delegado que é adequado para a manipulação de eventos. Os métodos que podem ser invocados por este manipulador de eventos de acordo com a assinatura especificada nas diretrizes de Design. `AlarmEventHandler` é o nome do tipo do delegado. `AlarmEventArgs` deriva da classe base de dados de eventos, <xref:System.EventArgs>, e mantém dados de evento do alarme.

 [!code-cpp[FxCop.Design.EventsTwoParams#1](../code-quality/codesnippet/CPP/ca1009-declare-event-handlers-correctly_1.cpp)]
 [!code-csharp[FxCop.Design.EventsTwoParams#1](../code-quality/codesnippet/CSharp/ca1009-declare-event-handlers-correctly_1.cs)]
 [!code-vb[FxCop.Design.EventsTwoParams#1](../code-quality/codesnippet/VisualBasic/ca1009-declare-event-handlers-correctly_1.vb)]

## <a name="related-rules"></a>Regras relacionadas
 [CA2109: examinar manipuladores de eventos visíveis](../code-quality/ca2109-review-visible-event-handlers.md)

## <a name="see-also"></a>Consulte também
 <xref:System.EventArgs?displayProperty=fullName> <xref:System.Object?displayProperty=fullName> [Manipulando e acionando eventos](/dotnet/standard/events/index)