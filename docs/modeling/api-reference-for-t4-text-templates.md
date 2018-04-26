---
title: Referência de API para modelos de texto T4
ms.date: 11/04/2016
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: ea0b136659b57b8430a355b4e231423c5e55b2b9
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="api-reference-for-t4-text-templates"></a>Referência de API para modelos de texto T4

A API de modelagem de texto permite invocar e personalizar a transformação de [modelos de texto](../modeling/code-generation-and-t4-text-templates.md).

## <a name="namespaces"></a>Namespaces

|Namespace|Finalidade|
|---------------|-------------|
|<xref:Microsoft.VisualStudio.TextTemplating>|Contém classes para a funcionalidade de transformação de modelo de texto. O mecanismo de transformação de modelo de texto é integrado ao Visual Studio e transforma os arquivos de modelo de texto em arquivos de saída de texto gerado.|
|<xref:Microsoft.VisualStudio.TextTemplating.Modeling>|Fornece o texto de recursos de transformação relacionados a modelos UML e linguagens específicas de domínio, como acesso a [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ModelBus.|
|<xref:Microsoft.VisualStudio.TextTemplating.VSHost>|Fornece acesso ao serviço de modelagem de texto em [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].|