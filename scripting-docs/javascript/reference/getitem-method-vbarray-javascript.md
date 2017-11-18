---
title: "Método getItem (VBArray) (JavaScript) | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: getItem
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- getItem method
- Item property
ms.assetid: f62964ad-8b2f-4596-95d0-b20e587ecea5
caps.latest.revision: "16"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e6457435d047f2780a19fa8ce26fc2bb86f7ae0e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="getitem-method-vbarray-javascript"></a>Método getItem (VBArray) (JavaScript)
Retorna o item no local especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
safeArray.getItem(dimension1[, dimension2, ...], dimensionN)   
```  
  
## <a name="parameters"></a>Parâmetros  
 *safeArray*  
 Necessário. Um objeto VBArray.  
  
 *dimension1,..., dimensionN*  
 Especifica o local exato do elemento do VBArray desejado. *n*é igual ao número de dimensões a VBArray.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir consiste em três partes. A primeira parte é o código VBScript para criar uma matriz segura do Visual Basic. A segunda parte é [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] código itera a matriz segura do Visual Basic e imprime o conteúdo de cada elemento. Todas essas partes ir para o \<HEAD > seção de uma página HTML. A terceira parte é o [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] código vai para o \<corpo > para executar as duas partes.  
  
```JavaScript  
<head>  
<script type="text/vbscript">  
<!--  
Function CreateVBArray()  
   Dim i, j, k  
   Dim a(2, 2)  
   k = 1  
   For i = 0 To 2  
      For j = 0 To 2  
         a(i, j) = k  
         document.writeln(k)  
         k = k + 1  
      Next  
      document.writeln("<BR>")  
   Next  
   CreateVBArray = a  
End Function  
-->  
</script>  
<script type="text/javascript">  
<!--  
function GetItemTest(vbarray)  
{  
   var i, j;  
   var a = new VBArray(vbarray);  
   for (i = 0; i <= 2; i++)  
   {  
      for (j =0; j <= 2; j++)  
      {  
         document.writeln(a.getItem(i, j));  
      }  
   }  
}  
-->  
</script>  
</head>  
<body>  
<script type="text/javascript">  
<!--  
   GetItemTest(CreateVBArray());  
-->  
</script>  
</body>  
```  
  
## <a name="requirements"></a>Requisitos  
 Tem suporte nos seguintes modos de documentos: Quirks, padrões do Internet Explorer 6, padrões do Internet Explorer 7, padrões do Internet Explorer 8, padrões do Internet Explorer 9 e padrões do Internet Explorer 10. Sem suporte nos aplicativos [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)]. Consulte [Informações sobre versão](../../javascript/reference/javascript-version-information.md).  
  
 **Aplica-se a**: [objeto VBArray](../../javascript/reference/vbarray-object-javascript.md)  
  
## <a name="see-also"></a>Consulte também  
 [Método dimensions (VBArray)](../../javascript/reference/dimensions-method-vbarray-javascript.md)   
 [Método LBound (VBArray)](../../javascript/reference/lbound-method-vbarray-javascript.md)   
 [Método toArray (VBArray)](../../javascript/reference/toarray-method-vbarray-javascript.md)   
 [Método ubound (VBArray)](../../javascript/reference/ubound-method-vbarray-javascript.md)