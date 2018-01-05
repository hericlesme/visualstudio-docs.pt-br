---
title: "Conjunto de regras de globalização para código gerenciado | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3c4032ee-0805-4581-8c48-b1827cd6b213
caps.latest.revision: "9"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: dotnet
ms.openlocfilehash: 07a2e8da87eb486f8247a79263ec371a8fd4afc5
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="globalization-rules-rule-set-for-managed-code"></a>Conjunto de regras de globalização para código gerenciado
Você pode usar o Microsoft globalização conjunto de regras para se concentrar nos problemas que podem impedir que os dados em seu aplicativo seja exibido corretamente em diferentes idiomas, localidades e culturas. Você deve incluir essa regra definida se seu aplicativo for localizado, globalizados, ou ambos.  
  
|Regra|Descrição|  
|----------|-----------------|  
|[CA1300](../code-quality/ca1300-specify-messageboxoptions.md)|Especificar MessageBoxOptions|  
|[CA1301](../code-quality/ca1301-avoid-duplicate-accelerators.md)|Evitar aceleradores duplicados|  
|[CA1302](../code-quality/ca1302-do-not-hardcode-locale-specific-strings.md)|Não codificar cadeias de caracteres específicas de localidade|  
|[CA1303](../code-quality/ca1303-do-not-pass-literals-as-localized-parameters.md)|Não passar literais como parâmetros localizados|  
|[CA1304](../code-quality/ca1304-specify-cultureinfo.md)|Especificar CultureInfo|  
|[CA1305](../code-quality/ca1305-specify-iformatprovider.md)|Especificar IFormatProvider|  
|[CA1306](../code-quality/ca1306-set-locale-for-data-types.md)|Definir localidade para tipos de dados|  
|[CA1307](../code-quality/ca1307-specify-stringcomparison.md)|Especificar StringComparison|  
|[CA1308](../code-quality/ca1308-normalize-strings-to-uppercase.md)|Normalizar cadeias de caracteres em maiusculas|  
|[CA1309](../code-quality/ca1309-use-ordinal-stringcomparison.md)|Usar StringComparison ordinal|  
|[CA2101](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)|Especificar marshaling para argumentos de cadeia de caracteres P/Invoke|