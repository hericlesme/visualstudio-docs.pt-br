---
title: "Método toArray (VBArray) (JavaScript) | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: toArray
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: toArray method
ms.assetid: 664de44c-2039-4289-82f6-948e9d744d80
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: eeee8acad04125eb942089b4d8dacef6f0f5e6fb
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="toarray-method-vbarray-javascript"></a>Método toArray (VBArray) (JavaScript)
Retorna um padrão [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] matriz convertido de um VBArray.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
safeArray.toArray( )   
```  
  
## <a name="remarks"></a>Comentários  
 Obrigatório *safeArray* referência é um objeto VBArray.  
  
 A conversão converte o VBArray multidimensional em uma única dimensional [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] matriz. Cada dimensão sucessivo é acrescentado ao final do anterior. Por exemplo, um VBArray com três dimensões e três elementos em cada dimensão é convertido em um [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] matriz da seguinte maneira:  
  
 Suponha que contém o VBArray: (1, 2, 3), (4, 5, 6), (7, 8, 9). Após a conversão, o [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] matriz contém: 1, 2, 3, 4, 5, 6, 7, 8, 9.  
  
 Atualmente, não há nenhuma maneira de converter um [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] matriz em um VBArray.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir consiste em três partes. A primeira parte é o código VBScript para criar uma matriz segura do Visual Basic. A segunda parte é [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] código que converte a matriz segura do Visual Basic para um [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] matriz. Todas essas partes ir para o \<HEAD > seção de uma página HTML. A terceira parte é o [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] código vai para o \<corpo > para executar as duas partes.  
  
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
         a(j, i) = k  
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
function VBArrayTest(vbarray)  
{  
   var a = new VBArray(vbarray);  
   var b = a.toArray();  
   var i;  
   for (i = 0; i < 9; i++)   
   {  
      document.writeln(b[i]);  
   }  
}  
-->  
</script>  
</head>  
  
<body>  
<script type="text/javascript">  
<!--  
   VBArrayTest(CreateVBArray());  
-->  
</script>  
</body>  
```  
  
## <a name="requirements"></a>Requisitos  
 Tem suporte nos seguintes modos de documentos: Quirks, padrões do Internet Explorer 6, padrões do Internet Explorer 7, padrões do Internet Explorer 8, padrões do Internet Explorer 9 e padrões do Internet Explorer 10. Sem suporte nos aplicativos [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)]. Consulte [Informações sobre versão](../../javascript/reference/javascript-version-information.md).  
  
 **Aplica-se a**: [objeto VBArray](../../javascript/reference/vbarray-object-javascript.md)  
  
## <a name="see-also"></a>Consulte também  
 [Método dimensions (VBArray)](../../javascript/reference/dimensions-method-vbarray-javascript.md)   
 [Método getItem (VBArray)](../../javascript/reference/getitem-method-vbarray-javascript.md)   
 [Método LBound (VBArray)](../../javascript/reference/lbound-method-vbarray-javascript.md)   
 [Método ubound (VBArray)](../../javascript/reference/ubound-method-vbarray-javascript.md)