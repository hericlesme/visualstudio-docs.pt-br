---
title: 'CA2137: Os métodos transparentes devem conter apenas verificável IL | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- CA2137
ms.assetid: cbaeb0e1-56b6-43b4-812a-596b2859c329
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 83c366bb69e25d128b190a9ee8b192f13cf61013
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="ca2137-transparent-methods-must-contain-only-verifiable-il"></a>CA2137: os métodos transparentes só devem conter IL verificável
|||  
|-|-|  
|NomeDoTipo|TransparentMethodsMustBeVerifiable|  
|CheckId|CA2137|  
|Categoria|Microsoft.Security|  
|Alteração Significativa|Quebra|  
  
## <a name="cause"></a>Causa  
 Um método contém código não verificável ou retorna um tipo por referência.  
  
## <a name="rule-description"></a>Descrição da Regra  
 Esta regra é acionada em tentativas por código transparente de segurança para executar MSIL (Microsoft Intermediate Language) não verificável. Entretanto, a regra não contém um verificador de IL completo e, em vez disso, usa heurística para capturar a maioria das violações de verificação de MSIL.  
  
 Para ter certeza de que seu código contém apenas verificável MSIL, execute [Peverify.exe (ferramenta PEVerify)](/dotnet/framework/tools/peverify-exe-peverify-tool) em seu assembly. Executar PEVerify com o **/ transparente** opção que limita a saída para apenas não verificável os métodos transparentes que causa um erro. Se a / opção transparente não for usada, PEVerify também verifica os métodos importantes que podem conter código não verificado.  
  
## <a name="how-to-fix-violations"></a>Como Corrigir Violações  
 Para corrigir uma violação desta regra, marcar o método com o <xref:System.Security.SecurityCriticalAttribute> ou <xref:System.Security.SecuritySafeCriticalAttribute> de atributo, ou remova o código não verificado.  
  
## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos  
 Não suprima um aviso nessa regra.  
  
## <a name="example"></a>Exemplo  
 O método neste exemplo usa o código não verificado e deve ser marcado com o <xref:System.Security.SecurityCriticalAttribute> ou <xref:System.Security.SecuritySafeCriticalAttribute> atributo.  
  
 [!code-csharp[FxCop.Security.CA2137.TransparentMethodsMustBeVerifiable#1](../code-quality/codesnippet/CSharp/ca2137-transparent-methods-must-contain-only-verifiable-il_1.cs)]