---
title: "CA2201: Não gerar tipos de exceção reservados | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- DoNotRaiseReservedExceptionTypes
- CA2201
helpviewer_keywords:
- CA2201
- DoNotRaiseReservedExceptionTypes
ms.assetid: dd14ef5c-80e6-41a5-834e-eba8e2eae75e
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 11e00594c1cf279fb6b07791bb48f2222cc9c79b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
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
|`null`referência|<xref:System.ArgumentNullException?displayProperty=fullName>|  
|Fora do intervalo permitido de valores (como um índice para uma coleção ou lista)|<xref:System.ArgumentOutOfRangeException?displayProperty=fullName>|  
|Inválido `enum` valor|<xref:System.ComponentModel.InvalidEnumArgumentException?displayProperty=fullName>|  
|Contém um formato que não atende às especificações de parâmetro de um método (como a cadeia de caracteres de formato para `ToString(String)`)|<xref:System.FormatException?displayProperty=fullName>|  
|Caso contrário inválido|<xref:System.ArgumentException?displayProperty=fullName>|  
  
 Quando uma operação é inválida para o estado atual de um objeto throw<xref:System.InvalidOperationException?displayProperty=fullName>  
  
 Quando uma operação é executada em um objeto que foi descartado throw<xref:System.ObjectDisposedException?displayProperty=fullName>  
  
 Quando uma operação não tem suporte (como uma substituição **Stream.Write** em um fluxo aberto para leitura) throw<xref:System.NotSupportedException?displayProperty=fullName>  
  
 Quando uma conversão pode resultar em um estouro (como em uma sobrecarga de operador de conversão explícita) gerar<xref:System.OverflowException?displayProperty=fullName>  
  
 Em outras situações, considere a criação de seu próprio tipo que deriva de <xref:System.Exception> e lançar que.  
  
## <a name="how-to-fix-violations"></a>Como Corrigir Violações  
 Para corrigir uma violação desta regra, altere o tipo de exceção lançada para um tipo específico que não é um dos tipos de reservado.  
  
## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos  
 Não suprima um aviso nessa regra.  
  
## <a name="related-rules"></a>Regras relacionadas  
 [CA1031: não capturar tipos de exceção gerais](../code-quality/ca1031-do-not-catch-general-exception-types.md)