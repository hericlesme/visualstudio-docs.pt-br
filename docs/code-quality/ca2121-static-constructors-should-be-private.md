---
title: "Ca2121: os Construtores estáticos devem ser privados | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA2121
- StaticConstructorsShouldBePrivate
helpviewer_keywords:
- CA2121
- StaticConstructorsShouldBePrivate
ms.assetid: ee93c620-8fc1-4e47-866c-d389c3ca9f2e
caps.latest.revision: 
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 33770496c5d7585979d0be4198155982068957cf
ms.sourcegitcommit: d6327b978661c0a745bf4b59f32d8171607803a3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/01/2018
---
# <a name="ca2121-static-constructors-should-be-private"></a>CA2121: os construtores estáticos devem ser privados
|||  
|-|-|  
|NomeDoTipo|StaticConstructorsShouldBePrivate|  
|CheckId|CA2121|  
|Categoria|Microsoft.Security|  
|Alteração Significativa|Quebra|  
  
## <a name="cause"></a>Causa  
 Um tipo tem um construtor estático não é privado.  
  
## <a name="rule-description"></a>Descrição da Regra  
 Um construtor estático, também conhecido como um construtor de classe é usado para inicializar um tipo. O sistema chama o construtor estático antes que a primeira instância do tipo seja criada ou que outros membros estáticos sejam referenciados. O usuário não tem controle sobre quando o construtor estático é chamado. Se não for privado, um construtor estático poderá ser chamado por um código diferente do sistema. Dependendo das operações realizadas no construtor, isso pode causar um comportamento inesperado.  
  
 Essa regra é aplicada, os compiladores c# e Visual Basic.  
  
## <a name="how-to-fix-violations"></a>Como Corrigir Violações  
 Violações geralmente são causadas por uma das seguintes ações:  
  
-   Definido um construtor estático para o tipo e não faz privada.  
  
-   O compilador de linguagem de programação adicionado um construtor estático padrão para seu tipo e não faz privada.  
  
 Para corrigir o primeiro tipo de violação, torne o construtor estático privado. Para corrigir o segundo tipo, adicione um construtor estático privado para o seu tipo.  
  
## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos  
 Não suprima estas violações. Se o projeto de software requer uma chamada explícita para um construtor estático, é provável que o projeto contém falhas graves e deve ser revisado.