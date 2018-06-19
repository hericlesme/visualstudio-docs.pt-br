---
title: Manipular eventos do Windows Runtime em JavaScript | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- javascript
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- JavaScript, Windows Runtime events
- Windows Runtime events [JavaScript]
ms.assetid: d9436aff-2c30-4846-b8df-eaa3e63fd75c
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e963472ee51f2439b50807a49425dcd7f6d8443a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24571426"
---
# <a name="handling-windows-runtime-events-in-javascript"></a>Manipular eventos do Windows Runtime em JavaScript
Eventos do Tempo de Execução do Windows não são representados da mesma maneira que em JavaScript, pois eles estão em C++ ou .NET Framework. Eles não são propriedades de classe, mas, em vez disso, são representados como identificadores de cadeia de caracteres enviados para os métodos `addEventListener` e `removeEventListener` da classe. Por exemplo, você pode adicionar um manipulador de eventos para o evento [Geolocator.PositionChanged](http://msdn.microsoft.com/library/windows/apps/xaml/windows.devices.geolocation.geolocator.positionchanged.aspx) passando a cadeia de caracteres "positionchanged" para o método `Geolocator.addEventListener`:  
  
```JavaScript  
var locator =  new Windows.Devices.Geolocation.Geolocator();  
locator.addEventListener(  
    "positionchanged",   
     function (ev) {  
        console.log("Got event");  
    });  
```  
  
 Também é possível definir a propriedade `locator.onpositionchanged`.  
  
```  
locator.onpositionchanged =    
    function (ev) {  
        console.log("Got event");  
    };  
```  
  
 Em JavaScript, os argumentos do Tempo de Execução do Windows são representados como um único objeto de evento. No exemplo a seguir de um método de manipulador de evento, o parâmetro `ev` é um objeto que contém o remetente (a propriedade de destino) e outros argumentos de evento. Os argumentos de evento são aqueles documentados para cada evento.  
  
```JavaScript  
function (ev) {  
    console.log("Target: " + ev.target);  
    console.log("Position: " +  
        ev.position.latitude + "," +  
        ev.position.longitude);  
};  
  
```  
  
> [!IMPORTANT]
>  Os recursos de Tempo de Execução do Windows não estão disponíveis para aplicativos executados no Internet Explorer.  
  
## <a name="see-also"></a>Consulte também  
 [Usar o Windows Runtime em JavaScript](../jswinrt/using-the-windows-runtime-in-javascript.md)