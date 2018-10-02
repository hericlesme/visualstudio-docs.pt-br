---
title: 'CA2137: Métodos transparentes devem conter apenas verificável IL | Microsoft Docs'
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
- CA2137
ms.assetid: cbaeb0e1-56b6-43b4-812a-596b2859c329
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 77ff02a0db733c3151f4faccd00e07518d61e600
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/24/2018
ms.locfileid: "47586992"
---
# <a name="ca2137-transparent-methods-must-contain-only-verifiable-il"></a>CA2137: os métodos transparentes só devem conter IL verificável
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [CA2137: métodos transparentes devem conter apenas verificável IL](https://docs.microsoft.com/visualstudio/code-quality/ca2137-transparent-methods-must-contain-only-verifiable-il).

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

 Para ter certeza de que seu código contém apenas verificável MSIL, execute [Peverify.exe (ferramenta PEVerify)](http://msdn.microsoft.com/library/f4f46f9e-8d08-4e66-a94b-0c69c9b0bbfa) em seu assembly. Execução de PEVerify com o **/ transparente** opção que limita a saída para apenas não verificável métodos transparentes que causaria um erro. Se o / opção transparente não é usada, PEVerify também verifica os métodos críticos que podem conter código não verificável.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir uma violação dessa regra, marque o método com o <xref:System.Security.SecurityCriticalAttribute> ou <xref:System.Security.SecuritySafeCriticalAttribute> de atributo, ou remova o código não verificável.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 Não suprima um aviso nessa regra.

## <a name="example"></a>Exemplo
 O método neste exemplo usa um código não verificável e deve ser marcado com o <xref:System.Security.SecurityCriticalAttribute> ou <xref:System.Security.SecuritySafeCriticalAttribute> atributo.

 [!code-csharp[FxCop.Security.CA2137.TransparentMethodsMustBeVerifiable#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2137.transparentmethodsmustbeverifiable/cs/ca2137 - transparentmethodsmustbeverifiable.cs#1)]



