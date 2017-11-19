---
title: Objeto VBArray (JavaScript) | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: VBArray
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: VBArray object constant
ms.assetid: f0b767f1-ea8a-4726-962b-2708d4742518
caps.latest.revision: "17"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b86e261a0cef445f1e0e0ecd651d5eb283cffce1
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="vbarray-object-javascript"></a>Objeto VBArray (JavaScript)
Fornece acesso a matrizes seguras do Visual Basic.  
  
> [!WARNING]
>  Esse objeto é suportado no Internet Explorer apenas, não no [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] aplicativos.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
varName = new VBArray(safeArray)   
```  
  
## <a name="parameters"></a>Parâmetros  
 `varName`  
 Necessário. O nome da variável à qual o VBArray é atribuído.  
  
 *safeArray*  
 Necessário. Um valor de VBArray.  
  
## <a name="remarks"></a>Comentários  
 VBArrays são somente leitura e não pode ser criados diretamente. O *safeArray* argumento deve ter obtido um valor VBArray antes de ser passado para o construtor VBArray. Isso pode ser feito somente por recuperar o valor de um controle ActiveX existente ou em outro objeto.  
  
 VBArrays pode ter várias dimensões. Os índices de cada dimensão podem ser diferentes. O **dimensões** método recupera o número de dimensões da matriz; a `lbound` e `ubound` métodos de recuperar o intervalo de índices usado por cada dimensão.  
  
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
      document.writeln("<br />")  
   Next  
   CreateVBArray = a  
End Function  
-->  
</script>  
  
<script type="text/javascript">  
<!--  
function VBArrayTest(vbarray){  
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
  
## <a name="properties"></a>Propriedades  
 O `VBArray` objeto não tem propriedades.  
  
## <a name="methods"></a>Métodos  
 [Método Dimensions](../../javascript/reference/dimensions-method-vbarray-javascript.md) &#124; [método getItem](../../javascript/reference/getitem-method-vbarray-javascript.md) &#124; [método lbound](../../javascript/reference/lbound-method-vbarray-javascript.md) &#124; [método toArray](../../javascript/reference/toarray-method-vbarray-javascript.md) &#124; [método ubound](../../javascript/reference/ubound-method-vbarray-javascript.md)  
  
## <a name="requirements"></a>Requisitos  
 Tem suporte nos seguintes modos de documentos: Quirks, padrões do Internet Explorer 6, padrões do Internet Explorer 7, padrões do Internet Explorer 8, padrões do Internet Explorer 9 e padrões do Internet Explorer 10. Sem suporte nos aplicativos [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)]. Consulte [Informações sobre versão](../../javascript/reference/javascript-version-information.md).  
  
## <a name="see-also"></a>Consulte também  
 [Objeto Array](../../javascript/reference/array-object-javascript.md)