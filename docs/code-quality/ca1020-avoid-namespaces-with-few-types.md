---
title: 'CA1020: evitar namespaces com poucos tipos'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
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
ms.openlocfilehash: d95e626349296f9b6c857263a78ce67751b471b5
ms.sourcegitcommit: 5b767247b3d819a99deb0dbce729a0562b9654ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/20/2018
ms.locfileid: "39178924"
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

Certifique-se de que cada um dos namespaces tem uma organização lógica e a existência de um motivo válido para colocar tipos em um namespace populado de modo disperso. Namespaces deve conter tipos que são usados juntos na maioria dos cenários. Quando seus aplicativos são mutuamente exclusivos, tipos deverá estar localizados em namespaces separados. Por exemplo, o <xref:System.Web.UI> namespace contém tipos que são usados em aplicativos web, e o <xref:System.Windows.Forms> namespace contém tipos que são usados em [!INCLUDE[TLA#tla_mswin](../code-quality/includes/tlasharptla_mswin_md.md)]-com base em aplicativos. Embora ambos os namespaces têm tipos que controlam aspectos da interface do usuário, esses tipos não são projetados para uso no mesmo aplicativo. Portanto, eles estão localizados em namespaces separados. Namespace cuidado organização também pode ser útil, pois ele aumenta a detectabilidade de um recurso. Examinando a hierarquia de namespace, os clientes de biblioteca devem ser capazes de localizar os tipos que implementam um recurso.

> [!NOTE]
> Permissões e tipos de tempo de design não devem ser mescladas em outros namespaces em conformidade com essa diretriz. Esses tipos pertencem a seus próprios namespaces abaixo seu namespace principal, e deve terminar com os namespaces `.Design` e `.Permissions`, respectivamente.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações

Para corrigir uma violação dessa regra, tente combinar os namespaces que contêm apenas alguns tipos em um único namespace.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos

É seguro suprimir um aviso nessa regra, quando o namespace não contém tipos que são usados com os tipos de seus outros namespaces.