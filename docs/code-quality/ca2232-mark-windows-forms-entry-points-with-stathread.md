---
title: 'CA2232: marcar pontos de entrada dos Windows Forms com STAThread'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- MarkWindowsFormsEntryPointsWithStaThread
- CA2232
helpviewer_keywords:
- CA2232
- MarkWindowsFormsEntryPointsWithStaThread
ms.assetid: a3c95130-8e7f-4419-9fcd-b67d077e8efb
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c5a1ba8eae4cc98242581d1ea525648b5e6b434b
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31919273"
---
# <a name="ca2232-mark-windows-forms-entry-points-with-stathread"></a>CA2232: marcar pontos de entrada dos Windows Forms com STAThread
|||
|-|-|
|NomeDoTipo|MarkWindowsFormsEntryPointsWithStaThread|
|CheckId|CA2232|
|Categoria|Microsoft.Usage|
|Alteração Significativa|Não separáveis|

## <a name="cause"></a>Causa
 Faz referência a um assembly de <xref:System.Windows.Forms> namespace e seu ponto de entrada não está marcado com o <xref:System.STAThreadAttribute?displayProperty=fullName> atributo.

## <a name="rule-description"></a>Descrição da Regra
 <xref:System.STAThreadAttribute> indica que o modelo para o aplicativo de threading COM single-threaded apartment. Esse atributo deve estar presente no ponto de entrada de qualquer aplicativo que use o Windows Forms; se ele for omitido, os componentes do Windows poderão não funcionar corretamente. Se o atributo não estiver presente, o aplicativo usa o modelo de multi-threaded apartment, e não há suporte para formulários do Windows.

> [!NOTE]
>  [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] projetos que usam a estrutura de aplicativo não é necessário marcar a **principal** método com STAThread. O [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] compilador faz isso automaticamente.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir uma violação desta regra, adicione o <xref:System.STAThreadAttribute> de atributo para o ponto de entrada. Se o <xref:System.MTAThreadAttribute?displayProperty=fullName> atributo estiver presente, remova-o.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 É seguro suprimir um aviso dessa regra, se você estiver desenvolvendo para o .NET Compact Framework para o qual o <xref:System.STAThreadAttribute> atributo é desnecessário e não tem suporte.

## <a name="example"></a>Exemplo
 Os exemplos a seguir demonstram o uso correto de <xref:System.STAThreadAttribute>.

 [!code-csharp[FxCop.Usage.StaThread#1](../code-quality/codesnippet/CSharp/ca2232-mark-windows-forms-entry-points-with-stathread_1.cs)]
 [!code-vb[FxCop.Usage.StaThread#1](../code-quality/codesnippet/VisualBasic/ca2232-mark-windows-forms-entry-points-with-stathread_1.vb)]