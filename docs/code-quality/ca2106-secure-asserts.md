---
title: 'CA2106: declarações seguras'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2106
- SecureAsserts
helpviewer_keywords:
- CA2106
- SecureAsserts
ms.assetid: 91feb36e-6e2c-436c-8272-5aee31f77e98
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 40d497efd766fa5716b92e16ad513df85a41d2cf
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/19/2018
---
# <a name="ca2106-secure-asserts"></a>CA2106: declarações seguras
|||
|-|-|
|NomeDoTipo|SecureAsserts|
|CheckId|CA2106|
|Categoria|Microsoft.Security|
|Alteração Significativa|Quebra|

## <a name="cause"></a>Causa
 Um método declara uma permissão e nenhuma verificação de segurança é realizada no chamador.

## <a name="rule-description"></a>Descrição da Regra
 A declaração de uma permissão de segurança sem realizar verificações de segurança pode deixar uma fraqueza de segurança explorável no código. Um exame da pilha de segurança para quando uma permissão de segurança é declarada. Se você declarar uma permissão sem realizar verificações no chamador, o chamador indiretamente pode executar códigos usando suas permissões. Declara sem verificações de segurança são permitidos apenas quando tiver certeza de que a declaração não pode ser usada de maneira prejudicial. Uma declaração é inofensiva se o código que você chamar é inofensivo, ou os usuários não é possível passar informações arbitrárias ao código que você chama.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir uma violação desta regra, adicione uma exigência de segurança para o método ou seu tipo declarativo.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 Suprima um aviso dessa regra somente após uma análise cuidadosa de segurança.

## <a name="see-also"></a>Consulte também
 <xref:System.Security.CodeAccessPermission.Assert%2A?displayProperty=fullName> [Diretrizes de codificação segura](/dotnet/standard/security/secure-coding-guidelines)