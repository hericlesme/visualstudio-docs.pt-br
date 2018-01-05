---
title: "CA1823: Evitar campos privados não usados | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- AvoidUnusedPrivateFields
- CA1823
helpviewer_keywords:
- AvoidUnusedPrivateFields
- CA1823
ms.assetid: 614f94f6-0dc7-430f-8124-cb889a4a720f
caps.latest.revision: "11"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 8843db809184afee02a104b719392da75b14bec3
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ca1823-avoid-unused-private-fields"></a>CA1823: evitar campos privados não usados
|||  
|-|-|  
|NomeDoTipo|AvoidUnusedPrivateFields|  
|CheckId|CA1823|  
|Categoria|Microsoft.Performance|  
|Alteração Significativa|Não recentes|  
  
## <a name="cause"></a>Causa  
 Essa regra é relatada quando um campo particular em seu código existe, mas não é usado por qualquer caminho de código.  
  
## <a name="rule-description"></a>Descrição da Regra  
 Foram detectados campos particulares que aparentemente não são acessados no assembly.  
  
## <a name="how-to-fix-violations"></a>Como Corrigir Violações  
 Para corrigir uma violação desta regra, remova o campo ou adicionar o código que o usa.  
  
## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos  
 É seguro suprimir um aviso dessa regra.  
  
## <a name="related-rules"></a>Regras relacionadas  
 [CA1812: evitar classes internas sem instâncias](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)  
  
 [CA1801: examinar parâmetros não usados](../code-quality/ca1801-review-unused-parameters.md)  
  
 [CA1804: remover locais não usados](../code-quality/ca1804-remove-unused-locals.md)  
  
 [CA1811: evitar código privado não chamado](../code-quality/ca1811-avoid-uncalled-private-code.md)