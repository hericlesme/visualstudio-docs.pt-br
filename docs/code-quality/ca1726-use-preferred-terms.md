---
title: 'CA1726: Usar termos preferenciais | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- UsePreferredTerms
- CA1726
helpviewer_keywords: UsePreferredTerms
ms.assetid: 642b2acd-3a33-4d1f-b0a7-67073ae73be2
caps.latest.revision: "23"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 63a27c62f46343ac840a550ccbefd30f20e9f06a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ca1726-use-preferred-terms"></a>CA1726: usar termos preferenciais
|||  
|-|-|  
|NomeDoTipo|UsePreferredTerms|  
|CheckId|CA1726|  
|Categoria|Microsoft.Naming|  
|Alteração Significativa|Quebra - quando disparado em assemblies<br /><br /> Separação de não - quando disparado em parâmetros de tipo|  
  
## <a name="cause"></a>Causa  
 O nome de um identificador visível externamente inclui um termo para o qual existe um termo preferido, alternativo. Como alternativa, o nome inclui o termo sinalizador ou sinalizadores.  
  
## <a name="rule-description"></a>Descrição da Regra  
 Esta regra analisa um identificador em tokens. Cada combinação de token dupla contígua e cada token único é comparado com termos que são criados para a regra e na seção preterido dicionários personalizados. A tabela a seguir mostra os termos que são incorporados a regra e suas alternativas preferenciais.  
  
|Termo obsoleto|Termo preferencial|  
|-------------------|--------------------|  
|não são|Não são|  
|Cancelada|Cancelado|  
|Não é possível|Não é possível|  
|ComPlus|EnterpriseServices|  
|Couldnt|Não foi|  
|Didnt|DidNot|  
|Doesnt|Não|  
|Não|Não|  
|Sinalizador ou sinalizadores|Não há nenhum termo de substituição. Não use.|  
|não haviam|HadNot|  
|Não|HasNot|  
|ainda não|HaveNot|  
|Índices|Índices|  
|não é|IsNot|  
|Logon|LogOn|  
|Logoff|Fazer LogOff|  
|Shouldnt|ShouldNot|  
|Logon|Entrar|  
|Aprovação|Saída|  
|Wasnt|WasNot|  
|não foram|Não foram|  
|Não|Vai|  
|Wouldnt|WouldNot|  
|Gravável|Gravável|  
  
## <a name="how-to-fix-violations"></a>Como Corrigir Violações  
 Para corrigir uma violação desta regra, substitua o termo com o termo alternativo preferido.  
  
## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos  
 Suprima um aviso dessa regra somente se o nome do identificador é intencional e se relaciona especificamente para o termo original em vez do termo preferencial.  
  
## <a name="related-rules"></a>Regras relacionadas  
 [Avisos de Nomenclatura](../code-quality/naming-warnings.md)