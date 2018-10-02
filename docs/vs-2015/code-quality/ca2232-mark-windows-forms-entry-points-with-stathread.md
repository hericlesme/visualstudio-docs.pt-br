---
title: 'CA2232: Pontos de entrada de marca Windows Forms com STAThread | Microsoft Docs'
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
- MarkWindowsFormsEntryPointsWithStaThread
- CA2232
helpviewer_keywords:
- CA2232
- MarkWindowsFormsEntryPointsWithStaThread
ms.assetid: a3c95130-8e7f-4419-9fcd-b67d077e8efb
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 9345009b889b3c382ce0030c34b547a8fd337e0e
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/24/2018
ms.locfileid: "47586982"
---
# <a name="ca2232-mark-windows-forms-entry-points-with-stathread"></a>CA2232: marcar pontos de entrada dos Windows Forms com STAThread
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [CA2232: pontos de entrada de marca Windows Forms com STAThread](https://docs.microsoft.com/visualstudio/code-quality/ca2232-mark-windows-forms-entry-points-with-stathread).

|||
|-|-|
|NomeDoTipo|MarkWindowsFormsEntryPointsWithStaThread|
|CheckId|CA2232|
|Categoria|Microsoft.Usage|
|Alteração Significativa|Não separável|

## <a name="cause"></a>Causa
 Um assembly faz referência a <xref:System.Windows.Forms> namespace e seu ponto de entrada não está marcado com o <xref:System.STAThreadAttribute?displayProperty=fullName> atributo.

## <a name="rule-description"></a>Descrição da Regra
 <xref:System.STAThreadAttribute> indica que o modelo para o aplicativo de threading COM é single-threaded apartment. Esse atributo deve estar presente no ponto de entrada de qualquer aplicativo que use o Windows Forms; se ele for omitido, os componentes do Windows poderão não funcionar corretamente. Se o atributo não estiver presente, o aplicativo usa o modelo de multi-threaded apartment, o que não há suporte para Windows Forms.

> [!NOTE]
>  [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] projetos que usam a estrutura de aplicativo não é necessário marcar as **Main** método com STAThread. O [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] compilador faz isso automaticamente.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir uma violação dessa regra, adicione o <xref:System.STAThreadAttribute> de atributo para o ponto de entrada. Se o <xref:System.MTAThreadAttribute?displayProperty=fullName> atributo estiver presente, remova-o.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 É seguro suprimir um aviso nessa regra, se você estiver desenvolvendo para o .NET Compact Framework para o qual o <xref:System.STAThreadAttribute> atributo é desnecessário e não tem suporte.

## <a name="example"></a>Exemplo
 Os exemplos a seguir demonstram o uso correto do <xref:System.STAThreadAttribute>.

 [!code-csharp[FxCop.Usage.StaThread#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.StaThread/cs/FxCop.Usage.StaThread.cs#1)]
 [!code-vb[FxCop.Usage.StaThread#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.StaThread/vb/FxCop.Usage.StaThread.vb#1)]



