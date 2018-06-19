---
title: Método getVarDate (Date) (JavaScript) | Microsoft Docs
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
- getVarDate
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Date object
- getVarDate method
- dates, VT_DATE format
ms.assetid: 561238de-5c91-45a3-b839-a16910d3a1cf
caps.latest.revision: 18
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d21394a5381653997a6b406537a6bde4f5266b97
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24637126"
---
# <a name="getvardate-method-date-javascript"></a>Método getVarDate (Date) (JavaScript)
Retorna um valor VT_DATE de um `Date` objeto.  
  
> [!WARNING]
>  Esse método tem suporte apenas no Internet Explorer.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
dateObj.getVarDate()   
```  
  
#### <a name="parameters"></a>Parâmetros  
 Obrigatório `dateObj` referência é um `Date` objeto.  
  
## <a name="return-value"></a>Valor de retorno  
 Retorna um valor VT_DATE.  
  
## <a name="remarks"></a>Comentários  
 O `getVarDate` método é usado quando o código JavaScript interage com objetos COM, objetos ActiveX ou outros objetos que aceitam e retornam valores de data no formato VT_DATE. Eles incluem objetos no Visual Basic e Visual Basic Scripting Edition (VBScript). O formato real do valor retornado depende das configurações regionais.  
  
## <a name="requirements"></a>Requisitos  
 Tem suporte nos seguintes modos de documentos: Quirks, padrões do Internet Explorer 6, padrões do Internet Explorer 7, padrões do Internet Explorer 8, padrões do Internet Explorer 9 e padrões do Internet Explorer 10. Sem suporte nos aplicativos [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)]. Consulte [Informações sobre versão](../../javascript/reference/javascript-version-information.md).  
  
 **Aplica-se a**: [objeto de data](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Consulte também  
 [Método getDate (Date)](../../javascript/reference/getdate-method-date-javascript.md)   
 [Função Date.parse](../../javascript/reference/date-parse-function-javascript.md)