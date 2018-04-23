---
title: 'CA1713: os eventos não devem ter um prefixo anterior ou posterior'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- EventsShouldNotHaveBeforeOrAfterPrefix
- CA1713
helpviewer_keywords:
- CA1713
- EventsShouldNotHaveBeforeOrAfterPrefix
ms.assetid: 855772a4-aa9e-410b-88c1-c5fba1ca63da
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f575cf00756c730133d91ed56f73bf923cd5ab76
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/19/2018
---
# <a name="ca1713-events-should-not-have-before-or-after-prefix"></a>CA1713: os eventos não devem ter um prefixo anterior ou posterior
|||
|-|-|
|NomeDoTipo|EventsShouldNotHaveBeforeOrAfterPrefix|
|CheckId|CA1713|
|Categoria|Microsoft.Naming|
|Alteração Significativa|Quebra|

## <a name="cause"></a>Causa
 O nome de um evento começa com 'Before' ou 'After'.

## <a name="rule-description"></a>Descrição da Regra
 Nomes de evento devem descrever a ação que gera o evento. Para nomear eventos relacionados acionados em uma sequência específica, use o presente ou o pretérito para indicar a posição relativa na sequência de ações. Por exemplo, quando um par de eventos de nomenclatura que é gerado quando um recurso de fechamento, você pode nomeá-lo 'De fechamento' e 'Fechado', em vez de 'BeforeClose' e 'AfterClose'.

 Convenções de nomenclatura fornecem uma aparência comum para bibliotecas de destino do common language runtime. Isso reduz a curva de aprendizado que é necessário para novas bibliotecas de software e aumenta a confiança do cliente que a biblioteca foi desenvolvida por uma pessoa com experiência em desenvolvimento de código gerenciado.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Remova o prefixo do nome do evento e considere alterar o nome para usar o presente ou no passado de um verbo.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 Não suprima um aviso nessa regra.