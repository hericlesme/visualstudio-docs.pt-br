---
title: 'CA1409: Os tipos visíveis Com devem ser criáveis | Microsoft Docs'
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
- ComVisibleTypesShouldBeCreatable
- CA1409
helpviewer_keywords:
- ComVisibleTypesShouldBeCreatable
- CA1409
ms.assetid: 9f59569b-de15-4a38-b7cb-cff152972243
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: a9b946fc68774d33bc17a37dafc5366d6532f745
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/24/2018
ms.locfileid: "47587257"
---
# <a name="ca1409-com-visible-types-should-be-creatable"></a>CA1409: os tipos visíveis Com devem ser criáveis
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [CA1409: tipos visíveis Com devem ser criáveis](https://docs.microsoft.com/visualstudio/code-quality/ca1409-com-visible-types-should-be-creatable).

|||
|-|-|
|NomeDoTipo|ComVisibleTypesShouldBeCreatable|
|CheckId|CA1409|
|Categoria|Microsoft.Interoperability|
|Alteração Significativa|Não são significativas|

## <a name="cause"></a>Causa
 Um tipo de referência marcado especificamente como visível para COM Component Object Model () contém um construtor parametrizado público, mas não contém um construtor público padrão (sem parâmetros).

## <a name="rule-description"></a>Descrição da Regra
 Um tipo sem um construtor padrão público não pode ser criado por clientes COM. No entanto, o tipo ainda pode ser acessado por clientes COM se houver outros meios criar o tipo e passá-lo para o cliente (por exemplo, por meio de obter o valor retornado de uma chamada de método).

 A regra sempre ignora os tipos que são derivados de <xref:System.Delegate?displayProperty=fullName>.

 Por padrão, a seguir é visível no COM: assemblies, tipos públicos, membros de instância pública em tipos públicos e todos os membros de tipos de valor público.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir uma violação dessa regra, adicione um construtor padrão público ou remova o <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> do tipo.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 É seguro suprimir um aviso nessa regra, se outros modos são fornecidos para criar e passar o objeto para o cliente COM.

## <a name="related-rules"></a>Regras relacionadas
 [CA1017: marcar assemblies com ComVisibleAttribute](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)

## <a name="see-also"></a>Consulte também
 [Qualificando tipos do .NET para interoperação](http://msdn.microsoft.com/library/4b8afb52-fb8d-4e65-b47c-fd82956a3cdd) [interoperação com código não gerenciado](http://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)



