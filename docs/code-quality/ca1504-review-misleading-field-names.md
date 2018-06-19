---
title: 'CA1504: revisar nomes de campo confusos'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- ReviewMisleadingFieldNames
- CA1504
helpviewer_keywords:
- CA1504
- ReviewMisleadingFieldNames
ms.assetid: 94136ff1-4aaf-4dc2-9170-48c171ab7499
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1457390b523af45b5e3b23a3420cba830f45cee5
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31915076"
---
# <a name="ca1504-review-misleading-field-names"></a>CA1504: revisar nomes de campo confusos
|||
|-|-|
|NomeDoTipo|ReviewMisleadingFieldNames|
|CheckId|CA1504|
|Categoria|Microsoft.Maintainability|
|Alteração Significativa|Não recentes|

## <a name="cause"></a>Causa
 O nome de um campo de instância começa com "s _" ou o nome de um `static` (`Shared` em [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) campo começa com "m _".

## <a name="rule-description"></a>Descrição da Regra
 Nomes de campo que começam com "s _" são associados a dados estáticos por muitos usuários. Da mesma forma, os nomes de campo que começam com "m _" são associados aos dados de instância (membro). Para código mais fácil manutenção, nomes deverá seguir as convenções geralmente usadas.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir uma violação desta regra, renomeie o campo usando o prefixo apropriado. Como alternativa, verifique o campo concordar com o sufixo atual, adicionando ou removendo o `static` modificador.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 Não suprima um aviso nessa regra.