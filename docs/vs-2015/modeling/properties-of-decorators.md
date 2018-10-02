---
title: Propriedades de decoradores | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Domain-Specific Language, decorators
ms.assetid: f6322fe5-dc08-4d32-a6b3-0bd18879136d
caps.latest.revision: 25
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: dc111cf868d2136a4d274889d96d50d2c9500a9a
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47475179"
---
# <a name="properties-of-decorators"></a>Propriedades de decoradores
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [propriedades de decoradores](https://docs.microsoft.com/visualstudio/modeling/properties-of-decorators).  
  
Os decoradores são ícones, texto ou expandir/recolher divisas que podem aparecer em formas ou conectores no diagrama. As tabelas a seguir mostram as propriedades para os três tipos de decorador. Algumas das propriedades aparecem somente em decoradores de forma ou somente em decoradores do conector.  
  
 Para obter mais informações, consulte [como definir uma linguagem específica do domínio](../modeling/how-to-define-a-domain-specific-language.md). Para obter mais informações sobre como usar essas propriedades, consulte [personalizando e estendendo uma linguagem específica do domínio](../modeling/customizing-and-extending-a-domain-specific-language.md).  
  
## <a name="expandcollapse-decorator"></a>Expandir/recolher decorador  
  
|Propriedade|Descrição|Padrão|  
|--------------|-----------------|-------------|  
|DisplayName|O nome do decorador que será exibido no designer gerado.|Expandir recolher decorador|  
|Nome|O nome do decorador.|ExpandCollapseDecorator|  
|Observações|Observações informais associadas esse decorador.|\<Nenhum >|  
|HorizontalOffset|O deslocamento horizontal, em relação à posição padrão do decorador, em polegadas. (Nas formas somente.)|0|  
|VerticalOffset|O deslocamento vertical, em relação à posição padrão do decorador, em polegadas. (Nas formas somente.)|0|  
|OffsetFromLine|O deslocamento do decorador da linha, em relação à sua posição padrão, em polegadas. (Nos conectores somente.)|0|  
|OffsetFromShape|O deslocamento do decorador da forma, relativo à sua posição padrão, em polegadas. (Nos conectores somente.)|0|  
|Posição|A posição padrão do decorador.|SourceTop|  
  
## <a name="icon-decorator"></a>Ícone de decorador  
  
|Propriedade|Descrição|Padrão|  
|--------------|-----------------|-------------|  
|DefaultIcon|O caminho do arquivo de imagem ou ícone a ser exibido.|\<Nenhum >|  
|DisplayName|O nome do decorador a ser exibido no designer gerado.|Ícone de decorador|  
|Nome|O nome do decorador.|IconDecorator|  
|Observações|Observações informais que estão associadas com o decorador.|\<Nenhum >|  
|HorizontalOffset|O deslocamento horizontal, em relação à posição padrão do decorador, em polegadas. (Nas formas somente.)|0|  
|VerticalOffset|O deslocamento vertical, em relação à posição padrão do decorador, em polegadas. (Nas formas somente.)|0|  
|OffsetFromLine|O deslocamento do decorador da linha, em relação à sua posição padrão, em polegadas. (Nos conectores somente.)|0|  
|OffsetFromShape|O deslocamento do decorador da forma, relativo à sua posição padrão, em polegadas. (Nos conectores somente.)|0|  
|Posição|A posição padrão do decorador.|SourceTop|  
  
## <a name="textdecorator"></a>TextDecorator  
  
|Propriedade|Descrição|Padrão|  
|--------------|-----------------|-------------|  
|DefaultText|O texto padrão a ser exibido.|Rotular|  
|DisplayName|O nome do decorador a ser exibido no designer gerado.|Rotular|  
|FontSize|O tamanho da fonte para o texto que é exibido no decorador.|8|  
|fontStyle|O estilo da fonte para o texto que é exibido no decorador.|Normal|  
|Nome|O nome do decorador.|Rotular|  
|Observações|Observações informais que estão associadas com o decorador.|\<Nenhum >|  
|HorizontalOffset|O deslocamento horizontal, em relação à posição padrão do decorador, em polegadas. (Nas formas somente.)|0|  
|VerticalOffset|O deslocamento vertical, em relação à posição padrão do decorador, em polegadas. (Nas formas somente.)|0|  
|OffsetFromLine|O deslocamento do decorador da linha, em relação à sua posição padrão, em polegadas. (Nos conectores somente.)|0|  
|OffsetFromShape|O deslocamento do decorador da forma, relativo à sua posição padrão, em polegadas. (Nos conectores somente.)|0|  
|Posição|A posição padrão do decorador.|TargetBottom|  
  
## <a name="see-also"></a>Consulte também  
 [Glossário de ferramentas de linguagem específica do domínio](http://msdn.microsoft.com/en-us/ca5e84cb-a315-465c-be24-76aa3df276aa)



