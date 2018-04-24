---
title: 'CA2124: encapsular cláusulas finalmente vulneráveis em tentativa externa'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2124
- WrapVulnerableFinallyClausesInOuterTry
helpviewer_keywords:
- CA2124
- WrapVulnerableFinallyClausesInOuterTry
ms.assetid: 82efd224-9e60-4b88-a0f5-dfabcc49a254
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d46bc7bcfa8c1918091fabbbd759172259ea9ba6
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/19/2018
---
# <a name="ca2124-wrap-vulnerable-finally-clauses-in-outer-try"></a>CA2124: encapsular cláusulas finalmente vulneráveis em tentativa externa
|||
|-|-|
|NomeDoTipo|WrapVulnerableFinallyClausesInOuterTry|
|CheckId|CA2124|
|Categoria|Microsoft.Security|
|Alteração Significativa|Não separáveis|

## <a name="cause"></a>Causa
 Nas versões 1.0 e 1.1 do [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], um método público ou protegido contém um `try` / `catch` / `finally` bloco. O `finally` bloco é exibido redefinir o estado de segurança e não está contido em um `finally` bloco.

## <a name="rule-description"></a>Descrição da Regra
 Essa regra localiza `try` / `finally` blocos no código que tem como alvo versões 1.0 e 1.1 do [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] que podem estar vulneráveis a filtros de exceção mal-intencionado presentes na pilha de chamadas. Se operações confidenciais como representação ocorrerem no bloco try, e uma exceção será lançada, o filtro pode ser executado antes do `finally` bloco. Para o exemplo de representação, isso significa que o filtro será executado como o usuário representado. Os filtros são implementável atualmente apenas no Visual Basic.

> [!WARNING]
>  **Observação** nas versões 2.0 e posteriores do [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], o tempo de execução protege automaticamente um `try` / `catch` /  `finally` bloco de filtros de exceção mal-intencionados, se a reinicialização ocorre diretamente dentro do método que contém o bloco de exceção.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Coloque o desencapsulamento `try` / `finally` em um bloco try externo. Consulte o segundo exemplo que segue. Isso força o `finally` seja executado antes do código de filtro.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 Não suprima um aviso nessa regra.

## <a name="pseudo-code-example"></a>Exemplo de código pseudo

### <a name="description"></a>Descrição
 O pseudocódigo a seguir ilustra o padrão detectado por essa regra.

### <a name="code"></a>Código

```
try {
   // Do some work.
   Impersonator imp = new Impersonator("John Doe");
   imp.AddToCreditCardBalance(100);
}
finally {
   // Reset security state.
   imp.Revert();
}
```

## <a name="example"></a>Exemplo
 O pseudocódigo a seguir mostra o padrão que você pode usar para proteger seu código e atender a essa regra.

```
try {
     try {
        // Do some work.
     }
     finally {
        // Reset security state.
     }
}
catch()
{
    throw;
}
```