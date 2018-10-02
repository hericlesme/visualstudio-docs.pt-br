---
title: 'CA2207: Inicializar campos estáticos de tipo de valor embutido | Microsoft Docs'
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
- InitializeValueTypeStaticFieldsInline
- CA2207
helpviewer_keywords:
- CA2207
- InitializeValueTypeStaticFieldsInline
ms.assetid: d1ea9d8b-ecc2-46ca-86e2-c41dd0e76658
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 0f90e52ed5d80c9b3e97415e920d7d6f4f0972fc
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/24/2018
ms.locfileid: "47587125"
---
# <a name="ca2207-initialize-value-type-static-fields-inline"></a>CA2207: inicializar campos estáticos de tipo de valor embutido
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [CA2207: inicializar campos estáticos de tipo de valor embutido](https://docs.microsoft.com/visualstudio/code-quality/ca2207-initialize-value-type-static-fields-inline).

|||
|-|-|
|NomeDoTipo|InitializeValueTypeStaticFieldsInline|
|CheckId|CA2207|
|Categoria|Microsoft.Usage|
|Alteração Significativa|Não separável|

## <a name="cause"></a>Causa
 Um tipo de valor declara um construtor estático explícito.

## <a name="rule-description"></a>Descrição da Regra
 Quando um tipo de valor é declarado, ele passa por uma inicialização padrão em que todos os campos de tipo de valor são definidos como zero e todos os campos de tipo de referência são definidos como `null` (`Nothing` no Visual Basic). Um construtor estático explícito é garantido somente para executar antes de um construtor de instância ou um membro estático do tipo é chamado. Portanto, se o tipo é criado sem chamar um construtor de instância, o construtor estático não é garantido para ser executado.

 Se todos os dados estáticos é inicializado embutido e nenhum construtor estático explícito é declarado, os compiladores c# e Visual Basic, adicione o `beforefieldinit` sinalizador à definição de classe MSIL. Os compiladores também adicionar um construtor estático privado que contém o código de inicialização estática. Este construtor estático privado é garantido para ser executado antes de qualquer campo estático do tipo é acessado.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir uma violação dessa regra inicializar todos os dados estáticos quando ele é declarado e remova o construtor estático.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 Não suprima um aviso nessa regra.

## <a name="related-rules"></a>Regras relacionadas
 [CA1810: inicializar campos estáticos de tipo de referência embutido](../code-quality/ca1810-initialize-reference-type-static-fields-inline.md)



