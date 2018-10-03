---
title: 'CA1900: Os campos de tipo de valor devem ser móveis | Microsoft Docs'
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
- CA1900
- ValueTypeFieldsShouldBePortable
helpviewer_keywords:
- ValueTypeFieldsShouldBePortable
- CA1900
ms.assetid: 1787d371-389f-4d39-b305-12b53bc0dfb9
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: b0a636c1de245aa46adb0b0e43c6802dddf57810
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47475710"
---
# <a name="ca1900-value-type-fields-should-be-portable"></a>CA1900: os campos de tipo de valor devem ser móveis
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Para obter a documentação mais recente do Visual Studio 2017, consulte [CA1900: os campos de tipo de valor devem ser portáteis](https://docs.microsoft.com/visualstudio/code-quality/ca1900-value-type-fields-should-be-portable) em docs.microsoft.com.  
  
|||  
|-|-|  
|NomeDoTipo|ValueTypeFieldsShouldBePortable|  
|CheckId|CA1900|  
|Categoria|Microsoft.Portability|  
|Alteração Significativa|Quebrando - se o campo pode ser visto de fora do assembly.<br /><br /> Sem quebra - se o campo não está visível fora do assembly.|  
  
## <a name="cause"></a>Causa  
 Esta regra verifica que estruturas que são declaradas com layout explícito serão corretamente alinhados quando passa por marshaling para código não gerenciado em sistemas operacionais de 64 bits. IA-64 não permite que os acessos à memória desalinhada e o processo falhará se essa violação não for corrigida.  
  
## <a name="rule-description"></a>Descrição da Regra  
 Estruturas com layout explícito contendo campos desalinhados podem causar quedas em sistemas operacionais de 64 bits.  
  
## <a name="how-to-fix-violations"></a>Como Corrigir Violações  
 Todos os campos que são menores do que 8 bytes devem ter os deslocamentos são um múltiplo de seu tamanho e os campos que são 8 bytes ou mais devem ter os deslocamentos são um múltiplo de 8. Outra solução é usar `LayoutKind.Sequential` em vez de `LayoutKind.Explicit`, se razoável.  
  
## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos  
 Esse aviso deve ser suprimido somente se ele ocorrer no erro.

