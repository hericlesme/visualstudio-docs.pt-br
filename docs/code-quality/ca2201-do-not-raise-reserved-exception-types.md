---
title: 'CA2201: não acionar tipos de exceção reservados'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotRaiseReservedExceptionTypes
- CA2201
helpviewer_keywords:
- CA2201
- DoNotRaiseReservedExceptionTypes
ms.assetid: dd14ef5c-80e6-41a5-834e-eba8e2eae75e
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 696eed674dd2b85ec048290ba88084751230635d
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31924031"
---
# <a name="ca2201-do-not-raise-reserved-exception-types"></a>CA2201: não acionar tipos de exceção reservados
|||
|-|-|
|NomeDoTipo|DoNotRaiseReservedExceptionTypes|
|CheckId|CA2201|
|Categoria|Microsoft.Usage|
|Alteração Significativa|Quebra|

## <a name="cause"></a>Causa
 Um método gera um tipo de exceção que é muito geral ou que está reservado pelo tempo de execução.

## <a name="rule-description"></a>Descrição da Regra
 Os seguintes tipos de exceção são gerais demais para fornecer informações suficientes para o usuário:

-   <xref:System.Exception?displayProperty=fullName>

-   <xref:System.ApplicationException?displayProperty=fullName>

-   <xref:System.SystemException?displayProperty=fullName>

 Os seguintes tipos de exceção são reservados e deverá ser lançados apenas pelo common language runtime:

-   <xref:System.ExecutionEngineException?displayProperty=fullName>

-   <xref:System.IndexOutOfRangeException?displayProperty=fullName>

-   <xref:System.NullReferenceException?displayProperty=fullName>

-   <xref:System.OutOfMemoryException?displayProperty=fullName>

 **Não emitem exceções gerais**

 Se você gera um tipo de exceção geral, como <xref:System.Exception> ou <xref:System.SystemException> em uma biblioteca ou estrutura, ele força os consumidores a capturar todas as exceções, incluindo exceções desconhecidas que não sabem como manipular.

 Em vez disso, ou gerar um tipo mais derivado que já existe no framework ou criar seu próprio tipo que deriva de <xref:System.Exception>.

 **Lançar exceções específicas**

 A tabela a seguir mostra os parâmetros e as exceções para lançar ao validar o parâmetro, incluindo o parâmetro de valor no acessador set de uma propriedade:

|Descrição do parâmetro|Exceção|
|---------------------------|---------------|
|`null` Referência|<xref:System.ArgumentNullException?displayProperty=fullName>|
|Fora do intervalo permitido de valores (como um índice para uma coleção ou lista)|<xref:System.ArgumentOutOfRangeException?displayProperty=fullName>|
|Inválido `enum` valor|<xref:System.ComponentModel.InvalidEnumArgumentException?displayProperty=fullName>|
|Contém um formato que não atende às especificações de parâmetro de um método (como a cadeia de caracteres de formato para `ToString(String)`)|<xref:System.FormatException?displayProperty=fullName>|
|Caso contrário inválido|<xref:System.ArgumentException?displayProperty=fullName>|

 Quando uma operação é inválida para o estado atual de um objeto throw <xref:System.InvalidOperationException?displayProperty=fullName>

 Quando uma operação é executada em um objeto que foi descartado throw <xref:System.ObjectDisposedException?displayProperty=fullName>

 Quando uma operação não tem suporte (como uma substituição **Stream.Write** em um fluxo aberto para leitura) throw <xref:System.NotSupportedException?displayProperty=fullName>

 Quando uma conversão pode resultar em um estouro (como em uma sobrecarga de operador de conversão explícita) gerar <xref:System.OverflowException?displayProperty=fullName>

 Em outras situações, considere a criação de seu próprio tipo que deriva de <xref:System.Exception> e lançar que.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir uma violação desta regra, altere o tipo de exceção lançada para um tipo específico que não é um dos tipos de reservado.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 Não suprima um aviso nessa regra.

## <a name="related-rules"></a>Regras relacionadas
 [CA1031: não capturar tipos de exceção gerais](../code-quality/ca1031-do-not-catch-general-exception-types.md)