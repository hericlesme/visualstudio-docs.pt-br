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
ms.openlocfilehash: f7e5780a2462e8980c22c474ae6236c87aee599b
ms.sourcegitcommit: 498e39e89a89ad7bf9dcb0617424fff999b1c3b2
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/21/2018
ms.locfileid: "36302799"
---
# <a name="handling-windows-runtime-events-in-javascript"></a>Manipular eventos do Windows Runtime em JavaScript
Eventos do Tempo de Execução do Windows não são representados da mesma maneira que em JavaScript, pois eles estão em C++ ou .NET Framework. Eles não são propriedades de classe, mas são representados como identificadores de cadeia de caracteres (em minúsculas) enviados para os métodos `addEventListener` e `removeEventListener` da classe. Por exemplo, você pode adicionar um manipulador de eventos para o evento [Geolocator.PositionChanged](https://msdn.microsoft.com/library/windows/apps/xaml/windows.devices.geolocation.geolocator.positionchanged.aspx) passando a cadeia de caracteres "positionchanged" para o método `Geolocator.addEventListener`:  
  
```JavaScript  
var locator = new Windows.Devices.Geolocation.Geolocator();  
locator.addEventListener(  
    "positionchanged",   
     function (ev) {  
        console.log("Got event");  
    });  
```  
  
 Também é possível definir a propriedade `locator.onpositionchanged`:  
  
```JavaScript  
locator.onpositionchanged =    
    function (ev) {  
        console.log("Got event");  
    };  
```  
  
Outra diferença entre o .NET/C++ e o JavaScript é o número de parâmetros usados por um manipulador de eventos. No .NET/C++, o manipulador usa dois: o remetente do evento e os dados do evento. No JavaScript, os dois são empacotados como um único objeto `Event`. No exemplo a seguir, o parâmetro `ev` contém o remetente do evento (a propriedade `target`) e as propriedades de dados de evento (aqui, apenas `position`). As propriedades de dados de evento são aquelas que estão documentados para cada evento.
  
```JavaScript  
function (ev) {  
    console.log("Sender: " + ev.target);  
    console.log("Position: " +  
        ev.position.latitude + "," +  
        ev.position.longitude);  
};  
```  
  
> [!IMPORTANT]
>  Os recursos de Tempo de Execução do Windows não estão disponíveis para aplicativos executados no Internet Explorer.  
  
## <a name="see-also"></a>Consulte também  
 [Usar o Windows Runtime em JavaScript](../jswinrt/using-the-windows-runtime-in-javascript.md)
