---
title: '&lt;Resumo&gt; (JavaScript) | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- summary JavaScript XML tag
- <summary> JavaScript XML tag
ms.assetid: 6540582d-bdb3-42ec-ad2f-c176783e6f9c
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: f6b4808112e746e30f0e40d4626f546c3f99b193
ms.sourcegitcommit: 71218ffc33da325cc1b886f69ff2ca50d44f5f33
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/09/2018
ms.locfileid: "48879012"
---
# <a name="ltsummarygt-javascript"></a>&lt;Resumo&gt; (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [documentação do Visual Studio 2017](/visualstudio/).  
  
Especifica a descrição de uma função ou método.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
<summary locid="descriptionID">description  
</summary>  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `locid`  
 Opcional. O identificador de informações de localização sobre o método ou função. O identificador é um membro ID ou ele corresponde ao `name` valor em um pacote de mensagem definido pelos metadados OpenAjax do atributo. O tipo de identificador depende do formato especificado na [ \<loc >](../ide/loc-javascript.md) elemento.  
  
 `description`  
 Opcional. Uma descrição da função ou método.  
  
## <a name="remarks"></a>Comentários  
 Os elementos usados para anotar as funções, que incluem [ \<resumo >](../ide/summary-javascript.md), [ \<param >](../ide/param-javascript.md), e [ \<retorna >](../ide/returns-javascript.md), deve ser colocado no corpo da função antes que as instruções.  
  
## <a name="example"></a>Exemplo  
 O código a seguir mostra como usar o `<summary>` elemento.  
  
```javascript  
function areaFunction(radiusParam)  
{  
    /// <summary>Determines the area of a circle when supplied a radius parameter.</summary>  
    /// <param name="radiusParam" type="Number">The radius of the circle.</param>  
    /// <returns type="Number">The area.</returns>  
    var areaVal;  
    areaVal = Math.PI * radiusParam * radiusParam;  
    return areaVal;  
}  
  
```  
  
## <a name="see-also"></a>Consulte também  
 [Comentários da documentação XML](../ide/xml-documentation-comments-javascript.md)



