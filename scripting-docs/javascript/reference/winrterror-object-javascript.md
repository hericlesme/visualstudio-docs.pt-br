---
title: Objeto WinRTError (JavaScript) | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- WinRTError object [JavaScript]
- JavaScript, WinRTError object
ms.assetid: d75ab8e5-e729-4d86-90fd-ea228c30dd66
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 11b339b4fc3c4bd4f34416ffd98b8f9c3f288f98
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="winrterror-object-javascript"></a>Objeto WinRTError (JavaScript)
Quanto um Tempo de Execução do Windows retorna um HRESULT que indica falha, o JavaScript o converte em um erro especial de Tempo de Execução do Windows. Isso só acontece em aplicativos [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] e quando o Tempo de Execução do Windows está disponível como parte do namespace de JavaScript global.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
errorObj = new WinRTError();  
  
```  
  
## <a name="remarks"></a>Comentários  
 O tipo de erro WinRTError só é usado para erros originados nas APIs do Tempo de Execução do Windows.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como os erros WinRTError surgem e são reconhecidos.  
  
```JavaScript  
try {  
            Windows.Storage.ApplicationData.localFolder.createFileAsync("sample.txt");  
        } catch (err) {  
            var n = err;  
        }  
  
```  
  
## <a name="methods"></a>Métodos  
 O objeto WinRTError não tem métodos.  
  
## <a name="properties"></a>Propriedades  
 O objeto WinRTError tem as mesmas propriedades que o [erro objeto](../../javascript/reference/error-object-javascript.md) objeto.  
  
## <a name="requirements"></a>Requisitos  
 O objeto WinRTError é compatível somente com aplicativos da [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] e não é compatível com o Internet Explorer.  
  
## <a name="see-also"></a>Consulte também  
 [Objeto Error](../../javascript/reference/error-object-javascript.md)