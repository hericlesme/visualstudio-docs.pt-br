---
title: "Análise de código para código gerenciado avisos | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.project.vcfxcoptool.enablefxcop
helpviewer_keywords:
- managed code analyis, warnings
- warnings, managed code analysis
- managed code analysis warnings
- code analysis,managed code
ms.assetid: 3c2741ff-0d3a-42e6-acd5-d42310bd03c4
caps.latest.revision: "20"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: dotnet
ms.openlocfilehash: 689fe39cfb8a7719efbba15b412800d9dfa78361
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="code-analysis-for-managed-code-warnings"></a>Avisos da análise de código para código gerenciado
A ferramenta de análise de código gerenciado fornece avisos que indicam as violações de regra nas bibliotecas de código gerenciado. Os avisos são organizados em áreas de regra, como design, localização, desempenho e segurança. Cada aviso significa uma violação de uma regra de análise de código gerenciado. Esta seção fornece discussões detalhadas e exemplos de cada aviso de análise de código gerenciado.  
  
 A tabela a seguir mostra o tipo de informação que é fornecido para cada aviso.  
  
|Item|Descrição|  
|----------|-----------------|  
|Tipo|O TypeName para a regra.|  
|CheckId|O identificador exclusivo para a regra. CheckId e categoria são usadas para supressão na origem de um aviso.|  
|Categoria|A categoria do aviso.|  
|Alteração Significativa|Se a correção de uma violação da regra é uma alteração significativa. Quebra de alteração significa que um assembly que tem uma dependência no destino que causou a violação não recompilará com o novo fixa versão ou pode falhar em tempo de execução devido à alteração. Quando várias correções estão disponíveis e pelo menos uma correção é uma alteração significativa e uma correção não for, tanto 'Recentes' e 'Sem quebra' são especificados.|  
|Causa|O código gerenciado específico que faz com que a regra gerar um alerta.|  
|Descrição|Discute os problemas que estão por trás do aviso.|  
|Como Corrigir Violações|Explica como alterar o código-fonte para satisfazer a regra e impedir que ele gera um aviso.|  
|Quando Suprimir Avisos|Descreve quando é seguro suprimir um aviso da regra.|  
|Exemplo de código|Exemplos que violam a regra e corrigido exemplos que atendem à regra.|  
|Avisos relacionados|Avisos relacionados.|  
  
## <a name="in-this-section"></a>Nesta seção  
  
|||  
|-|-|  
|[Avisos por CheckId](../code-quality/code-analysis-warnings-for-managed-code-by-checkid.md)|Lista todos os avisos por CheckId|  
|[Avisos de criptografia](../code-quality/cryptography-warnings.md)|Avisos que dão suporte a mais segura bibliotecas e aplicativos com o uso correto da criptografia.|  
|[Avisos de design](../code-quality/design-warnings.md)|Os avisos que dão suporte a biblioteca correta de design conforme especificado pelo [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] diretrizes de Design.|  
|[Avisos de globalização](../code-quality/globalization-warnings.md)|Avisos que oferecem suporte a aplicativos e bibliotecas prontos para o mundo.|  
|[Avisos de interoperabilidade](../code-quality/interoperability-warnings.md)|Avisos que dão suporte à interação com clientes COM.|  
|[Avisos de facilidade de manutenção](../code-quality/maintainability-warnings.md)|Avisos que oferecem suporte à manutenção de biblioteca e o aplicativo.|  
|[Avisos de mobilidade](../code-quality/mobility-warnings.md)|Avisos que dão suporte ao uso de energia eficiente.|  
|[Avisos de Nomenclatura](../code-quality/naming-warnings.md)|Os avisos que dão suporte a conformidade com as convenções de nomenclatura do [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] diretrizes de Design.|  
|[Avisos de desempenho](../code-quality/performance-warnings.md)|Avisos que oferecem suporte a aplicativos e bibliotecas de alto desempenho.|  
|[Avisos de portabilidade](../code-quality/portability-warnings.md)|Avisos que dão suporte a portabilidade entre plataformas diferentes.|  
|[Avisos de confiabilidade](../code-quality/reliability-warnings.md)|Avisos que oferecem suporte a confiabilidade de biblioteca e o aplicativo, como uso de memória e thread correto.|  
|[Avisos de segurança](../code-quality/security-warnings.md)|Avisos que dão suporte a mais segura de bibliotecas e aplicativos.|  
|[Avisos de Uso](../code-quality/usage-warnings.md)|Os avisos que dão suporte ao uso apropriado do [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].|  
|[Erros da política de análise de código](../code-quality/code-analysis-policy-errors.md)|Erros que ocorrem se a política de análise de código não for atendida no check-in.|