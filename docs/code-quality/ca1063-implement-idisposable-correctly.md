---
title: 'CA1063: implementar IDisposable corretamente'
ms.date: 02/12/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- ImplementIDisposableCorrectly
- CA1063
helpviewer_keywords:
- CA1063
- ImplementIDisposableCorrectly
ms.assetid: 12afb1ea-3a17-4a3f-a1f0-fcdb853e2359
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ac3827dd8ed34a118bb3e4eaaed47bf7400cef90
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="ca1063-implement-idisposable-correctly"></a>CA1063: implementar IDisposable corretamente

|||
|-|-|
|NomeDoTipo|ImplementIDisposableCorrectly|
|CheckId|CA1063|
|Categoria|Microsoft.Design|
|Alteração Significativa|Não recentes|

## <a name="cause"></a>Causa

`IDisposable` não é implementado corretamente. Alguns motivos para esse problema estão listados aqui:

- IDisposable é novamente implementado na classe.

- Finalizar novamente é substituído.

- Dispose é substituído.

- Dispose () não é público, sealed ou a chamada Dispose.

- Dispose (bool) não está protegido, virtual ou sem lacre.

- Tipos não lacrados, Dispose () deve chamar Dispose (True).

- Para tipos sem lacre, a implementação de finalização não chama um ou ambos os Dispose (bool) ou o finalizador da classe maiusculas.

Violação de qualquer um desses padrões irão disparar esse aviso.

Cada tipo que declara e implementa a interface IDisposable deve fornecer seu próprio método void Dispose (bool) virtual protegido. Descarte devem chamar Dipose(true) e Finalize deve chamar Dispose (False). Se você estiver criando um tipo que declara e implementa a interface IDisposable, você deve definir Dispose (bool) e chamá-lo. Para obter mais informações, consulte [limpeza de recursos não gerenciados](/dotnet/standard/garbage-collection/unmanaged) no [diretrizes de design do .NET Framework](/dotnet/standard/design-guidelines/index).

## <a name="rule-description"></a>Descrição da regra

Todos os tipos IDisposable devem implementar o padrão Dispose corretamente.

## <a name="how-to-fix-violations"></a>Como corrigir violações

Examine seu código e determinar que as seguintes resoluções corrigirá essa violação.

- Remova IDisposable da lista de interfaces implementadas por {0} e substituir a implementação Dispose da classe base em vez disso.

- Remova o finalizador do tipo {0}, substitua Dispose (bool disposing) e coloque a lógica de finalização no caminho do código onde "disposing" é false.

- Remover {0}, substitua Dispose (bool disposing) e coloque a lógica de descarte no caminho do código onde "disposing" é true.

- Certifique-se de que {0} é declarado como público e lacrado.

- Renomear {0} 'Dispose' e certifique-se de que ele é declarado como público e lacrado.

- Verifique se {0} é declarado como protegido, virtual e sem lacre.

- Modificar {0} para que ele chama Dispose (True), em seguida, chama GC. SuppressFinalize na instância atual do objeto ('this' ou 'Me' no [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) e, em seguida, retorna.

- Modificar {0} para que ele chama Dispose (False) e, em seguida, retorna.

- Se você estiver criando um tipo que declara e implementa a interface IDisposable, certifique-se de que a implementação de IDisposable segue o padrão descrito anteriormente nesta seção.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos

Não suprima um aviso nessa regra.

## <a name="pseudo-code-example"></a>Exemplo de código pseudo

O pseudocódigo a seguir fornece um exemplo geral de como Dispose (bool) devem ser implementadas em uma classe que usa gerenciada e recursos nativos.

```csharp
public class Resource : IDisposable
{
    private IntPtr nativeResource = Marshal.AllocHGlobal(100);
    private AnotherResource managedResource = new AnotherResource();

    // Dispose() calls Dispose(true)
    public void Dispose()
    {
        Dispose(true);
        GC.SuppressFinalize(this);
    }

    // NOTE: Leave out the finalizer altogether if this class doesn't
    // own unmanaged resources itself, but leave the other methods
    // exactly as they are.
    ~Resource()
    {
        // Finalizer calls Dispose(false)
        Dispose(false);
    }

    // The bulk of the clean-up code is implemented in Dispose(bool)
    protected virtual void Dispose(bool disposing)
    {
        if (disposing)
        {
            // free managed resources
            if (managedResource != null)
            {
                managedResource.Dispose();
                managedResource = null;
            }
        }
        // free native resources if there are any.
        if (nativeResource != IntPtr.Zero)
        {
            Marshal.FreeHGlobal(nativeResource);
            nativeResource = IntPtr.Zero;
        }
    }
}
```