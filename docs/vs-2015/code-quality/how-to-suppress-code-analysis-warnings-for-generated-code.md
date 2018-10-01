---
title: 'Como: suprimir avisos de análise de código para código gerado | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3a96434e-d419-43a7-81ba-95cccac835b8
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 81bb371a3e16236e22ab3a1fd4ac5ab431f61512
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47463258"
---
# <a name="how-to-suppress-code-analysis-warnings-for-generated-code"></a>Como suprimir avisos de análise do código para código gerenciado
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [como: suprimir avisos da análise de código para código gerado pelo](https://docs.microsoft.com/visualstudio/code-quality/how-to-suppress-code-analysis-warnings-for-generated-code).  
  
Compiladores de código gerenciado com frequência geram código que é adicionado a um projeto para facilitar o desenvolvimento rápido de código. Além disso, os desenvolvedores normalmente usam ferramentas de terceiros para ajudar a desenvolver aplicativos rapidamente. Essas ferramentas também geram código que é adicionado ao projeto.  
  
 Você talvez queira ver as violações de regra que detecta de análise de código no código gerado. No entanto, talvez você não queira vê-los se você não pode exibir e manter o código que contém a violação.  
  
 O **Suprimir resultados do código gerado** caixa de seleção na página de propriedades de análise de código de um projeto permite que você selecione se deseja ver avisos de análise de código do código gerado por uma ferramenta de terceiros.  
  
> [!NOTE]
>  Essa opção não suprime erros de análise de código e avisos do código gerado quando os erros e avisos que aparecem em formulários e modelos. Você pode exibir e manter o código-fonte para um formulário ou um modelo.  
  
### <a name="to-suppress-warnings-for-generated-code-in-a-project"></a>Para suprimir avisos para código gerado em um projeto  
  
1.  Clique com botão direito no projeto no Gerenciador de soluções e, em seguida, clique em **propriedades**.  
  
2.  Clique em **análise de código**.  
  
3.  Selecione o **Suprimir resultados do código gerado** caixa de seleção.



