---
title: 'CA1301: evitar aceleradores duplicados'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1301
- AvoidDuplicateAccelerators
helpviewer_keywords:
- CA1301
- AvoidDuplicateAccelerators
ms.assetid: 20570a00-864b-459c-a1fa-a6e9db5f1001
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9d402bec5bf9c79b845f3bfa643c65fc07359a09
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31900113"
---
# <a name="ca1301-avoid-duplicate-accelerators"></a>CA1301: evitar aceleradores duplicados
|||
|-|-|
|NomeDoTipo|AvoidDuplicateAccelerators|
|CheckId|CA1301|
|Categoria|Microsoft.Globalization|
|Alteração Significativa|Não recentes|

## <a name="cause"></a>Causa
 Estende um tipo <xref:System.Windows.Forms.Control?displayProperty=fullName> e contém dois ou mais controles de nível superior que têm chaves de acesso idênticos são armazenadas em um arquivo de recurso.

## <a name="rule-description"></a>Descrição da Regra
 Uma tecla de acesso, também conhecida como acelerador, dá ao teclado acesso a um controle usando-se a tecla ALT. Quando vários controles têm teclas de acesso duplicadas, o comportamento da tecla de acesso não é bem definido. O usuário pode não ser capaz de acessar o controle desejado usando a chave de acesso e um controle diferente daquele que é destinado deve estar habilitado.

 A implementação atual desta regra ignora itens de menu. No entanto, os itens de menu no submenu mesmo não devem ter chaves de acesso idênticos.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir uma violação desta regra, definirá as chaves de acesso exclusivo para todos os controles.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 Não suprima um aviso nessa regra.

## <a name="example"></a>Exemplo
 O exemplo a seguir mostra um formulário mínimo que contém dois controles que têm chaves de acesso idênticos. As chaves são armazenadas em um arquivo de recurso, que não é exibido; No entanto, seus valores aparecerão no comentados out `checkBox.Text` linhas. O comportamento de aceleradores duplicados pode ser examinado trocando o `checkBox.Text` linhas com suas contrapartes comentados. No entanto, nesse caso, o exemplo não irá gerar um aviso da regra.

 [!code-csharp[FxCop.Globalization.AvoidDuplicateAccels#1](../code-quality/codesnippet/CSharp/ca1301-avoid-duplicate-accelerators_1.cs)]

## <a name="see-also"></a>Consulte também
 <xref:System.Resources.ResourceManager?displayProperty=fullName> [Recursos em aplicativos de área de trabalho](/dotnet/framework/resources/index)