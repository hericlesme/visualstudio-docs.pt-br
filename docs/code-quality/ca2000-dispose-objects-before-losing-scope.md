---
title: 'CA2000: descartar objetos antes de perder o escopo'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2000
- Dispose objects before losing scope
- DisposeObjectsBeforeLosingScope
helpviewer_keywords:
- CA2000
- DisposeObjectsBeforeLosingScope
ms.assetid: 0c3d7d8d-b94d-46e8-aa4c-38df632c1463
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6b492324b87bfc25741492669b7c659c43fc9765
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31920399"
---
# <a name="ca2000-dispose-objects-before-losing-scope"></a>CA2000: descartar objetos antes de perder o escopo
|||
|-|-|
|NomeDoTipo|DisposeObjectsBeforeLosingScope|
|CheckId|CA2000|
|Categoria|Microsoft.Reliability|
|Alteração Significativa|Não recentes|

## <a name="cause"></a>Causa
 Um objeto de local de um <xref:System.IDisposable> tipo é criado, mas o objeto não for descartado antes de todas as referências ao objeto fora do escopo.

## <a name="rule-description"></a>Descrição da Regra
 Se um objeto descartável não for explicitamente descartado antes de todas as referências a ele estão fora do escopo, o objeto será descartado em algum momento indeterminado quando o coletor de lixo é executado o finalizador do objeto. Como pode ocorrer um evento excepcional que impedirá o finalizador do objeto de execução, o objeto deve ser explicitamente descartado.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir uma violação desta regra, chame <xref:System.IDisposable.Dispose%2A> no objeto antes de todas as referências a ele estão fora do escopo.

 Observe que você pode usar o `using` instrução (`Using` na [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) para incluir objetos que implementam `IDisposable`. Objetos que são encapsulados dessa maneira serão descartados automaticamente ao final do `using` bloco.

 A seguir estão algumas situações em que a instrução using não é suficiente para proteger os objetos IDisposable e pode causar CA2000 ocorra.

-   Retornar um objeto descartável requer que o objeto for construído em um bloco try/finally fora de uso de um bloco.

-   Membros de inicialização de um objeto descartável não devem ser feito no construtor do uso de uma instrução.

-   Construtores protegidos apenas pelo manipulador de exceção de aninhamento. Por exemplo,

    ```csharp
    using (StreamReader sr = new StreamReader(new FileStream("C:\myfile.txt", FileMode.Create)))
    { ... }
    ```

     faz com que CA2000 porque uma falha na construção do objeto StreamReader pode resultar no objeto FileStream nunca que está sendo fechado.

-   Objetos dinâmicos devem usar um objeto de sombra para implementar o padrão Dispose de objetos IDisposable.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 Não suprimir um aviso dessa regra, a menos que você chamou um método em seu objeto que chama `Dispose`, como <xref:System.IO.Stream.Close%2A>, ou se o método que gerou o aviso retornará um objeto IDisposable encapsula o objeto.

## <a name="related-rules"></a>Regras relacionadas
 [CA2213: os campos descartáveis devem ser descartados](../code-quality/ca2213-disposable-fields-should-be-disposed.md)

 [CA2202: não descartar objetos várias vezes](../code-quality/ca2202-do-not-dispose-objects-multiple-times.md)

## <a name="example"></a>Exemplo
 Se você estiver implementando um método que retorna um objeto descartável, use um bloco try/finally sem um bloco catch para certificar-se de que o objeto é descartado. Usando um bloco try/finally, você permitir exceções ser gerado no ponto de falha e certifique-se de que o objeto é descartado.

 O método OpenPort1, a chamada para abrir o objeto ISerializable SerialPort ou a chamada para SomeMethod pode falhar. Um aviso CA2000 é gerado com essa implementação.

 No método OpenPort2, os dois objetos de SerialPort são declarado e está definida como null:

-   `tempPort`, que é usado para testar as operações do método tenha êxito.

-   `port`, que é usado para o valor de retorno do método.

 O `tempPort` é criada e aberta em uma `try` bloco e qualquer outro necessários o trabalho é executado no mesmo `try` bloco. No final do `try` bloco, a porta aberta é atribuído para o `port` objeto que será retornado e a `tempPort` objeto é definido como `null`.

 O `finally` bloco verifica o valor de `tempPort`. Se não for null, houve falha na operação no método, e `tempPort` é fechado para certificar-se de que todos os recursos são liberados. O objeto de porta retornada conterá o objeto de SerialPort aberto se as operações do método foi bem-sucedida, ou ele será nulo se uma operação falhou.

```csharp
public SerialPort OpenPort1(string portName)
{
   SerialPort port = new SerialPort(portName);
   port.Open();  //CA2000 fires because this might throw
   SomeMethod(); //Other method operations can fail
   return port;
}

public SerialPort OpenPort2(string portName)
{
   SerialPort tempPort = null;
   SerialPort port = null;
   try
   {
      tempPort = new SerialPort(portName);
      tempPort.Open();
      SomeMethod();
      //Add any other methods above this line
      port = tempPort;
      tempPort = null;

   }
   finally
   {
      if (tempPort != null)
      {
         tempPort.Close();
      }
   }
   return port;
}
```

```vb
Public Function OpenPort1(ByVal PortName As String) As SerialPort

   Dim port As New SerialPort(PortName)
   port.Open()    'CA2000 fires because this might throw
   SomeMethod()   'Other method operations can fail
   Return port

End Function


Public Function OpenPort2(ByVal PortName As String) As SerialPort

   Dim tempPort As SerialPort = Nothing
   Dim port As SerialPort = Nothing

   Try
      tempPort = New SerialPort(PortName)
      tempPort.Open()
      SomeMethod()
      'Add any other methods above this line
      port = tempPort
      tempPort = Nothing

   Finally
      If Not tempPort Is Nothing Then
         tempPort.Close()
      End If


   End Try

   Return port

End Function
```

## <a name="example"></a>Exemplo
 Por padrão, o [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] compilador tem operadores aritméticos todos verificação de estouro. Portanto, qualquer operação aritmética do Visual Basic poderá gerar um <xref:System.OverflowException>. Isso pode levar a violações inesperadas nas regras, como CA2000. Por exemplo, a seguinte função CreateReader1 produzirá uma violação CA2000 porque o compilador do Visual Basic está emitindo um estouro de verificação de instrução para a adição que pode gerar uma exceção que possam causar StreamReader para não ser descartado.

 Para corrigir isso, você pode desativar a emissão de verificações de estouro pelo compilador do Visual Basic no seu projeto ou você pode modificar seu código como a seguinte função CreateReader2.

 Para desabilitar a emissão de verificações de estouro, clique no nome do projeto no Gerenciador de soluções e, em seguida, clique em **propriedades**. Clique em **compilar**, clique em **opções avançadas de compilação**e, em seguida, verifique **remover verificações de estouro de inteiro**.

  [!code-vb[FxCop.Reliability.CA2000.DisposeObjectsBeforeLosingScope#1](../code-quality/codesnippet/VisualBasic/ca2000-dispose-objects-before-losing-scope-vboverflow_1.vb)]

## <a name="see-also"></a>Consulte também
 <xref:System.IDisposable> [Padrão de Dispose](/dotnet/standard/design-guidelines/dispose-pattern)