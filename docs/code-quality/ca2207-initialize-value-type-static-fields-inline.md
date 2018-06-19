---
title: 'CA2207: inicializar campos estáticos de tipo de valor embutido'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- InitializeValueTypeStaticFieldsInline
- CA2207
helpviewer_keywords:
- CA2207
- InitializeValueTypeStaticFieldsInline
ms.assetid: d1ea9d8b-ecc2-46ca-86e2-c41dd0e76658
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 883e5d842346a0821b54b2b4eacad3cbc92028b6
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31917680"
---
# <a name="ca2207-initialize-value-type-static-fields-inline"></a>CA2207: inicializar campos estáticos de tipo de valor embutido
|||
|-|-|
|NomeDoTipo|InitializeValueTypeStaticFieldsInline|
|CheckId|CA2207|
|Categoria|Microsoft.Usage|
|Alteração Significativa|Não separáveis|

## <a name="cause"></a>Causa
 Um tipo de valor declara um construtor estático explícito.

## <a name="rule-description"></a>Descrição da Regra
 Quando um tipo de valor é declarado, passa por uma inicialização padrão, onde todos os campos de tipo de valor são definidos como zero e todos os campos de tipo de referência são definidos como `null` (`Nothing` no Visual Basic). Um construtor estático explícito só é garantido para ser executado antes de um construtor de instância ou um membro estático do tipo é chamado. Portanto, se o tipo é criado sem chamar um construtor de instância, o construtor estático não é garantido para ser executado.

 Se todos os dados estáticos são inicializado embutido e nenhum construtor estático explícito é declarado, os compiladores c# e Visual Basic, adicione o `beforefieldinit` sinalizador à definição de classe MSIL. Os compiladores também adicionar um construtor estático particular que contém o código de inicialização estática. Este construtor estático privado é garantido para ser executado antes de qualquer campo estático do tipo é acessado.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir uma violação desta regra inicializar todos os dados estáticos quando ele é declarado e remover o construtor estático.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 Não suprima um aviso nessa regra.

## <a name="related-rules"></a>Regras relacionadas
 [CA1810: inicializar campos estáticos de tipo de referência embutido](../code-quality/ca1810-initialize-reference-type-static-fields-inline.md)