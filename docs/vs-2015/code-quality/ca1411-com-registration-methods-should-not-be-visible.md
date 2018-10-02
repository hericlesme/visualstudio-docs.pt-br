---
title: 'CA1411: Os métodos de registro não devem estar visíveis | Microsoft Docs'
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
- CA1411
- ComRegistrationMethodsShouldNotBeVisible
helpviewer_keywords:
- ComRegistrationMethodsShouldNotBeVisible
- CA1411
ms.assetid: a59f96f1-1f38-4596-b656-947df5c55311
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 410531222f19632f6358bdbc320b95fe1254bafe
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/24/2018
ms.locfileid: "47587172"
---
# <a name="ca1411-com-registration-methods-should-not-be-visible"></a>CA1411: os métodos de registro COM não devem estar visíveis
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [CA1411: os métodos de registro não devem ser visíveis](https://docs.microsoft.com/visualstudio/code-quality/ca1411-com-registration-methods-should-not-be-visible).

|||
|-|-|
|NomeDoTipo|ComRegistrationMethodsShouldNotBeVisible|
|CheckId|CA1411|
|Categoria|Microsoft.Interoperability|
|Alteração Significativa|Quebra|

## <a name="cause"></a>Causa
 Um método que é marcado com o <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName> ou o <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName> atributo é visível externamente.

## <a name="rule-description"></a>Descrição da Regra
 Quando um assembly é registrado com o modelo de objeto de componente (COM), as entradas são adicionadas ao registro para cada tipo visível em COM no assembly. Métodos que são marcados com o <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute> e <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute> atributos são chamados durante os processos e cancelamento de registro, respectivamente, para executar o código de usuário que é específico para o registro/cancelamento do registro desses tipos. Esse código não deve ser chamado fora desses processos.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir uma violação dessa regra, altere a acessibilidade do método a ser `private` ou `internal` (`Friend` em [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]).

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 Não suprima um aviso nessa regra.

## <a name="example"></a>Exemplo
 O exemplo a seguir mostra dois métodos que violam a regra.

 [!code-csharp[FxCop.Interoperability.ComRegistration2#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.ComRegistration2/cs/FxCop.Interoperability.ComRegistration2.cs#1)]
 [!code-vb[FxCop.Interoperability.ComRegistration2#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.ComRegistration2/vb/FxCop.Interoperability.ComRegistration2.vb#1)]

## <a name="related-rules"></a>Regras relacionadas
 [CA1410: os métodos de registro COM devem ser correspondentes](../code-quality/ca1410-com-registration-methods-should-be-matched.md)

## <a name="see-also"></a>Consulte também
 <xref:System.Runtime.InteropServices.RegistrationServices?displayProperty=fullName> [Registrando Assemblies usando COM](http://msdn.microsoft.com/library/87925795-a3ae-4833-b138-125413478551) [Regasm.exe (ferramenta de registro de Assembly)](http://msdn.microsoft.com/library/e190e342-36ef-4651-a0b4-0e8c2c0281cb)



