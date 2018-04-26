---
title: 'CA1900: os campos de tipo de valor devem ser móveis'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1900
- ValueTypeFieldsShouldBePortable
helpviewer_keywords:
- ValueTypeFieldsShouldBePortable
- CA1900
ms.assetid: 1787d371-389f-4d39-b305-12b53bc0dfb9
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9add21d932f7685a2dee214f396b2cbda089a5a5
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="ca1900-value-type-fields-should-be-portable"></a>CA1900: os campos de tipo de valor devem ser móveis
|||
|-|-|
|NomeDoTipo|ValueTypeFieldsShouldBePortable|
|CheckId|CA1900|
|Categoria|Microsoft.Portability|
|Alteração Significativa|Quebrar - se o campo pode ser visto fora do assembly.<br /><br /> Não quebra - se o campo não é visível fora do assembly.|

## <a name="cause"></a>Causa
 Esta regra verifica se estruturas que são declaradas com layout explícito serão alinhado corretamente quando passa por marshaling para código não gerenciado em sistemas operacionais de 64 bits. IA-64 não permite memória não acessa e o processo falhará se essa violação não for corrigida.

## <a name="rule-description"></a>Descrição da Regra
 Estruturas com layout explícito contendo campos desalinhados podem causar quedas em sistemas operacionais de 64 bits.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Todos os campos que são menores do que 8 bytes devem ter os deslocamentos são um múltiplo de seu tamanho e campos de 8 bytes ou mais devem ter os deslocamentos são um múltiplo de 8. Outra solução é usar `LayoutKind.Sequential` em vez de `LayoutKind.Explicit`, se razoável.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 Esse aviso deve ser suprimido somente se ele ocorrer no erro.