---
title: 'CA1020: Evitar namespaces com poucos tipos | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- CA1020
- AvoidNamespacesWithFewTypes
helpviewer_keywords:
- CA1020
- AvoidNamespacesWithFewTypes
ms.assetid: 9cb272f6-a3ff-45af-b35d-70dea620b074
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2a90f43735092591ad019fd2a46569e9302cf0c3
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="ca1020-avoid-namespaces-with-few-types"></a>CA1020: evitar namespaces com poucos tipos
|||  
|-|-|  
|NomeDoTipo|AvoidNamespacesWithFewTypes|  
|CheckId|CA1020|  
|Categoria|Microsoft.Design|  
|Alteração Significativa|Quebra|  
  
## <a name="cause"></a>Causa  
 Um namespace diferente do namespace global contém menos de cinco tipos.  
  
## <a name="rule-description"></a>Descrição da Regra  
 Certifique-se de que cada um dos seus namespaces tem uma organização lógica e tipos de existência de um motivo válido para colocar em um namespace de modo disperso preenchido. Namespaces deve conter tipos que são usados juntos na maioria dos cenários. Quando os aplicativos são mutuamente exclusivos, tipos devem estar localizados em namespaces separados. Por exemplo, o <xref:System.Web.UI> namespace contém tipos que são usados em aplicativos Web, e o <xref:System.Windows.Forms> namespace contém tipos que são usados em [!INCLUDE[TLA#tla_mswin](../code-quality/includes/tlasharptla_mswin_md.md)]-com base em aplicativos. Embora os dois namespaces têm tipos que controlam aspectos da interface do usuário, esses tipos não são projetados para uso no mesmo aplicativo. Portanto, eles estão localizados nos namespaces separados. Namespace cuidado organização também pode ser útil, pois ele aumenta a capacidade de descoberta de um recurso. Examinando a hierarquia de namespace, os consumidores de biblioteca devem ser capazes de localizar os tipos que implementam um recurso.  
  
> [!NOTE]
>  Tipos de tempo de design e as permissões não devem ser mescladas em outros namespaces de cumprimento dessa diretriz. Esses tipos pertencem a seus próprios namespaces abaixo o namespace principal e deve terminar com os namespaces `.Design` e `.Permissions`, respectivamente.  
  
## <a name="how-to-fix-violations"></a>Como Corrigir Violações  
 Para corrigir uma violação desta regra, tente combinar os namespaces que contêm apenas alguns tipos em um único namespace.  
  
## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos  
 É seguro suprimir um aviso dessa regra quando o namespace não contém tipos que são usados com os tipos de seus outros namespaces.