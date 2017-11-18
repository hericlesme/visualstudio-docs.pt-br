---
title: "CA2207: Inicializar campos estáticos de tipo de valor embutido | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- InitializeValueTypeStaticFieldsInline
- CA2207
helpviewer_keywords:
- CA2207
- InitializeValueTypeStaticFieldsInline
ms.assetid: d1ea9d8b-ecc2-46ca-86e2-c41dd0e76658
caps.latest.revision: "14"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 7f22975ba591e4300e54a4bda01f3802b393ae59
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="ca2207-initialize-value-type-static-fields-inline"></a>CA2207: inicializar campos estáticos de tipo de valor embutido
|||  
|-|-|  
|NomeDoTipo|InitializeValueTypeStaticFieldsInline|  
|CheckId|CA2207|  
|Categoria|Microsoft.Usage|  
|Alteração Significativa|Não separáveis|  
  
## <a name="cause"></a>Causa  
 Um tipo de valor declara um construtor estático explícito.  
  
## <a name="rule-description"></a>Descrição da Regra  
 Quando um tipo de valor é declarado, passa por uma inicialização padrão, onde todos os campos de tipo de valor são definidos como zero e todos os campos de tipo de referência são definidos como `null` (`Nothing` no Visual Basic). Um construtor estático explícito só é garantido para ser executado antes de um construtor de instância ou um membro estático do tipo é chamado. Portanto, se o tipo é criado sem chamar um construtor de instância, o construtor estático não é garantido para ser executado.  
  
 Se todos os dados estáticos são inicializado embutido e nenhum construtor estático explícito é declarado, os compiladores c# e Visual Basic, adicione o `beforefieldinit` sinalizador à definição de classe MSIL. Os compiladores também adicionar um construtor estático particular que contém o código de inicialização estática. Este construtor estático privado é garantido para ser executado antes de qualquer campo estático do tipo é acessado.  
  
## <a name="how-to-fix-violations"></a>Como Corrigir Violações  
 Para corrigir uma violação desta regra inicializar todos os dados estáticos quando ele é declarado e remover o construtor estático.  
  
## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos  
 Não suprima um aviso nessa regra.  
  
## <a name="related-rules"></a>Regras relacionadas  
 [CA1810: inicializar campos estáticos de tipo de referência embutido](../code-quality/ca1810-initialize-reference-type-static-fields-inline.md)