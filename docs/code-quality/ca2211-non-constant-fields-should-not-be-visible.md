---
title: 'CA2211: os campos não constantes não devem estar visíveis'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2211
- NonConstantFieldsShouldNotBeVisible
helpviewer_keywords:
- NonConstantFieldsShouldNotBeVisible
- CA2211
ms.assetid: e1e42c40-0acd-4312-af29-70133739a304
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2b3c508aaf8632ff7fc064fabb4367044e079fa8
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31921173"
---
# <a name="ca2211-non-constant-fields-should-not-be-visible"></a>CA2211: os campos não constantes não devem estar visíveis
|||
|-|-|
|NomeDoTipo|NonConstantFieldsShouldNotBeVisible|
|CheckId|CA2211|
|Categoria|Microsoft.Usage|
|Alteração Significativa|Quebra|

## <a name="cause"></a>Causa
 Não é um campo estático público ou protegido constante nem é somente leitura.

## <a name="rule-description"></a>Descrição da Regra
 Os campos estáticos que não são constantes nem somente leitura não são thread-safe. Acesso a esse campo deve ser cuidadosamente controlado e requer técnicas de programação avançadas para sincronizar o acesso ao objeto de classe. Porque são habilidades difícil de aprender e mestre e teste desse objeto apresenta seus próprios desafios, campos estáticos são melhor usados para armazenar dados que não é alterado. Essa regra se aplica a bibliotecas; aplicativos não devem expor os campos.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir uma violação desta regra, verifique o campo estático constante ou somente leitura. Se isso não for possível, recrie o tipo para usar um mecanismo alternativo, como uma propriedade de thread-safe que gerencia o acesso thread-safe ao campo subjacente. Observe que os problemas, como contenção de bloqueio e deadlocks podem afetar o desempenho e o comportamento da biblioteca.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 É seguro suprimir um aviso dessa regra, se você estiver desenvolvendo um aplicativo e, portanto, ter controle total sobre o acesso para o tipo que contém o campo estático. Designers de biblioteca não devem suprimir um aviso dessa regra; campos estáticos de constante não pode fazer usando a biblioteca de difícil para os desenvolvedores a usar corretamente.

## <a name="example"></a>Exemplo
 O exemplo a seguir mostra um tipo que violam essa regra.

 [!code-vb[FxCop.Usage.AvoidStaticNonConstants#1](../code-quality/codesnippet/VisualBasic/ca2211-non-constant-fields-should-not-be-visible_1.vb)]
 [!code-csharp[FxCop.Usage.AvoidStaticNonConstants#1](../code-quality/codesnippet/CSharp/ca2211-non-constant-fields-should-not-be-visible_1.cs)]