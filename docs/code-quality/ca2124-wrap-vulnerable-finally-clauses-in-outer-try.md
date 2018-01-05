---
title: "CA2124: Wrap vulnerável finalmente cláusulas externa tente | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA2124
- WrapVulnerableFinallyClausesInOuterTry
helpviewer_keywords:
- CA2124
- WrapVulnerableFinallyClausesInOuterTry
ms.assetid: 82efd224-9e60-4b88-a0f5-dfabcc49a254
caps.latest.revision: "20"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 567c519b09042dbd0bba447d4631544dd78ca1ad
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
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