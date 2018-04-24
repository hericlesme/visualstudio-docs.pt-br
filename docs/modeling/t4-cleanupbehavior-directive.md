---
title: Diretiva CleanUpBehavior T4
ms.date: 11/04/2016
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: cb9c92aad2518a9e16adbcb37006c62c421c4361
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/20/2018
---
# <a name="t4-cleanupbehavior-directive"></a>Diretiva CleanUpBehavior T4

Para excluir o appDomain depois de processar um modelo de texto, inclua a seguinte linha:

```
<#@ CleanupBehavior processor="T4VSHost" CleanupAfterProcessingtemplate="true" #>
```

Os modelos de texto são processados em um appDomain que é separado do processo do host. Na maioria dos casos, quando um modelo de texto é processado, o appdomain é usado novamente para processar o próximo modelo. Mas se você especificar CleanupBehavior, o appDomain será excluído e o próximo modelo será processado em um novo appDomain.

Isso reduz o processamento de texto, mas pode ser útil para garantir que os recursos sejam descartados.

Essa diretiva só funciona no host do Visual Studio.