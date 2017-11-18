---
title: "Método moveNext (Enumerator) (JavaScript) | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: moveNext
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: MoveNext method
ms.assetid: 59aa339b-f375-450a-8276-37896a55a824
caps.latest.revision: "16"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ab9b07a9a9c4640407cff0eaf21a6e8cd65dac11
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="movenext-method-enumerator-javascript"></a>Método moveNext (Enumerator) (JavaScript)
Move o item atual para o próximo item na coleção.  
  
> [!WARNING]
>  Esse objeto é compatível somente com o Internet Explorer.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
enumObj.moveNext( )   
```  
  
## <a name="remarks"></a>Comentários  
 Obrigatório *enumObj* referência é qualquer `Enumerator` objeto.  
  
 Se o enumerador está no final da coleção ou a coleção está vazia, o item atual está definido como indefinido.  
  
## <a name="example"></a>Exemplo  
 No exemplo a seguir, o **moveNext** método é usado para mover para a próxima unidade no `Drives` coleção:  
  
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
 [Método moveFirst (Enumerator)](../../javascript/reference/movefirst-method-enumerator-javascript.md)