---
title: "CA1713: Os eventos não devem ter prefixo before ou after | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- EventsShouldNotHaveBeforeOrAfterPrefix
- CA1713
helpviewer_keywords:
- CA1713
- EventsShouldNotHaveBeforeOrAfterPrefix
ms.assetid: 855772a4-aa9e-410b-88c1-c5fba1ca63da
caps.latest.revision: "14"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: c211d2f2cc65c12fd11782058c5e8b8a3aaf47b6
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="ca1713-events-should-not-have-before-or-after-prefix"></a>CA1713: os eventos não devem ter um prefixo anterior ou posterior
|||  
|-|-|  
|NomeDoTipo|EventsShouldNotHaveBeforeOrAfterPrefix|  
|CheckId|CA1713|  
|Categoria|Microsoft.Naming|  
|Alteração Significativa|Quebra|  
  
## <a name="cause"></a>Causa  
 O nome de um evento começa com 'Before' ou 'After'.  
  
## <a name="rule-description"></a>Descrição da Regra  
 Nomes de evento devem descrever a ação que gera o evento. Para nomear eventos relacionados acionados em uma sequência específica, use o presente ou o pretérito para indicar a posição relativa na sequência de ações. Por exemplo, quando um par de eventos de nomenclatura que é gerado quando um recurso de fechamento, você pode nomeá-lo 'De fechamento' e 'Fechado', em vez de 'BeforeClose' e 'AfterClose'.  
  
 Convenções de nomenclatura fornecem uma aparência comum para bibliotecas de destino do common language runtime. Isso reduz a curva de aprendizado que é necessário para novas bibliotecas de software e aumenta a confiança do cliente que a biblioteca foi desenvolvida por uma pessoa com experiência em desenvolvimento de código gerenciado.  
  
## <a name="how-to-fix-violations"></a>Como Corrigir Violações  
 Remova o prefixo do nome do evento e considere alterar o nome para usar o presente ou no passado de um verbo.  
  
## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos  
 Não suprima um aviso nessa regra.