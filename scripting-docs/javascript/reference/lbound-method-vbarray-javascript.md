---
title: "Método LBound (VBArray) (JavaScript) | Microsoft Docs"
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
- lbound
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- lbound method
ms.assetid: 30ff5e8a-8165-494b-bce8-0a562ec2eec3
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b01adf424d42e9d24512d15b03ede6079a3da186
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="lbound-method-vbarray-javascript"></a>Método lbound (VBArray) (JavaScript)
Retorna o menor valor de índice usado na dimensão especificada de um VBArray.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
safeArray.lbound(dimension)   
```  
  
## <a name="parameters"></a>Parâmetros  
 *safeArray*  
 Necessário. Um objeto VBArray.  
  
 `dimension`  
 Opcional. A dimensão do VBArray desejado para a qual o índice de limite inferior. Se omitido, `lbound` se comporta como se um 1 foi passado.  
  
## <a name="remarks"></a>Comentários  
 Se o VBArray estiver vazia, o `lbound` método retorna indefinido. Se `dimension` é maior que o número de dimensões a VBArray ou for negativo, o método gera um erro "Subscrito fora do intervalo".  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir consiste em três partes. A primeira parte é o código VBScript para criar uma matriz segura do Visual Basic. A segunda parte é [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] código que determina o número de dimensões da matriz segura e o limite inferior de cada dimensão. Desde que a matriz segura é criada no VBScript em vez de Visual Basic, o limite inferior sempre será zero. Todas essas partes ir para o \<HEAD > seção de uma página HTML. A terceira parte é o [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] código vai para o \<corpo > para executar as duas partes.  
  
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
         k = k + 1  
      Next  
   Next  
   CreateVBArray = a  
End Function  
-->  
</script>  
  
<script type="text/javascript">  
<!--  
function VBArrayTest(vba){  
   var i;  
   var a = new VBArray(vba);  
   var s = "";  
   for (i = 1; i <= a.dimensions(); i++)  
   {  
      s += "The lower bound of dimension ";  
      s += i + " is ";  
      s += a.lbound(i);  
      s += ".<br />";  
   }  
   return (s);  
}  
-->  
</script>  
</head>  
  
<body>  
<script type="text/javascript">  
   document.write(VBArrayTest(CreateVBArray()));  
</script>  
</body>  
```  
  
## <a name="requirements"></a>Requisitos  
 Tem suporte nos seguintes modos de documentos: Quirks, padrões do Internet Explorer 6, padrões do Internet Explorer 7, padrões do Internet Explorer 8, padrões do Internet Explorer 9 e padrões do Internet Explorer 10. Sem suporte nos aplicativos [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)]. Consulte [Informações sobre versão](../../javascript/reference/javascript-version-information.md).  
  
 **Aplica-se a**: [objeto VBArray](../../javascript/reference/vbarray-object-javascript.md)  
  
## <a name="see-also"></a>Consulte também  
 [Método dimensions (VBArray)](../../javascript/reference/dimensions-method-vbarray-javascript.md)   
 [Método getItem (VBArray)](../../javascript/reference/getitem-method-vbarray-javascript.md)   
 [Método toArray (VBArray)](../../javascript/reference/toarray-method-vbarray-javascript.md)   
 [Método ubound (VBArray)](../../javascript/reference/ubound-method-vbarray-javascript.md)