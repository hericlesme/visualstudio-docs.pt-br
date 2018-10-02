---
title: 'CA1823: Evitar campos privados não usados | Microsoft Docs'
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
- AvoidUnusedPrivateFields
- CA1823
helpviewer_keywords:
- AvoidUnusedPrivateFields
- CA1823
ms.assetid: 614f94f6-0dc7-430f-8124-cb889a4a720f
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: bfe51ab6c163c82d413c5c7cc74edc0b980abd85
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/24/2018
ms.locfileid: "47476441"
---
# <a name="ca1823-avoid-unused-private-fields"></a>CA1823: evitar campos privados não usados
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [CA1823: evitar campos privados não usados](https://docs.microsoft.com/visualstudio/code-quality/ca1823-avoid-unused-private-fields).

|||
|-|-|
|NomeDoTipo|AvoidUnusedPrivateFields|
|CheckId|CA1823|
|Categoria|Microsoft.Performance|
|Alteração Significativa|Não são significativas|

## <a name="cause"></a>Causa
 Essa regra é relatada quando um campo particular em seu código existe, mas não é usado por qualquer caminho de código.

## <a name="rule-description"></a>Descrição da Regra
 Foram detectados campos particulares que aparentemente não são acessados no assembly.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir uma violação dessa regra, remova o campo ou adicionar código que o usa.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 É seguro suprimir um aviso nessa regra.

## <a name="related-rules"></a>Regras relacionadas
 [CA1812: evitar classes internas sem instâncias](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)

 [CA1801: examinar parâmetros não usados](../code-quality/ca1801-review-unused-parameters.md)

 [CA1804: remover locais não usados](../code-quality/ca1804-remove-unused-locals.md)

 [CA1811: evitar código privado não chamado](../code-quality/ca1811-avoid-uncalled-private-code.md)



