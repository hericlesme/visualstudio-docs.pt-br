---
title: Avisos de portabilidade | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.codeanalysis.PortabilityRules
helpviewer_keywords:
- portability warnings
- managed code analysis warnings, portability warnings
- warnings, portability
ms.assetid: 902e859a-2153-4970-baaa-8a5b4a11806f
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 112f3686f2a3d21b2d5d493498b42e9b63fdb05b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="portability-warnings"></a>Avisos de portabilidade
Avisos de portabilidade suportam a portabilidade entre diferentes sistemas operacionais.  
  
## <a name="in-this-section"></a>Nesta seção  
  
|Regra|Descrição|  
|----------|-----------------|  
|[CA1900: os campos de tipo de valor devem ser móveis](../code-quality/ca1900-value-type-fields-should-be-portable.md)|Esta regra verifica se estruturas que são declaradas usando um atributo de layout explícito serão alinhado corretamente quando passa por marshaling para código não gerenciado em sistemas operacionais de 64 bits.|  
|[CA1901: Declarações P/Invoke devem ser portáteis](../code-quality/ca1901-p-invoke-declarations-should-be-portable.md)|Essa regra avalia o tamanho de cada parâmetro e o valor de retorno de um P/Invoke e verifica se o seu tamanho é correto quando passa por marshaling para código não gerenciado em sistemas operacionais de 32 bits e 64 bits.|  
|[CA1903: usar apenas a API da estrutura de destino](../code-quality/ca1903-use-only-api-from-targeted-framework.md)|Um membro ou um tipo está usando um membro ou um tipo que foi introduzido em um service pack não incluído com a estrutura de destino do projeto.|