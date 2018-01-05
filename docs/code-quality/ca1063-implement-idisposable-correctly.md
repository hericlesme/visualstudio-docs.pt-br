---
title: 'CA1063: Implementar IDisposable corretamente | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ImplementIDisposableCorrectly
- CA1063
helpviewer_keywords:
- CA1063
- ImplementIDisposableCorrectly
ms.assetid: 12afb1ea-3a17-4a3f-a1f0-fcdb853e2359
caps.latest.revision: "17"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 33c9b3d7b3cdcfc49c3fac14e5ba3a2dcfc2fc49
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ca1063-implement-idisposable-correctly"></a>CA1063: implementar IDisposable corretamente
|||  
|-|-|  
|NomeDoTipo|ImplementIDisposableCorrectly|  
|CheckId|CA1063|  
|Categoria|Microsoft.Design|  
|Alteração Significativa|Não recentes|  
  
## <a name="cause"></a>Causa  
 `IDisposable`não é implementado corretamente. Alguns motivos para esse problema estão listados aqui:  
  
-   IDisposable é novamente implementado na classe.  
  
-   Finalizar novamente é substituído.  
  
-   Dispose é substituído.  
  
-   Dispose () não é público, sealed ou a chamada Dispose.  
  
-   Dispose (bool) não está protegido, virtual ou sem lacre.  
  
-   Tipos não lacrados, Dispose () deve chamar Dispose (True).  
  
-   Para tipos sem lacre, a implementação de finalização não chama um ou ambos os Dispose (bool) ou o finalizador da classe maiusculas.  
  
 Violação de qualquer um desses padrões irão disparar esse aviso.  
  
 Cada raiz sem lacre tipo IDisposable deve fornecer seu próprio método void Dispose (bool) virtual protegido. Descarte devem chamar Dipose(true) e Finalize deve chamar Dispose (False). Se você estiver criando um tipo de IDisposable raiz sem lacre, você deve definir Dispose (bool) e chamá-lo. Para obter mais informações, consulte [limpeza de recursos não gerenciados](/dotnet/standard/garbage-collection/unmanaged) no [diretrizes de Design do Framework](/dotnet/standard/design-guidelines/index) seção da documentação do .NET Framework.  
  
## <a name="rule-description"></a>Descrição da Regra  
 Todos os tipos IDisposable devem implementar o padrão Dispose corretamente.  
  
## <a name="how-to-fix-violations"></a>Como Corrigir Violações  
 Examine seu código e determinar que as seguintes resoluções corrigirá essa violação.  
  
-   Remova IDisposable da lista de interfaces que são implementados por {0} e substituir a implementação Dispose da classe base em vez disso.  
  
-   Remova o finalizador do tipo {0}, substitua Dispose (bool disposing) e coloque a lógica de finalização no caminho do código onde "disposing" é false.  
  
-   Remover {0}, substitua Dispose (bool disposing) e coloque a lógica de descarte no caminho do código onde "disposing" é true.  
  
-   Certifique-se de que {0} é declarado como público e lacrado.  
  
-   Renomear {0} 'Dispose' e certifique-se de que ele é declarado como público e lacrado.  
  
-   Certifique-se de que {0} é declarado como protegido, virtual e sem lacre.  
  
-   Modificar {0} para que ele chama Dispose (True), em seguida, chama GC. SuppressFinalize na instância atual do objeto ('this' ou 'Me' no [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) e, em seguida, retorna.  
  
-   Modificar {0} para que ele chama Dispose (False) e, em seguida, retorna.  
  
-   Se você estiver escrevendo uma classe de IDisposable raiz sem lacre, certifique-se de que a implementação de IDisposable segue o padrão descrito anteriormente nesta seção.  
  
## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos  
 Não suprima um aviso nessa regra.  
  
## <a name="pseudo-code-example"></a>Exemplo de código pseudo  
 O pseudocódigo a seguir fornece um exemplo geral de como Dispose (bool) devem ser implementadas em uma classe que usa gerenciada e recursos nativos.  
  
```  
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