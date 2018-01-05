---
title: "CA2109: Revisar manipuladores de eventos visíveis | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA2109
- ReviewVisibleEventHandlers
helpviewer_keywords:
- ReviewVisibleEventHandlers
- CA2109
ms.assetid: 8f8fa0ee-e94e-400e-b516-24d8727725d7
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 42b4ed61faae66c0a07e171a89a6ac9e4b9157e2
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ca2109-review-visible-event-handlers"></a>CA2109: revisar manipuladores de eventos visíveis
|||  
|-|-|  
|NomeDoTipo|ReviewVisibleEventHandlers|  
|CheckId|CA2109|  
|Categoria|Microsoft.Security|  
|Alteração Significativa|Quebra|  
  
## <a name="cause"></a>Causa  
 Um método público ou protegido de tratamento de eventos foi detectado.  
  
## <a name="rule-description"></a>Descrição da Regra  
 Um método de manipulação de eventos visível externamente apresenta um problema de segurança que requer a revisão.  
  
 Os métodos de tratamento de eventos não devem ser expostos, a menos que seja absolutamente necessário. Um manipulador de eventos, um tipo de delegado, que chama o método exposto pode ser adicionado a qualquer evento desde que as assinaturas de evento e manipulador correspondem. Eventos potencialmente podem ser gerados por qualquer código e frequentemente são gerados pelo código do sistema altamente confiáveis em resposta a ações do usuário, como clicar em um botão. Adicionar uma verificação de segurança para um método de manipulação de eventos não impedir que o código ao registrar um manipulador de eventos que chama o método.  
  
 Uma demanda de forma confiável não pode proteger um método invocado por um manipulador de eventos. Demandas de segurança ajuda proteger o código de chamadores não confiáveis, examinando os chamadores na pilha de chamadas. Código que adiciona um manipulador de eventos para um evento não é necessariamente presente na pilha de chamadas quando os métodos do manipulador de eventos é executado. Portanto, a pilha de chamadas pode ter apenas altamente confiável chamadores quando o método de manipulador de eventos é chamado. Isso faz com que as demandas feitas pelo método de manipulador de eventos seja bem-sucedida. Além disso, a permissão exigida pode ser declarada quando o método é invocado. Por esses motivos, o risco de não corrigir uma violação desta regra pode ser avaliado somente depois de examinar o método de manipulação de eventos. Ao revisar seu código, considere os seguintes problemas:  
  
-   O manipulador de eventos realiza todas as operações que são perigosas ou explorável como declarando permissões ou suprimindo permissão de código não gerenciado?  
  
-   Quais são as ameaças de segurança de seu código e como ele pode ser executado a qualquer momento com apenas altamente confiável chamadores na pilha?  
  
## <a name="how-to-fix-violations"></a>Como Corrigir Violações  
 Para corrigir uma violação desta regra, examine o método e avaliar o seguinte:  
  
-   Você pode fazer o método de manipulação de eventos não público?  
  
-   Você pode mover todas as funcionalidades perigosas fora do manipulador de eventos?  
  
-   Se uma exigência de segurança é imposta, isso pode ser feito em alguma outra forma?  
  
## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos  
 Suprima um aviso dessa regra somente após uma revisão de segurança cuidado para garantir que seu código não representem uma ameaça de segurança.  
  
## <a name="example"></a>Exemplo  
 O código a seguir mostra um método de manipulação de eventos que pode ser usados incorretamente por códigos mal-intencionados.  
  
 [!code-csharp[FxCop.Security.EventSecLib#1](../code-quality/codesnippet/CSharp/ca2109-review-visible-event-handlers_1.cs)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Security.CodeAccessPermission.Demand%2A?displayProperty=fullName>   
 <xref:System.EventArgs?displayProperty=fullName>   
 