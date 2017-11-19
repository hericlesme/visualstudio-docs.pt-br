---
title: "Como: avalie uma expressão XPath | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 159ba4ef-75e4-4ac8-80dc-e064e0bec345
caps.latest.revision: "2"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: d549afb96465590a21e516f649d860f23f4056f3
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-evaluate-an-xpath-expression"></a>Como: Avalie uma expressão XPath
Você pode avaliar expressões XPath com o **QuickWatch** caixa de diálogo. A expressão XPath deve ser válido de acordo com a recomendação XPath 1,0 W3C. O contexto XSLT atual — ou seja, o `self::node()` nó o **locais** janela — fornece o contexto de avaliação da expressão XPath.  
  
 A lista a seguir descreve quais funções são suportadas para avaliar uma expressão XPath:  
  
-   As funções internas XPath são suportadas.  
  
-   As funções internas XSLT não são suportadas.  
  
-   As funções definidas pelo usuário não são suportadas.  
  
> [!NOTE]
>  O procedimento a seguir usa os arquivos de belowAvg.xsl e books.xml o [passo a passo: depurar uma folha de estilos XSLT](../xml-tools/walkthrough-debug-an-xslt-style-sheet.md) tópico.  
  
### <a name="to-evaluate-an-xpath-expression"></a>Para avaliar uma expressão XPath  
  
1.  Inserir um ponto de interrupção na tag de início de `xsl:if` .  
  
2.  Clique o **depurar XSL** na barra de ferramentas do Editor de XML.  
  
     Inicia e as quebras do depurador na marca `xsl:if` .  
  
3.  Clique com botão direito e selecione **QuickWatch**.  
  
     O **QuickWatch** caixa de diálogo é exibida.  
  
4.  Digite `./price/text()` no **expressão** campo o **QuickWatch** caixa de diálogo e clique em **reavaliar**.  
  
     O preço do nó atual do catálogo aparece no **valor** caixa.  
  
5.  Altere a expressão XPath para `./price/text() < $bookAverage` e clique em **reavaliar**.  
  
     O **valor** caixa mostra que a expressão XPath é avaliada como `true`.  
  
## <a name="see-also"></a>Consulte também  
 [Depuração de XSLT](../xml-tools/debugging-xslt.md)