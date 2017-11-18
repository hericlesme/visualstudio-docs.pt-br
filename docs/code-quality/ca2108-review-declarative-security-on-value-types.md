---
title: "CA2108: Revisar segurança declarativa em tipos de valor | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ReviewDeclarativeSecurityOnValueTypes
- CA2108
helpviewer_keywords:
- ReviewDeclarativeSecurityOnValueTypes
- CA2108
ms.assetid: d62bffdd-3826-4d52-a708-1c646c5d48c2
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: a2d7ecd899b4da51e6ff200f1e18b00366db6669
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="ca2108-review-declarative-security-on-value-types"></a>CA2108: revisar segurança declarativa em tipos de valor
|||  
|-|-|  
|NomeDoTipo|ReviewDeclarativeSecurityOnValueTypes|  
|CheckId|CA2108|  
|Categoria|Microsoft.Security|  
|Alteração Significativa|Não separáveis|  
  
## <a name="cause"></a>Causa  
 Um tipo de valor público ou protegido é protegido por um [dados e modelagem](/dotnet/framework/data/index) ou [demandas de Link](/dotnet/framework/misc/link-demands).  
  
## <a name="rule-description"></a>Descrição da Regra  
 Tipos de valor são alocados e inicializados por seus construtores padrão antes de executar outros construtores. Se um tipo de valor é protegido por um Demand ou LinkDemand, e o chamador não tem permissões que atendem a verificação de segurança, nenhum construtor diferente do padrão falhará e será gerada uma exceção de segurança. O tipo de valor não é desalocado; ele é deixado no estado definido por seu construtor padrão. Não suponha que um chamador que transmite uma instância do tipo de valor tem permissão para criar ou acessar a instância.  
  
## <a name="how-to-fix-violations"></a>Como Corrigir Violações  
 Você não pode corrigir uma violação desta regra, a menos que você remover a verificação de segurança do tipo e verificações de segurança em nível de método usar em seu lugar. Observe que corrigir a violação dessa maneira não impedirá que os chamadores com permissões inadequadas obtenham as instâncias do tipo de valor. Você deve garantir que uma instância do tipo de valor, no seu estado padrão, não expõem informações confidenciais e não pode ser usada de maneira prejudicial.  
  
## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos  
 Você pode suprimir um aviso de que essa regra se qualquer chamador pode obter instâncias do tipo de valor em seu estado padrão sem apresentando uma ameaça à segurança.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra uma biblioteca que contém um tipo de valor que viola essa regra. Observe que o `StructureManager` tipo presume que um chamador que transmite uma instância do tipo de valor tem permissão para criar ou acessar a instância.  
  
 [!code-csharp[FxCop.Security.DemandOnValueType#1](../code-quality/codesnippet/CSharp/ca2108-review-declarative-security-on-value-types_1.cs)]  
  
## <a name="example"></a>Exemplo  
 O aplicativo a seguir demonstra o problema da biblioteca.  
  
 [!code-csharp[FxCop.Security.TestDemandOnValueType#1](../code-quality/codesnippet/CSharp/ca2108-review-declarative-security-on-value-types_2.cs)]  
  
 Este exemplo gerencia a seguinte saída.  
  
 **Construtor personalizado estrutura: Falha na solicitação.**  
**Novos valores SecuredTypeStructure 100 100**  
**Novos valores SecuredTypeStructure 200 200**   
## <a name="see-also"></a>Consulte também  
 [Demandas de link](/dotnet/framework/misc/link-demands)   
 [Dados e modelagem](/dotnet/framework/data/index)