---
title: "Referência de API para modelar o SDK do Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 590c9a69-4e22-4841-bb23-f32e80ec1e76
caps.latest.revision: "8"
author: alancameronwills
ms.author: awills
manager: douge
ms.workload: multiple
ms.openlocfilehash: c5dace5862354c26a22b65b3f471163e50738c7c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="api-reference-for-modeling-sdk-for-visual-studio"></a>Referência de API do SDK de Modelagem para Visual Studio
O SDK de modelagem e visualização do Visual Studio fornece a plataforma na qual as ferramentas de linguagens específicas de domínio (DSL) são criadas.  
  
 Esta seção contém o material de referência para namespaces que têm nomes que começam com "Microsoft.VisualStudio.Modeling".  
  
|Namespace|Conteúdo|  
|---------------|-------------|  
|<xref:Microsoft.VisualStudio.Modeling?displayProperty=fullName>|Classes como ModelElement, que é a classe base de todas as classes de domínio que você define em uma DSL.|  
|<xref:Microsoft.VisualStudio.Modeling.Design?displayProperty=fullName>|Classes que fazem parte de uma definição de DSL.|  
|<xref:Microsoft.VisualStudio.Modeling.Diagnostics?displayProperty=fullName>|Os modelo Visualizador de armazenamento e desempenho ferramentas de medição.|  
|<xref:Microsoft.VisualStudio.Modeling.Diagrams?displayProperty=fullName>|Classes como ShapeElement, que é a classe base de todas as formas que você define em uma DSL.|  
|<xref:Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement?displayProperty=fullName>|Métodos de gesto e seleção.|  
|<xref:Microsoft.VisualStudio.Modeling.DslDefinition?displayProperty=fullName>|A API do designer de definição de DSL.|  
|<xref:Microsoft.VisualStudio.Modeling.DslDefinition.Design?displayProperty=fullName>|Classes internas do designer de definição de DSL.|  
|<xref:Microsoft.VisualStudio.Modeling.DslDefinition.ExtensionEnablement?displayProperty=fullName>|Atributos que permitem que você estenda o designer DSL com comandos, gestos e validação.|  
|<xref:Microsoft.VisualStudio.Modeling.Extensibility?displayProperty=fullName>|Métodos de extensão para ModelElement que implementam DSL extensibilidade.|  
|<xref:Microsoft.VisualStudio.Modeling.ExtensionEnablement?displayProperty=fullName>|Atributos de extensibilidade|  
|<xref:Microsoft.VisualStudio.Modeling.Immutability?displayProperty=fullName>|Permite que você torne partes de um modelo somente leitura.|  
|<xref:Microsoft.VisualStudio.Modeling.Integration?displayProperty=fullName>|A API de Modelbus, que ajuda a integrar modelos diferentes.|  
|<xref:Microsoft.VisualStudio.Modeling.Integration.Picker?displayProperty=fullName>|A caixa de diálogo que permite aos usuários navegar para modelos e elementos para criar referências de Modelbus.|  
|<xref:Microsoft.VisualStudio.Modeling.Integration.Picker.Hosting?displayProperty=fullName>|O serviço do seletor.|  
|<xref:Microsoft.VisualStudio.Modeling.Integration.Shell?displayProperty=fullName>|Estrutura do adaptador Modelbus para [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].|  
|<xref:Microsoft.VisualStudio.Modeling.Integration.Shell.Picker?displayProperty=fullName>|A caixa de diálogo Seletor que permite aos usuários navegar para modelos e elementos para criar referências de Modelbus.|  
|<xref:Microsoft.VisualStudio.Modeling.Shell?displayProperty=fullName>|A interface entre DSLs e [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].|  
|<xref:Microsoft.VisualStudio.Modeling.Shell.ExtensionEnablement?displayProperty=fullName>|Permite que você defina comandos de menu de atalho (contexto).|  
|<xref:Microsoft.VisualStudio.Modeling.Validation?displayProperty=fullName>|Permite que você defina restrições de validação.|  
  
## <a name="see-also"></a>Consulte também  
 [Personalizando a transformação de texto T4](../modeling/customizing-t4-text-transformation.md)
