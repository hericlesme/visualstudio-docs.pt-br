---
title: 'CA2139: Os métodos transparentes talvez não usem o atributo HandleProcessCorruptingExceptions | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA2139
ms.assetid: 45a0328a-add7-40f9-8934-dff59beb02b3
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 0922665ebbabb5456e58ecfe0442c5ad3d37a6d7
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/24/2018
ms.locfileid: "47587122"
---
# <a name="ca2139-transparent-methods-may-not-use-the-handleprocesscorruptingexceptions-attribute"></a>CA2139: os métodos transparentes talvez não usem o atributo HandleProcessCorruptingExceptions
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [CA2139: métodos transparentes talvez não usem o atributo HandleProcessCorruptingExceptions](https://docs.microsoft.com/visualstudio/code-quality/ca2139-transparent-methods-may-not-use-the-handleprocesscorruptingexceptions-attribute).

|||
|-|-|
|NomeDoTipo|TransparentMethodsMustNotHandleProcessCorruptingExceptions|
|CheckId|CA2139|
|Categoria|Microsoft.Security|
|Alteração Significativa|Quebra|

## <a name="cause"></a>Causa
 Um método transparente é marcado com o <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute> atributo.

## <a name="rule-description"></a>Descrição da Regra
 Essa regra é acionada em qualquer método que é transparente e tenta tratar uma exceção de corrompimento por meio de processo a <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute> atributo. Uma exceção de corrompimento de processo é uma classificação de exceção do CLR versão 4.0 de exceções tais <xref:System.AccessViolationException>. O atributo HandleProcessCorruptedStateExceptionsAttribute só pode ser usado por métodos de segurança crítica e será ignorado se for aplicado a um método transparente. Para lidar com exceções corrompam de processos, esse método deve se tornar seguro-crítica de segurança ou crítico para segurança.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir uma violação dessa regra, remova os <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute> de atributo, ou marcar o método com o <xref:System.Security.SecurityCriticalAttribute> ou o <xref:System.Security.SecuritySafeCriticalAttribute> atributo.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 Não suprima um aviso nessa regra.

## <a name="example"></a>Exemplo
 Neste exemplo, um método transparente é marcado com o <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute> de atributo e haverá falha na regra. O método também deve ser marcado com o <xref:System.Security.SecurityCriticalAttribute> ou o <xref:System.Security.SecuritySafeCriticalAttribute> atributo.

 [!code-csharp[FxCop.Security.CA2139.TransparentMethodsMustNotHandleProcessCorruptingExceptions#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2139.transparentmethodsmustnothandleprocesscorruptingexceptions/cs/ca2139 - transparentmethodsmustnothandleprocesscorruptingexceptions.cs#1)]



