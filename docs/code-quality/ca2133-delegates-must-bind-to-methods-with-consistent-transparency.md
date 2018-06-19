---
title: 'CA2133: os representantes devem ser associados a métodos com transparência consistente'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2133
ms.assetid: a09672e2-63cb-4abd-9e8f-dff515e101ce
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 389de424c3d9e2cd0e12431e857983b267213f9c
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31920913"
---
# <a name="ca2133-delegates-must-bind-to-methods-with-consistent-transparency"></a>CA2133: os representantes devem ser associados a métodos com transparência consistente
|||
|-|-|
|NomeDoTipo|DelegatesMustBindWithConsistentTransparency|
|CheckId|CA2133|
|Categoria|Microsoft.Security|
|Alteração Significativa|Quebra|

> [!NOTE]
>  Esse aviso é aplicado somente ao código que está executando o CoreCLR (a versão do CLR que é específico para aplicativos Web do Silverlight).

## <a name="cause"></a>Causa
 Esse aviso é acionado em um método que associa um delegado que é marcado com o <xref:System.Security.SecurityCriticalAttribute> para um método que é transparente ou que está marcado com o <xref:System.Security.SecuritySafeCriticalAttribute>. O aviso também é acionado em um método que associa um representante transparente ou de segurança crítica a um método crítico.

## <a name="rule-description"></a>Descrição da Regra
 Tipos delegados e os métodos que eles se vincular a devem ter transparência consistente. Delegados transparentes e crítico para segurança só podem vincular a outros métodos de crítico para segurança ou transparentes. Da mesma forma, críticos delegados só podem vincular para métodos críticos. Essas regras de associação Certifique-se de que somente o código que pode invocar um método por meio de um representante pode ter também chamado o mesmo método diretamente. Por exemplo, regras de associação impedir que o código transparente de chamar código crítico diretamente por meio de um delegado transparente.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir uma violação desse aviso, altere a transparência do representante ou do método que ele é ligado para que a transparência dos dois são equivalentes.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 Não suprima um aviso nessa regra.

### <a name="code"></a>Código
 [!code-csharp[FxCop.Security.CA2133.DelegatesMustBindWithConsistentTransparency#1](../code-quality/codesnippet/CSharp/ca2133-delegates-must-bind-to-methods-with-consistent-transparency_1.cs)]