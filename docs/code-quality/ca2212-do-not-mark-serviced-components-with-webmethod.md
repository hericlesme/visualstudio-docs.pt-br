---
title: 'CA2212: não marcar componentes atendidos com WebMethod'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2212
- DoNotMarkServicedComponentsWithWebMethod
helpviewer_keywords:
- CA2212
- DoNotMarkServicedComponentsWithWebMethod
ms.assetid: 774bc55d-e588-48ee-8f38-c228580feca2
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 67d2e2790db4a3e8061dcd949b79c127e67f022d
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31922711"
---
# <a name="ca2212-do-not-mark-serviced-components-with-webmethod"></a>CA2212: não marcar componentes atendidos com WebMethod
|||
|-|-|
|NomeDoTipo|DoNotMarkServicedComponentsWithWebMethod|
|CheckId|CA2212|
|Categoria|Microsoft.Usage|
|Alteração Significativa|Quebra|

## <a name="cause"></a>Causa
 Um método em um tipo que herda de <xref:System.EnterpriseServices.ServicedComponent?displayProperty=fullName> está marcado com <xref:System.Web.Services.WebMethodAttribute?displayProperty=fullName>.

## <a name="rule-description"></a>Descrição da Regra
 <xref:System.Web.Services.WebMethodAttribute> aplica-se aos métodos em um serviço da Web em XML que foram criados usando o ASP.NET; ele torna o método pode ser chamado de clientes remotos da Web. O método e a classe devem ser público e em execução em um aplicativo Web ASP.NET. <xref:System.EnterpriseServices.ServicedComponent> tipos são hospedados por aplicativos COM+ e podem usar serviços COM+. <xref:System.Web.Services.WebMethodAttribute> não é aplicado a <xref:System.EnterpriseServices.ServicedComponent> porque eles não são destinados para os mesmos cenários. Especificamente, adicionando o atributo para o <xref:System.EnterpriseServices.ServicedComponent> método não faz o método pode ser chamado de clientes remotos da Web. Porque <xref:System.Web.Services.WebMethodAttribute> e um <xref:System.EnterpriseServices.ServicedComponent> método têm comportamentos conflitantes e requisitos para o contexto e fluxo de transações, o comportamento do método estará incorretos em alguns cenários.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir uma violação desta regra, remova o atributo do <xref:System.EnterpriseServices.ServicedComponent> método.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 Não suprima um aviso nessa regra. Não há nenhum cenário em que a combinação desses elementos está correto.

## <a name="see-also"></a>Consulte também
 <xref:System.EnterpriseServices.ServicedComponent?displayProperty=fullName> <xref:System.Web.Services.WebMethodAttribute?displayProperty=fullName>