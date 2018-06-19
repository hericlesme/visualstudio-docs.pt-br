---
title: 'CA1300: especificar MessageBoxOptions'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- SpecifyMessageBoxOptions
- CA1300
helpviewer_keywords:
- SpecifyMessageBoxOptions
- CA1300
ms.assetid: 9357a724-026e-4a3d-a03a-f14635064ec6
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a8469deaf13c12200aec6a68eed9e78c4e9b8543
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31896984"
---
# <a name="ca1300-specify-messageboxoptions"></a>CA1300: especificar MessageBoxOptions
|||
|-|-|
|NomeDoTipo|SpecifyMessageBoxOptions|
|CheckId|CA1300|
|Categoria|Microsoft.Globalization|
|Alteração Significativa|Não recentes|

## <a name="cause"></a>Causa
 Um método chama uma sobrecarga de <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=fullName> método que não têm um <xref:System.Windows.Forms.MessageBoxOptions?displayProperty=fullName> argumento.

## <a name="rule-description"></a>Descrição da Regra
 Para exibir uma caixa de mensagem corretamente para culturas que usam uma ordem de leitura da direita para esquerda, o <xref:System.Windows.Forms.MessageBoxOptions> e <xref:System.Windows.Forms.MessageBoxOptions> membros a <xref:System.Windows.Forms.MessageBoxOptions> enumeração deve ser passada para o <xref:System.Windows.Forms.MessageBox.Show%2A> método. Examine o <xref:System.Windows.Forms.Control.RightToLeft%2A?displayProperty=fullName> propriedade do recipiente de controle para determinar se deve usar uma ordem de leitura da direita para esquerda.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir uma violação desta regra, chame uma sobrecarga de <xref:System.Windows.Forms.MessageBox.Show%2A> método que utiliza um <xref:System.Windows.Forms.MessageBoxOptions> argumento.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 É seguro suprimir um aviso dessa regra quando a biblioteca de código não será localizada para uma cultura que usa uma ordem de leitura da direita para esquerda.

## <a name="example"></a>Exemplo
 O exemplo a seguir mostra um método que exibe uma caixa de mensagem que tem opções que são apropriadas para a ordem de leitura da cultura. Um arquivo de recurso, que não é exibido, é necessário para criar o exemplo. Siga os comentários no exemplo para compilar o exemplo sem um arquivo de recurso e testar o recurso da direita para esquerda.

 [!code-vb[FxCop.Globalization.SpecifyMBOptions#1](../code-quality/codesnippet/VisualBasic/ca1300-specify-messageboxoptions_1.vb)]
 [!code-csharp[FxCop.Globalization.SpecifyMBOptions#1](../code-quality/codesnippet/CSharp/ca1300-specify-messageboxoptions_1.cs)]

## <a name="see-also"></a>Consulte também
 <xref:System.Resources.ResourceManager?displayProperty=fullName> [Recursos em aplicativos de área de trabalho](/dotnet/framework/resources/index)