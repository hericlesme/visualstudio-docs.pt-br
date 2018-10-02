---
title: 'CA1308: Normalizar cadeias de caracteres em maiusculas | Microsoft Docs'
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
- CA1308
- NormalizeStringsToUppercase
helpviewer_keywords:
- NormalizeStringsToUppercase
- CA1308
ms.assetid: 7e9a7457-3f93-4938-ac6f-1389fba8d9cc
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 8f5a40d412b8ea9616dd75d7e0424ba447b5a185
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/24/2018
ms.locfileid: "47476443"
---
# <a name="ca1308-normalize-strings-to-uppercase"></a>CA1308: normalizar cadeias de caracteres para maiúsculas
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [CA1308: normalizar cadeias de caracteres em maiusculas](https://docs.microsoft.com/visualstudio/code-quality/ca1308-normalize-strings-to-uppercase).

|||
|-|-|
|NomeDoTipo|NormalizeStringsToUppercase|
|CheckId|CA1308|
|Categoria|Microsoft.Globalization|
|Alteração Significativa|Não são significativas|

## <a name="cause"></a>Causa
 Uma operação normaliza uma cadeia de caracteres em minúsculas.

## <a name="rule-description"></a>Descrição da Regra
 As cadeias de caracteres devem ser normalizadas em maiúsculas. Um pequeno grupo de caracteres, quando eles são convertidos em minúsculas, não é possível fazer uma viagem de ida e volta. Para fazer uma viagem de ida e volta o meio para converter os caracteres de uma localidade para outra localidade que representa dados de caracteres de forma diferente e, em seguida, com precisão recuperar os caracteres originais dos caracteres convertidos.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Altere as operações que convertem cadeias de caracteres em minúsculas, para que as cadeias de caracteres são convertidas em letras maiusculas em vez disso. Por exemplo, altere `String.ToLower(CultureInfo.InvariantCulture)` para `String.ToUpper(CultureInfo.InvariantCulture)`.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 É seguro suprimir uma mensagem de aviso quando você não estiver fazendo a decisão de segurança com base no resultado (por exemplo, quando você exibe na interface do usuário).

## <a name="see-also"></a>Consulte também
 [Avisos de globalização](../code-quality/globalization-warnings.md)



