---
title: Propriedades de decoradores | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.topic: article
helpviewer_keywords:
- Domain-Specific Language, decorators
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 95338b26019a2faf2afc2eb6be019ac33d6ece3c
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/09/2018
---
# <a name="properties-of-decorators"></a>Propriedades de decoradores
Os decoradores são ícones, texto ou expandir/recolher divisas que podem aparecer em conectores ou formas no diagrama. As tabelas a seguir mostram as propriedades para os três tipos de decorador. Algumas das propriedades aparecem somente em decoradores forma ou somente em decoradores de conector.  
  
 Para obter mais informações, consulte [como definir uma linguagem específica do domínio](../modeling/how-to-define-a-domain-specific-language.md). Para obter mais informações sobre como usar essas propriedades, consulte [personalizar e estender uma linguagem específica do domínio](../modeling/customizing-and-extending-a-domain-specific-language.md).  
  
## <a name="expandcollapse-decorator"></a>Expandir/recolher decorador  
  
|Propriedade|Descrição|Padrão|  
|--------------|-----------------|-------------|  
|DisplayName|O nome do decorador que será exibido no designer de gerado.|Expanda recolher decorador|  
|Nome|O nome do decorador.|ExpandCollapseDecorator|  
|Observações|Anotações informais que estão associadas este decorador.|\<none>|  
|HorizontalOffset|O deslocamento horizontal, em relação à posição padrão de decorador, em polegadas. (Em formas somente.)|0|  
|VerticalOffset|O deslocamento vertical, em relação à posição padrão de decorador, em polegadas. (Em formas somente.)|0|  
|OffsetFromLine|O deslocamento do decorador de linha, em relação a sua posição padrão, em polegadas. (Nos conectores somente.)|0|  
|OffsetFromShape|O deslocamento do decorador de forma, em relação a sua posição padrão, em polegadas. (Nos conectores somente.)|0|  
|Posição|A posição padrão do decorador.|SourceTop|  
  
## <a name="icon-decorator"></a>Ícone decorador  
  
|Propriedade|Descrição|Padrão|  
|--------------|-----------------|-------------|  
|DefaultIcon|O caminho do arquivo de ícone ou imagem a ser exibida.|\<none>|  
|DisplayName|O nome do decorador para ser exibido no designer de gerado.|Ícone decorador|  
|Nome|O nome do decorador.|IconDecorator|  
|Observações|Anotações informais que estão associadas com o decorador.|\<none>|  
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
|Observações|Anotações informais que estão associadas com o decorador.|\<none>|  
|HorizontalOffset|O deslocamento horizontal, em relação à posição padrão de decorador, em polegadas. (Em formas somente.)|0|  
|VerticalOffset|O deslocamento vertical, em relação à posição padrão de decorador, em polegadas. (Em formas somente.)|0|  
|OffsetFromLine|O deslocamento do decorador de linha, em relação a sua posição padrão, em polegadas. (Nos conectores somente.)|0|  
|OffsetFromShape|O deslocamento do decorador de forma, em relação a sua posição padrão, em polegadas. (Nos conectores somente.)|0|  
|Posição|A posição padrão do decorador.|TargetBottom|  
  
## <a name="see-also"></a>Consulte também  
 [Glossário de ferramentas de linguagem específica de domínio](http://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)