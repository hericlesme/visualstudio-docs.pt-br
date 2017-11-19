---
title: "CA1822: Marcar membros como estáticos | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- MarkMembersAsStatic
- CA1822
helpviewer_keywords:
- MarkMembersAsStatic
- CA1822
ms.assetid: 743f0af7-41d1-4852-8d97-af0688b31118
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 160b263bde66496bad4f4fcb363852bdb174ff62
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="ca1822-mark-members-as-static"></a>CA1822: marcar membros como estáticos
|||  
|-|-|  
|NomeDoTipo|MarkMembersAsStatic|  
|CheckId|CA1822|  
|Categoria|Microsoft.Performance|  
|Alteração Significativa|Separação de não - se o membro não é visível fora do assembly, independentemente da alteração é fazer. Separação de não - se você alterar o membro a um membro de instância com o `this` palavra-chave.<br /><br /> Quebrando - se você alterar o membro de um membro de instância para um membro estático e é visível fora do assembly.|  
  
## <a name="cause"></a>Causa  
 Um membro que não acessam os dados de instância não está marcado como estático (compartilhado no [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]).  
  
## <a name="rule-description"></a>Descrição da Regra  
 Os membros que não acessam dados da instância ou os métodos da instância de chamada podem ser marcados como estáticos (Shared no [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]). Depois que você marcar os métodos como estáticos, o compilador emitirá sites de chamada não virtuais para esses membros. Emitir sites de chamada impedirá que uma verificação em tempo de execução para cada chamada que garante que o ponteiro de objeto atual é não-nulo. Isso pode obter ganhos de desempenho mensurável para código sensível de desempenho. Em alguns casos, a falha ao acessar a instância atual do objeto representa um problema de exatidão.  
  
## <a name="how-to-fix-violations"></a>Como Corrigir Violações  
 Marque o membro como estático (ou compartilhado em [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) ou use 'this' / 'Me' no método body, se apropriado.  
  
## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos  
 É seguro suprimir um aviso dessa regra para o código fornecido anteriormente para os quais a correção seria uma alteração significativa.  
  
## <a name="related-rules"></a>Regras relacionadas  
 [CA1811: evitar código privado não chamado](../code-quality/ca1811-avoid-uncalled-private-code.md)  
  
 [CA1812: evitar classes internas sem instâncias](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)  
  
 [CA1804: remover locais não usados](../code-quality/ca1804-remove-unused-locals.md)