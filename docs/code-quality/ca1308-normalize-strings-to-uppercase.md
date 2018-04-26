---
title: 'CA1308: normalizar cadeias de caracteres para maiúsculas'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1308
- NormalizeStringsToUppercase
helpviewer_keywords:
- NormalizeStringsToUppercase
- CA1308
ms.assetid: 7e9a7457-3f93-4938-ac6f-1389fba8d9cc
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a5cda66d2a43ee3fde8e3e7b2d22a64a09655da3
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="ca1308-normalize-strings-to-uppercase"></a>CA1308: normalizar cadeias de caracteres para maiúsculas
|||
|-|-|
|NomeDoTipo|NormalizeStringsToUppercase|
|CheckId|CA1308|
|Categoria|Microsoft.Globalization|
|Alteração Significativa|Não recentes|

## <a name="cause"></a>Causa
 Uma operação normaliza uma cadeia de caracteres em minúsculas.

## <a name="rule-description"></a>Descrição da Regra
 As cadeias de caracteres devem ser normalizadas em maiúsculas. Um pequeno grupo de caracteres, quando eles são convertidos em minúsculas, não é possível fazer uma viagem de ida e. Para fazer uma viagem de ida e meios para converter os caracteres de uma localidade para outra localidade que representa dados de caracteres de forma diferente e, em seguida, com precisão recuperar os caracteres originais dos caracteres convertidos.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Altere as operações que converter cadeias de caracteres em minúsculas, para que as cadeias de caracteres são convertidas em letras maiusculas em vez disso. Por exemplo, altere `String.ToLower(CultureInfo.InvariantCulture)` para `String.ToUpper(CultureInfo.InvariantCulture)`.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 É seguro suprimir uma mensagem de aviso quando você não estiver fazendo a decisão de segurança com base no resultado (por exemplo, quando você estiver exibindo-la na interface de usuário).

## <a name="see-also"></a>Consulte também
 [Avisos de globalização](../code-quality/globalization-warnings.md)