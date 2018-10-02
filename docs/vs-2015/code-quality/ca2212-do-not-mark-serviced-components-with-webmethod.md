---
title: 'CA2212: Não marcar componentes atendidos com WebMethod | Microsoft Docs'
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
- CA2212
- DoNotMarkServicedComponentsWithWebMethod
helpviewer_keywords:
- CA2212
- DoNotMarkServicedComponentsWithWebMethod
ms.assetid: 774bc55d-e588-48ee-8f38-c228580feca2
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 33f23ead1a4236c60e8c152f5064d6d1b6f4d3b3
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/24/2018
ms.locfileid: "47587132"
---
# <a name="ca2212-do-not-mark-serviced-components-with-webmethod"></a>CA2212: não marcar componentes atendidos com WebMethod
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [CA2212: não marcar componentes atendidos com WebMethod](https://docs.microsoft.com/visualstudio/code-quality/ca2212-do-not-mark-serviced-components-with-webmethod).

|||
|-|-|
|NomeDoTipo|DoNotMarkServicedComponentsWithWebMethod|
|CheckId|CA2212|
|Categoria|Microsoft.Usage|
|Alteração Significativa|Quebra|

## <a name="cause"></a>Causa
 Um método em um tipo que herda de <xref:System.EnterpriseServices.ServicedComponent?displayProperty=fullName> está marcado com <xref:System.Web.Services.WebMethodAttribute?displayProperty=fullName>.

## <a name="rule-description"></a>Descrição da Regra
 <xref:System.Web.Services.WebMethodAttribute> se aplica aos métodos dentro de um serviço Web XML criados usando o ASP.NET; ele torna o método chamável de clientes remotos da Web. O método e a classe devem ser pública e em execução em um aplicativo Web ASP.NET. <xref:System.EnterpriseServices.ServicedComponent> tipos são hospedados por aplicativos COM+ e podem usar serviços COM+. <xref:System.Web.Services.WebMethodAttribute> não é aplicado a <xref:System.EnterpriseServices.ServicedComponent> porque eles não devem ser os mesmos cenários. Especificamente, adicionando o atributo para o <xref:System.EnterpriseServices.ServicedComponent> método não faz o método que pode ser chamado de clientes remotos da Web. Porque <xref:System.Web.Services.WebMethodAttribute> e um <xref:System.EnterpriseServices.ServicedComponent> método têm comportamentos conflitantes e requisitos para o contexto e fluxo de transações, o comportamento do método estará incorretos em alguns cenários.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir uma violação dessa regra, remova o atributo do <xref:System.EnterpriseServices.ServicedComponent> método.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 Não suprima um aviso nessa regra. Não há nenhum cenário em que a combinação desses elementos está correto.

## <a name="see-also"></a>Consulte também
 <xref:System.EnterpriseServices.ServicedComponent?displayProperty=fullName> <xref:System.Web.Services.WebMethodAttribute?displayProperty=fullName>



