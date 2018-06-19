---
title: Método moveFirst (Enumerator) (JavaScript) | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- moveFirst
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- MoveFirst method
ms.assetid: 96eedc66-7974-443c-b0cd-55373a7c0e59
caps.latest.revision: 18
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: af8c59194a5655730e8509b43533f699aeef51d2
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24638916"
---
# <a name="movefirst-method-enumerator-javascript"></a>Método moveFirst (Enumerator) (JavaScript)
Redefine o item atual na coleção para o primeiro item.  
  
> [!WARNING]
>  Esse objeto é compatível somente com o Internet Explorer.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
enumObj.moveFirst( )   
```  
  
## <a name="remarks"></a>Comentários  
 Obrigatório *enumObj* referência é qualquer `Enumerator` objeto.  
  
 Se não houver nenhum item na coleção, o item atual está definido como indefinido.  
  
## <a name="example"></a>Exemplo  
 No exemplo a seguir, o `moveFirst` método é usado para avaliar membros do `Drives` coleção desde o início da lista:  
  
```JavaScript  
function ShowDrives()  
{  
    var s = "";  
    var bytesPerGB = 1024 * 1024 * 1024;  
  
    var fso = new ActiveXObject("Scripting.FileSystemObject");  
    var e = new Enumerator(fso.Drives);  
  
    e.moveFirst();  
    while (e.atEnd() == false)  
    {  
        var drv = e.item();  
  
        s += drv.Path + " - ";  
  
        if (drv.IsReady)  
        {  
            var freeGB = drv.FreeSpace / bytesPerGB;  
            var totalGB = drv.TotalSize / bytesPerGB;  
  
            s += freeGB.toFixed(3) + " GB free of ";  
            s += totalGB.toFixed(3) + " GB";  
        }  
        else  
        {  
            s += "Not Ready";  
        }  
  
        s += "<br />";  
  
        e.moveNext();  
    }  
    return(s);  
}  
```  
  
## <a name="requirements"></a>Requisitos  
 Tem suporte nos seguintes modos de documentos: Quirks, padrões do Internet Explorer 6, padrões do Internet Explorer 7, padrões do Internet Explorer 8, padrões do Internet Explorer 9 e padrões do Internet Explorer 10. Sem suporte nos aplicativos [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)]. Consulte [Informações sobre versão](../../javascript/reference/javascript-version-information.md).  
  
 **Aplica-se a**: [objeto enumerador](../../javascript/reference/enumerator-object-javascript.md)  
  
## <a name="see-also"></a>Consulte também  
 [Método atEnd (Enumerator)](../../javascript/reference/atend-method-enumerator-javascript.md)   
 [Método item (Enumerator)](../../javascript/reference/item-method-enumerator-javascript.md)   
 [Método moveNext (Enumerator)](../../javascript/reference/movenext-method-enumerator-javascript.md)