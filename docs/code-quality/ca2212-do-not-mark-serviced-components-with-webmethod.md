---
title: "CA2212: Não marcar componentes atendidos com WebMethod | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA2212
- DoNotMarkServicedComponentsWithWebMethod
helpviewer_keywords:
- CA2212
- DoNotMarkServicedComponentsWithWebMethod
ms.assetid: 774bc55d-e588-48ee-8f38-c228580feca2
caps.latest.revision: "13"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 44c29215301212a12c5652fbf1fe91af23db1082
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
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
 <xref:System.Web.Services.WebMethodAttribute>aplica-se aos métodos em um serviço da Web em XML que foram criados usando o ASP.NET; ele torna o método pode ser chamado de clientes remotos da Web. O método e a classe devem ser público e em execução em um aplicativo Web ASP.NET. <xref:System.EnterpriseServices.ServicedComponent>tipos são hospedados por aplicativos COM+ e podem usar serviços COM+. <xref:System.Web.Services.WebMethodAttribute>não é aplicado a <xref:System.EnterpriseServices.ServicedComponent> porque eles não são destinados para os mesmos cenários. Especificamente, adicionando o atributo para o <xref:System.EnterpriseServices.ServicedComponent> método não faz o método pode ser chamado de clientes remotos da Web. Porque <xref:System.Web.Services.WebMethodAttribute> e um <xref:System.EnterpriseServices.ServicedComponent> método têm comportamentos conflitantes e requisitos para o contexto e fluxo de transações, o comportamento do método estará incorretos em alguns cenários.  
  
## <a name="how-to-fix-violations"></a>Como Corrigir Violações  
 Para corrigir uma violação desta regra, remova o atributo do <xref:System.EnterpriseServices.ServicedComponent> método.  
  
## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos  
 Não suprima um aviso nessa regra. Não há nenhum cenário em que a combinação desses elementos está correto.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.EnterpriseServices.ServicedComponent?displayProperty=fullName>   
 <xref:System.Web.Services.WebMethodAttribute?displayProperty=fullName>