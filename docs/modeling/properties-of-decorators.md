---
title: Propriedades de decoradores | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Domain-Specific Language, decorators
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 7f5bd86a9fe8d67111886e7578187747b1ea3ec8
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/13/2018
---
# <a name="properties-of-decorators"></a>Propriedades de decoradores
Os decoradores são ícones, texto ou expandir/recolher divisas que podem aparecer em conectores ou formas no diagrama. As tabelas a seguir mostram as propriedades para os três tipos de decorador. Algumas das propriedades aparecem somente em decoradores forma ou somente em decoradores de conector.  
  
 Para obter mais informações, consulte [como definir uma linguagem específica do domínio](../modeling/how-to-define-a-domain-specific-language.md). Para obter mais informações sobre como usar essas propriedades, consulte [personalizar e estender uma linguagem específica do domínio](../modeling/customizing-and-extending-a-domain-specific-language.md).  
  
## <a name="expandcollapse-decorator"></a>Expandir/recolher decorador  
  
|Propriedade|Descrição|Padrão|  
|--------------|-----------------|-------------|  
|DisplayName|O nome do decorador que será exibido no designer de gerado.|Expanda recolher decorador|  
|Nome|O nome do decorador.|ExpandCollapseDecorator|  
|Observações|Anotações informais que estão associadas este decorador.|\<Nenhum >|  
|HorizontalOffset|O deslocamento horizontal, em relação à posição padrão de decorador, em polegadas. (Em formas somente.)|0|  
|VerticalOffset|O deslocamento vertical, em relação à posição padrão de decorador, em polegadas. (Em formas somente.)|0|  
|OffsetFromLine|O deslocamento do decorador de linha, em relação a sua posição padrão, em polegadas. (Nos conectores somente.)|0|  
|OffsetFromShape|O deslocamento do decorador de forma, em relação a sua posição padrão, em polegadas. (Nos conectores somente.)|0|  
|Posição|A posição padrão do decorador.|SourceTop|  
  
## <a name="icon-decorator"></a>Ícone decorador  
  
|Propriedade|Descrição|Padrão|  
|--------------|-----------------|-------------|  
|DefaultIcon|O caminho do arquivo de ícone ou imagem a ser exibida.|\<Nenhum >|  
|DisplayName|O nome do decorador para ser exibido no designer de gerado.|Ícone decorador|  
|Nome|O nome do decorador.|IconDecorator|  
|Observações|Anotações informais que estão associadas com o decorador.|\<Nenhum >|  
|HorizontalOffset|O deslocamento horizontal, em relação à posição padrão de decorador, em polegadas. (Em formas somente.)|0|  
|VerticalOffset|O deslocamento vertical, em relação à posição padrão de decorador, em polegadas. (Em formas somente.)|0|  
|OffsetFromLine|O deslocamento do decorador de linha, em relação a sua posição padrão, em polegadas. (Nos conectores somente.)|0|  
|OffsetFromShape|O deslocamento do decorador de forma, em relação a sua posição padrão, em polegadas. (Nos conectores somente.)|0|  
|Posição|A posição padrão do decorador.|SourceTop|  
  
## <a name="textdecorator"></a>TextDecorator  
  
|Propriedade|Descrição|Padrão|  
|--------------|-----------------|-------------|  
|DefaultText|O texto padrão a ser exibido.|Rotular|  
|DisplayName|O nome do decorador para ser exibido no designer de gerado.|Rotular|  
|FontSize|O tamanho da fonte para o texto que é exibido no decorador.|8|  
|FontStyle|O estilo da fonte para o texto que é exibido no decorador.|Normal|  
|Nome|O nome do decorador.|Rotular|  
|Observações|Anotações informais que estão associadas com o decorador.|\<Nenhum >|  
|HorizontalOffset|O deslocamento horizontal, em relação à posição padrão de decorador, em polegadas. (Em formas somente.)|0|  
|VerticalOffset|O deslocamento vertical, em relação à posição padrão de decorador, em polegadas. (Em formas somente.)|0|  
|OffsetFromLine|O deslocamento do decorador de linha, em relação a sua posição padrão, em polegadas. (Nos conectores somente.)|0|  
|OffsetFromShape|O deslocamento do decorador de forma, em relação a sua posição padrão, em polegadas. (Nos conectores somente.)|0|  
|Posição|A posição padrão do decorador.|TargetBottom|  
  
## <a name="see-also"></a>Consulte também  
 [Glossário de ferramentas de linguagem específica de domínio](http://msdn.microsoft.com/en-us/ca5e84cb-a315-465c-be24-76aa3df276aa)