---
title: "CA2145: Os métodos transparentes não devem ser decorados com o SuppressUnmanagedCodeSecurityAttribute | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: CA2145
ms.assetid: 81970700-b438-4b3b-9239-16887e16f7b7
caps.latest.revision: "11"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 23cf7599e4d699a6be42bae55381ffb31ce1556e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="ca2145-transparent-methods-should-not-be-decorated-with-the-suppressunmanagedcodesecurityattribute"></a>CA2145: os métodos transparentes não devem ser decorados com o SuppressUnmanagedCodeSecurityAttribute
|||  
|-|-|  
|NomeDoTipo|TransparentMethodsShouldNotUseSuppressUnmanagedCodeSecurity|  
|CheckId|CA2145|  
|Categoria|Microsoft.Security|  
|Alteração Significativa|Quebra|  
  
## <a name="cause"></a>Causa  
 Um método transparente, um método marcado com o <xref:System.Security.SecuritySafeCriticalAttribute> método ou um tipo que contém um método é marcado com o <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> atributo.  
  
## <a name="rule-description"></a>Descrição da Regra  
 Métodos decorados com o <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> atributo tem um LinkDemand implícita colocada em qualquer método que o chama. Este LinkDemand requer que o código de chamada seja crítico de segurança. Marcar o método que usa SuppressUnmanagedCodeSecurity com o <xref:System.Security.SecurityCriticalAttribute> atributo torna esse requisito mais óbvio para chamadores do método.  
  
## <a name="how-to-fix-violations"></a>Como Corrigir Violações  
 Para corrigir uma violação desta regra, marque o método ou tipo com o <xref:System.Security.SecurityCriticalAttribute> atributo.  
  
## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos  
 Não suprima um aviso nessa regra.  
  
### <a name="code"></a>Código  
 [!code-csharp[FxCop.Security.CA2145.TransparentMethodsShouldNotUseSuppressUnmanagedCodeSecurity#1](../code-quality/codesnippet/CSharp/ca2145-transparent-methods-should-not-be-decorated-with-the-suppressunmanagedcodesecurityattribute_1.cs)]  
  
### <a name="comments"></a>Comentários