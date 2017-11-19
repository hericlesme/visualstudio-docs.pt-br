---
title: 'CA2205: Usar gerenciada equivalentes da API do Win32 | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- UseManagedEquivalentsOfWin32Api
- CA2205
helpviewer_keywords:
- UseManagedEquivalentsOfWin32Api
- CA2205
ms.assetid: 1c65ab59-3e50-4488-a727-3969c7f6cbe4
caps.latest.revision: "13"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: cbdc02843d0a2982a129dafd5948a4c1ab287427
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="ca2205-use-managed-equivalents-of-win32-api"></a>CA2205: usar equivalentes gerenciados da API do Win32
|||  
|-|-|  
|NomeDoTipo|UseManagedEquivalentsOfWin32Api|  
|CheckId|CA2205|  
|Categoria|Microsoft.Usage|  
|Alteração Significativa|Não separáveis|  
  
## <a name="cause"></a>Causa  
 Invocação de uma plataforma método está definido e um método com a funcionalidade equivalente existe o [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] biblioteca de classe.  
  
## <a name="rule-description"></a>Descrição da Regra  
 Uma plataforma de invocação de método é usado para chamar uma função DLL não gerenciada e é definido usando o <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName> atributo, ou o `Declare` palavra-chave no Visual Basic. Método de invocação de uma plataforma definida incorretamente pode resultar em exceções de tempo de execução devido a problemas como uma função equivocado, com defeito de mapeamento de parâmetro e retornar tipos de dados de valor e especificações de campo incorreto, como a convenção de chamada e o caractere conjunto. Se estiver disponível, geralmente é mais simples e menos propenso a erros chamar o método gerenciado equivalente que to definir e chame o método gerenciado diretamente. Chamando uma plataforma de invocar o método também pode levar a problemas de segurança adicional que precisam ser atendidas.  
  
## <a name="how-to-fix-violations"></a>Como Corrigir Violações  
 Para corrigir uma violação desta regra, substitua a chamada para a função não gerenciada por uma chamada para seu equivalente gerenciado.  
  
## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos  
 Suprima um aviso de que essa regra se o método de substituição sugerido não fornecer a funcionalidade necessária.  
  
## <a name="example"></a>Exemplo  
 A exemplo a seguir mostra uma plataforma de invocar a definição de método que viola a regra. Além disso, as chamadas para a plataforma de invocação de método e o método gerenciado equivalente são mostrados.  
  
 [!code-csharp[FxCop.Usage.ManagedEquivalents#1](../code-quality/codesnippet/CSharp/ca2205-use-managed-equivalents-of-win32-api_1.cs)]
 [!code-vb[FxCop.Usage.ManagedEquivalents#1](../code-quality/codesnippet/VisualBasic/ca2205-use-managed-equivalents-of-win32-api_1.vb)]  
  
## <a name="related-rules"></a>Regras relacionadas  
 [CA1404: Chamar GetLastError logo depois de P/Invoke](../code-quality/ca1404-call-getlasterror-immediately-after-p-invoke.md)  
  
 [CA1060: Mover P/Invokes para a classe NativeMethods](../code-quality/ca1060-move-p-invokes-to-nativemethods-class.md)  
  
 [CA1400: Os pontos de entrada P/Invoke devem existir](../code-quality/ca1400-p-invoke-entry-points-should-exist.md)  
  
 [CA1401: P/Invokes não devem ser visíveis](../code-quality/ca1401-p-invokes-should-not-be-visible.md)  
  
 [CA2101: Especificar marshaling para argumentos de cadeia de caracteres P/Invoke](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)