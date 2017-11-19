---
title: "CA2202: Não descartar objetos várias vezes | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA2202
- Do not dispose objects multiple times
- DoNotDisposeObjectsMultipleTimes
helpviewer_keywords: CA2202
ms.assetid: fa85349a-cf1e-42c8-a86b-eacae1f8bd96
caps.latest.revision: "20"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: ab5acc92df96c416cd614ac18ac66ff34d142a22
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="ca2202-do-not-dispose-objects-multiple-times"></a>CA2202: não descartar objetos várias vezes
|||  
|-|-|  
|NomeDoTipo|DoNotDisposeObjectsMultipleTimes|  
|CheckId|CA2202|  
|Categoria|Microsoft.Usage|  
|Alteração Significativa|Não separáveis|  
  
## <a name="cause"></a>Causa  
 Uma implementação do método contém os caminhos de código que poderiam causar várias chamadas para <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> ou um equivalente de Dispose, como um método Close () em alguns tipos, no mesmo objeto.  
  
## <a name="rule-description"></a>Descrição da Regra  
 Um implementado corretamente <xref:System.IDisposable.Dispose%2A> método pode ser chamado várias vezes sem lançar uma exceção. No entanto, isso não é garantido e para evitar a geração de um <xref:System.ObjectDisposedException?displayProperty=fullName> você não deve chamar <xref:System.IDisposable.Dispose%2A> mais de uma vez em um objeto.  
  
## <a name="related-rules"></a>Regras relacionadas  
 [CA2000: descartar objetos antes de perder o escopo](../code-quality/ca2000-dispose-objects-before-losing-scope.md)  
  
## <a name="how-to-fix-violations"></a>Como Corrigir Violações  
 Para corrigir uma violação desta regra, altere a implementação assim que independentemente do caminho de código de <xref:System.IDisposable.Dispose%2A> é chamado apenas uma vez para o objeto.  
  
## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos  
 Não suprima um aviso nessa regra. Mesmo se <xref:System.IDisposable.Dispose%2A> para o objeto é conhecido para ser segura pode ser chamado várias vezes, a implementação pode ser alterado no futuro.  
  
## <a name="example"></a>Exemplo  
 Aninhados `using` instruções (`Using` no Visual Basic) pode causar violações do aviso CA2202. Se o recurso de IDisposable de aninhados interna `using` declaração contém o recurso de externa `using` instrução, o `Dispose` método do recurso aninhado libera os recursos contidos. Quando essa situação ocorrer, o `Dispose` método externo `using` declaração tenta descartar seu recurso pela segunda vez.  
  
 No exemplo a seguir, uma <xref:System.IO.Stream> objeto que é criado em um externa usando a instrução é liberado no final da interna usando a instrução no método Dispose do <xref:System.IO.StreamWriter> objeto que contém o `stream` objeto. No final da externa `using` instrução, o `stream` objeto é liberado uma segunda vez. A segunda versão é uma violação de CA2202.  
  
```  
using (Stream stream = new FileStream("file.txt", FileMode.OpenOrCreate))  
{  
    using (StreamWriter writer = new StreamWriter(stream))  
    {  
        // Use the writer object...  
    }  
}  
  
```  
  
## <a name="example"></a>Exemplo  
 Para resolver esse problema, use um `try` / `finally` blocos em vez de externa `using` instrução. No `finally` bloquear, certifique-se de que o `stream` recurso não é nulo.  
  
```  
Stream stream = null;  
try  
{  
    stream = new FileStream("file.txt", FileMode.OpenOrCreate);  
    using (StreamWriter writer = new StreamWriter(stream))  
    {  
        stream = null;  
        // Use the writer object...  
    }  
}  
finally  
{  
    if(stream != null)  
        stream.Dispose();  
}  
  
```  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.IDisposable?displayProperty=fullName>   
 [Padrão de Dispose](/dotnet/standard/design-guidelines/dispose-pattern)