---
title: 'CA1030: Usar eventos quando apropriado | Microsoft Docs'
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
- UseEventsWhereAppropriate
- CA1030
helpviewer_keywords:
- CA1030
- UseEventsWhereAppropriate
ms.assetid: ea051367-deeb-40f9-9b65-eb818f1e133a
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 8100aff6c2215d9a5fa031d69fc0ee105e440e3a
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/24/2018
ms.locfileid: "47587312"
---
# <a name="ca1030-use-events-where-appropriate"></a>CA1030: usar eventos quando apropriado
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [CA1030: usar eventos quando apropriado](https://docs.microsoft.com/visualstudio/code-quality/ca1030-use-events-where-appropriate).

|||
|-|-|
|NomeDoTipo|UseEventsWhereAppropriate|
|CheckId|CA1030|
|Categoria|Microsoft.Design|
|Alteração Significativa|Não são significativas|

## <a name="cause"></a>Causa
 Um nome de método público, protegido ou particular começa com um dos seguintes:

-   Complemento

-   RemoveOn

-   Fogo

-   Gerar

## <a name="rule-description"></a>Descrição da Regra
 Essa regra detecta métodos que têm nomes que seriam usados normalmente em eventos. Os eventos seguem o padrão de design do observador ou publicar-assinar; eles são usados quando uma alteração de estado em um objeto deve ser comunicada aos outros objetos. Se um método é chamado em resposta a uma alteração de estado claramente definida, o método deve ser invocado por um manipulador de eventos. Os objetos que chamam o método devem acionar eventos, em vez de chamar o método diretamente.

 Alguns exemplos comuns de eventos são encontrados em aplicativos de interface do usuário em que uma ação do usuário, como clicar em um botão faz com que um segmento de código a ser executado. O [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] modelo de evento não é limitado a interfaces do usuário; ele deve ser usado em qualquer lugar, você deve comunicar o estado muda para um ou mais objetos.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Se o método é chamado quando o estado de um objeto é alterado, considere alterar o design para usar o [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] modelo de evento.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 Suprimir um aviso nessa regra, se o método não funciona com o [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] modelo de evento.



