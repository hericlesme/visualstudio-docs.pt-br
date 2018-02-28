---
title: Objeto enumerator (JavaScript) | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- Enumerator
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Enumerator object
ms.assetid: 63f03c21-d58c-47db-a728-4d8d88b0a422
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 50b1ebfb6e24ed734f008b3c05f10a1687c4aff5
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="enumerator-object-javascript"></a>Objeto Enumerator (JavaScript)
Habilita a enumeração de itens nas coleções.  
  
> [!WARNING]
>  Esse objeto é suportado no Internet Explorer apenas, não no [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] aplicativos.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
enumObj = new Enumerator([collection])   
```  
  
## <a name="parameters"></a>Parâmetros  
 `enumObj`  
 Obrigatório. O nome da variável à qual o objeto `Enumerator` é atribuído.  
  
 `collection`  
 Opcional. Qualquer objeto da coleção.  
  
## <a name="remarks"></a>Comentários  
 Coleções são diferentes de matrizes, os membros de uma coleção não são diretamente acessíveis. Em vez de usar índices, como você faria com matrizes, você pode mover o ponteiro do item atual apenas para o primeiro ou o próximo elemento de uma coleção.  
  
 O `Enumerator` objeto fornece uma maneira de acessar qualquer membro de uma coleção e se comporta da mesma forma que o `For...Each` instrução no VBScript.  
  
## <a name="example"></a>Exemplo  
 O código a seguir mostra o uso do `Enumerator` objeto:  
  
```JavaScript  
var bytesPerGB = 1024 * 1024 * 1024;  
  
var fso = new ActiveXObject("Scripting.FileSystemObject");  
  
document.write(fso.Drives);  
var e = new Enumerator(fso.Drives);  
  
var driveString = "";  
  
e.moveFirst();  
while (e.atEnd() == false)  
{  
    var drv = e.item();  
  
    driveString += drv.Path + " - ";  
  
    if (drv.IsReady){  
        var freeGB = drv.FreeSpace / bytesPerGB;  
        var totalGB = drv.TotalSize / bytesPerGB;  
  
        driveString += freeGB.toFixed(3) + " GB free of ";  
        driveString += totalGB.toFixed(3) + " GB";  
    }  
    else{  
        driveString += "Not Ready";  
    }  
  
    driveString += "<br />";;  
  
    e.moveNext();  
}  
document.write(driveString);  
  
// Output: <drive information  
  
```  
  
## <a name="properties"></a>Propriedades  
 O `Enumerator` objeto não tem propriedades.  
  
## <a name="methods"></a>Métodos  
 [Método atEnd](../../javascript/reference/atend-method-enumerator-javascript.md) &#124; [método item](../../javascript/reference/item-method-enumerator-javascript.md) &#124; [método moveFirst](../../javascript/reference/movefirst-method-enumerator-javascript.md) &#124; [método moveNext](../../javascript/reference/movenext-method-enumerator-javascript.md)  
  
## <a name="requirements"></a>Requisitos  
 Tem suporte nos seguintes modos de documentos: Quirks, padrões do Internet Explorer 6, padrões do Internet Explorer 7, padrões do Internet Explorer 8, padrões do Internet Explorer 9 e padrões do Internet Explorer 10. Sem suporte nos aplicativos [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)]. Consulte [Informações sobre versão](../../javascript/reference/javascript-version-information.md).  
  
## <a name="see-also"></a>Consulte também  
 [Objeto Boolean](../../javascript/reference/boolean-object-javascript.md)