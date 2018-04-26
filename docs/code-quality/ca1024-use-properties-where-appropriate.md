---
title: 'CA1024: usar propriedades quando apropriado'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- UsePropertiesWhereAppropriate
- CA1024
helpviewer_keywords:
- CA1024
- UsePropertiesWhereAppropriate
ms.assetid: 3a04f765-af7c-4872-87ad-9cc29e8e657f
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 58f27aebba0bd8a126928e01f13c65bec3381742
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="ca1024-use-properties-where-appropriate"></a>CA1024: usar propriedades quando apropriado
|||
|-|-|
|NomeDoTipo|UsePropertiesWhereAppropriate|
|CheckId|CA1024|
|Categoria|Microsoft.Design|
|Alteração Significativa|Quebra|

## <a name="cause"></a>Causa
 Um método público ou protegido tem um nome que começa com `Get`, não usa nenhum parâmetro e retorna um valor que não é uma matriz.

## <a name="rule-description"></a>Descrição da Regra
 Na maioria dos casos, propriedades representam os dados e os métodos executam ações. As propriedades são acessadas como campos, o que torna mais fácil de usar. Um método é uma boa candidata para se tornar uma propriedade, se houver uma das seguintes condições:

-   Não requer argumentos e retorna as informações de estado de um objeto.

-   Aceita um único argumento para definir a parte do estado de um objeto.

 Propriedades de se comportar como se eles são campos; Se o método não for possível, ele não deve ser alterado para uma propriedade. Métodos são melhores que as propriedades nas seguintes situações:

-   O método executa uma operação demorada. O método é perceivably mais lento do que o tempo necessário para definir ou obter o valor de um campo.

-   O método realiza uma conversão. Acessar um campo não retornou uma versão convertida dos dados que ele armazena.

-   O método Get tem um efeito colateral observável. Recuperar o valor de um campo não produzir efeitos colaterais.

-   A ordem de execução é importante. Definir o valor de um campo não contam com a ocorrência de outras operações.

-   Chamar o método duas vezes em sucessão gera resultados diferentes.

-   O método é estático, mas retorna um objeto que pode ser alterado pelo chamador. Recuperar o valor de um campo não permite que o chamador alterar os dados que são armazenados no campo.

-   O método retorna uma matriz.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir uma violação desta regra, altere o método para uma propriedade.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 Suprima um aviso de que essa regra se o método atender pelo menos um dos critérios listados anteriormente.

## <a name="controlling-property-expansion-in-the-debugger"></a>Controlando a expansão de propriedade no depurador
 Um motivo que os programadores evitar o uso de uma propriedade é porque eles não deseja que o depurador para expandir automaticamente. Por exemplo, a propriedade pode envolver a alocação de um objeto grande ou chamar um P/Invoke, mas ele não terá nenhum efeito colateral observável realmente.

 Você pode impedir que o depurador expansão automática propriedades aplicando <xref:System.Diagnostics.DebuggerBrowsableAttribute?displayProperty=fullName>. O exemplo a seguir mostra esse atributo está sendo aplicado a uma propriedade de instância.

```vb
Imports System
Imports System.Diagnostics

Namespace Microsoft.Samples

    Public Class TestClass

        ' [...]

        <DebuggerBrowsable(DebuggerBrowsableState.Never)> _
        Public ReadOnly Property LargeObject() As LargeObject
            Get
                ' Allocate large object
                ' [...]
            End Get
        End Property

    End Class

End Namespace
```

```csharp

      using System;
using System.Diagnostics;

namespace Microsoft.Samples
{
    publicclass TestClass
    {
        // [...]

        [DebuggerBrowsable(DebuggerBrowsableState.Never)]
        public LargeObject LargeObject
        {
            get
            {
                // Allocate large object
                // [...]

        }
    }
}
```

## <a name="example"></a>Exemplo
 O exemplo a seguir contém vários métodos que devem ser convertidas em propriedades e vários que devem não porque eles não se comportam como campos.

 [!code-csharp[FxCop.Design.MethodsProperties#1](../code-quality/codesnippet/CSharp/ca1024-use-properties-where-appropriate_1.cs)]