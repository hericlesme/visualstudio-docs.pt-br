---
title: 'CA1030: Usar eventos quando apropriado | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- UseEventsWhereAppropriate
- CA1030
helpviewer_keywords:
- CA1030
- UseEventsWhereAppropriate
ms.assetid: ea051367-deeb-40f9-9b65-eb818f1e133a
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 644e8c32c3c827431d347966d8bbecdc13585c5f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="ca1030-use-events-where-appropriate"></a>CA1030: usar eventos quando apropriado
|||  
|-|-|  
|NomeDoTipo|UseEventsWhereAppropriate|  
|CheckId|CA1030|  
|Categoria|Microsoft.Design|  
|Alteração Significativa|Não recentes|  
  
## <a name="cause"></a>Causa  
 Um nome de método pública, protegida ou privada começa com um dos seguintes:  
  
-   Complemento  
  
-   RemoveOn  
  
-   Incêndio  
  
-   Gerar  
  
## <a name="rule-description"></a>Descrição da Regra  
 Essa regra detecta métodos que têm nomes que seriam usados normalmente em eventos. Eventos seguem o padrão de design do observador ou assinar a publicação; elas são usadas quando uma alteração de estado em um objeto deve ser comunicada aos outros objetos. Se um método é chamado em resposta a uma alteração de estado claramente definida, o método deve ser chamado por um manipulador de eventos. Os objetos que chamam o método devem acionar eventos, em vez de chamar o método diretamente.  
  
 Alguns exemplos comuns de eventos são encontrados em aplicativos de interface de usuário em que uma ação do usuário, como clicar em um botão faz com que um segmento de código a ser executado. O [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] modelo de evento não é limitado às interfaces do usuário; ele deve ser usado em qualquer lugar, você deverá comunicar o estado muda para um ou mais objetos.  
  
## <a name="how-to-fix-violations"></a>Como Corrigir Violações  
 Se o método é chamado quando o estado de um objeto é alterado, considere alterar o projeto para usar o [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] modelo de evento.  
  
## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos  
 Suprimir um aviso de que essa regra se o método não funciona com o [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] modelo de evento.