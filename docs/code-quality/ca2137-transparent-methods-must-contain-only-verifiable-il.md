---
title: "CA2137: Os métodos transparentes devem conter apenas verificável IL | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: CA2137
ms.assetid: cbaeb0e1-56b6-43b4-812a-596b2859c329
caps.latest.revision: "13"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 70a7574e0379c8e4b8dc9a888185efceb480fad4
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
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