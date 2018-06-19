---
title: 'CA2139: os métodos transparentes talvez não usem o atributo HandleProcessCorruptingExceptions'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2139
ms.assetid: 45a0328a-add7-40f9-8934-dff59beb02b3
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 90c6178ce944edd2ffd46d9fa0095484a89a828a
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31918877"
---
# <a name="ca2139-transparent-methods-may-not-use-the-handleprocesscorruptingexceptions-attribute"></a>CA2139: os métodos transparentes talvez não usem o atributo HandleProcessCorruptingExceptions
|||
|-|-|
|NomeDoTipo|TransparentMethodsMustNotHandleProcessCorruptingExceptions|
|CheckId|CA2139|
|Categoria|Microsoft.Security|
|Alteração Significativa|Quebra|

## <a name="cause"></a>Causa
 Um método transparente está marcado com o <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute> atributo.

## <a name="rule-description"></a>Descrição da Regra
 Esta regra é disparada qualquer método que é transparente e tentativas de lidar com um processo corrompendo exceção usando o <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute> atributo. Um processo de corrupção de exceção é uma classificação de exceção do CLR versão 4.0 de tais exceções <xref:System.AccessViolationException>. O atributo HandleProcessCorruptedStateExceptionsAttribute só pode ser usado por métodos de segurança crítica e será ignorado se for aplicado a um método transparente. Para lidar com exceções de corrupção do processo, este método deve se tornar crítico de segurança ou segurança crítico para segurança.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir uma violação desta regra, remova o <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute> de atributo, ou marcar o método com o <xref:System.Security.SecurityCriticalAttribute> ou <xref:System.Security.SecuritySafeCriticalAttribute> atributo.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 Não suprima um aviso nessa regra.

## <a name="example"></a>Exemplo
 Neste exemplo, um método transparente está marcado com o <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute> de atributo e haverá falha na regra. O método também deve ser marcado com o <xref:System.Security.SecurityCriticalAttribute> ou <xref:System.Security.SecuritySafeCriticalAttribute> atributo.

 [!code-csharp[FxCop.Security.CA2139.TransparentMethodsMustNotHandleProcessCorruptingExceptions#1](../code-quality/codesnippet/CSharp/ca2139-transparent-methods-may-not-use-the-handleprocesscorruptingexceptions-attribute_1.cs)]