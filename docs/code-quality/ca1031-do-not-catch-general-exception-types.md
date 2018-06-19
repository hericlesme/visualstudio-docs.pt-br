---
title: 'CA1031: não capturar tipos de exceção gerais'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1031
- DoNotCatchGeneralExceptionTypes
helpviewer_keywords:
- CA1031
- DoNotCatchGeneralExceptionTypes
ms.assetid: cbc283ae-2a46-4ec0-940e-85aa189b118f
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9cbc03edf93c6b4977fe62d72a4df0d60dff035d
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31900374"
---
# <a name="ca1031-do-not-catch-general-exception-types"></a>CA1031: não capturar tipos de exceção gerais
|||
|-|-|
|NomeDoTipo|DoNotCatchGeneralExceptionTypes|
|CheckId|CA1031|
|Categoria|Microsoft.Design|
|Alteração Significativa|Não recentes|

## <a name="cause"></a>Causa
 Uma exceção geral como <xref:System.Exception?displayProperty=fullName> ou <xref:System.SystemException?displayProperty=fullName> é detectado em um `catch` instrução ou uma cláusula catch geral como `catch()` é usado.

## <a name="rule-description"></a>Descrição da Regra
 As exceções gerais não devem ser capturadas.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir uma violação desta regra, capturar uma exceção mais específica ou relançar a exceção geral como a última instrução no `catch` bloco.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 Não suprima um aviso nessa regra. Captura de tipos de exceção geral pode ocultar problemas de tempo de execução do usuário de biblioteca e pode tornar a depuração mais difícil.

> [!NOTE]
>  Começando com o [!INCLUDE[net_v40_long](../code-quality/includes/net_v40_long_md.md)], o common language runtime (CLR) não oferece exceções de estado corrompido que ocorrem no sistema operacional e código gerenciado, como violações de acesso em [!INCLUDE[TLA#tla_mswin](../code-quality/includes/tlasharptla_mswin_md.md)], para ser tratada pelo código gerenciado. Se você deseja compilar um aplicativo no [!INCLUDE[net_v40_short](../code-quality/includes/net_v40_short_md.md)] ou versões posteriores e manter o tratamento de exceções de estado corrompido, você pode aplicar o <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute> de atributo para o método que manipula a exceção de estado corrompido.

## <a name="example"></a>Exemplo
 O exemplo a seguir mostra um tipo que violam essa regra e um tipo que implementa corretamente o `catch` bloco.

 [!code-cpp[FxCop.Design.ExceptionAndSystemException#1](../code-quality/codesnippet/CPP/ca1031-do-not-catch-general-exception-types_1.cpp)]
 [!code-vb[FxCop.Design.ExceptionAndSystemException#1](../code-quality/codesnippet/VisualBasic/ca1031-do-not-catch-general-exception-types_1.vb)]
 [!code-csharp[FxCop.Design.ExceptionAndSystemException#1](../code-quality/codesnippet/CSharp/ca1031-do-not-catch-general-exception-types_1.cs)]

## <a name="related-rules"></a>Regras relacionadas
 [CA2200: relançar para preservar detalhes da pilha](../code-quality/ca2200-rethrow-to-preserve-stack-details.md)