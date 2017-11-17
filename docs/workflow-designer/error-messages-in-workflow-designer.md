---
title: Mensagens de erro no Designer de fluxo de trabalho | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- WFDErrorMessages.UI
- System.Activities.Presentation.ErrorActivity.UI
- System.Activities.Presentation.View.ErrorView.UI
ms.assetid: 4d8bbc2e-34fc-477f-9140-4adfd70c34a0
caps.latest.revision: "5"
author: ErikRe
ms.author: erikre
manager: erikre
ms.openlocfilehash: ef4e1883fd6f72ab0937f4b6502c6bad086eb68f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="error-messages-in-workflow-designer"></a>Mensagens de erro em Designer de Fluxo de Trabalho
Este tópico descreve os tipos de mensagens de erro que podem ser encontrados ao trabalhar com [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)].  
  
## <a name="situations-in-which-errors-in-the-workflow-designer-occur"></a>Situações em que os erros no criador de Fluxo de Trabalho ocorrem  
 Erros em [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] ocorrem nas seguintes situações:  
  
1.  Há um erro em uma expressão.  
  
2.  As restrições de validação de uma atividade não foram satisfeitas.  
  
3.  Há erros no arquivo XAML que fazem com que uma atividade a falha carregue.  
  
4.  Há erros no arquivo XAML que fazem com que o fluxo de trabalho a falha carregue.  
  
 As expressões inválidos e restrições insatisfeitas de validação não fazem com que o fluxo de trabalho a falha compile. Compilar seu fluxo de trabalho é bem-sucedido, mas <xref:System.Activities.InvalidWorkflowException> é lançada pelo tempo de execução. Se há erros no arquivo XAML, a compilação falhará.  
  
 Dentro de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], quando um fluxo de trabalho é carregado, os erros são exibidos no **lista de erros**. Para navegar para a atividade que é a origem do erro, clique duas vezes o erro a **lista de erros**.  
  
### <a name="expression-errors"></a>Erros de expressão  
 Uma expressão é inválido denotada por um círculo vermelho com um ponto de exclamação branco ao lado da expressão. Passa sobre este ícone exibe uma dica de ferramenta que descreve a fonte do erro. Dentro de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], clique na expressão para exibir a linha que enfatiza a fonte do erro. Passa sobre o texto alinhado exibe uma dica de ferramenta que descreve a fonte do erro.  
  
### <a name="activity-validation-errors"></a>Erros de validação de atividades  
 Quando as restrições de validação de uma atividade não forem atendidas, um círculo vermelho com um ponto de exclamação branco aparece no canto superior direito da atividade. Passa sobre este ícone exibe uma dica de ferramenta que descreve a fonte do erro.  
  
### <a name="xaml-load-errors"></a>Erros de carregamento XAML  
 Quando uma atividade Falha ao carregar, aparece uma caixa vermelha com o texto "atividade não pode ser carregada devido a erros em XAML". Isso normalmente ocorre quando o tipo da atividade não pode ser resolvido. A atividade inválido pode ser excluído no designer selecionando a caixa vermelha e excluindo a.  
  
### <a name="workflow-load-errors"></a>Erros de carregamento de fluxo de trabalho  
 Quando um fluxo de trabalho não for carregado, o texto "Problemas de Designer de fluxo de trabalho encontrado com o documento" aparece na superfície do designer, junto com as informações de exceção que causou a falha do fluxo de trabalho carregar. Isso geralmente ocorre quando o arquivo XAML não pode ser analisado.