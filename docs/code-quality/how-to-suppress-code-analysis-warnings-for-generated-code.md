---
title: "Como: suprimir avisos da análise de código para código gerado | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3a96434e-d419-43a7-81ba-95cccac835b8
caps.latest.revision: "5"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 24b94c0c4ce6031876f5ad26ce01a22299f7056a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-suppress-code-analysis-warnings-for-generated-code"></a>Como suprimir avisos de análise do código para código gerenciado
Compiladores de código gerenciado geralmente geram código que é adicionado a um projeto para facilitar o desenvolvimento rápido de código. Além disso, os desenvolvedores geralmente usam ferramentas de terceiros para ajudar a desenvolver aplicativos rapidamente. Essas ferramentas também geram código que é adicionado ao projeto.  
  
 Deseja ver as violações de regra da análise de código descobre no código gerado. No entanto, não deseja vê-los se você não pode exibir e manter o código que contém a violação.  
  
 O **Suprimir resultados do código gerado** caixa de seleção na página de propriedades de análise de código de um projeto permite que você selecione se você deseja ver avisos de análise de código do código gerado por uma ferramenta de terceiros.  
  
> [!NOTE]
>  Essa opção suprime erros de análise de código e avisos do código gerado quando os erros e avisos aparecem em formulários e modelos. Você pode exibir e manter o código-fonte para um formulário ou um modelo.  
  
### <a name="to-suppress-warnings-for-generated-code-in-a-project"></a>Para suprimir avisos para código gerenciado em um projeto  
  
1.  Clique com botão direito no projeto no Gerenciador de soluções e, em seguida, clique em **propriedades**.  
  
2.  Clique em **de análise de código**.  
  
3.  Selecione o **Suprimir resultados do código gerado** caixa de seleção.