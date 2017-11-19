---
title: Objeto ActiveXObject (JavaScript) | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: ActiveXObject
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- ActiveXObject object
- Automation objects, ActiveXObject objects
ms.assetid: 9c7bed07-853f-48aa-92db-3131324746ec
caps.latest.revision: "34"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 77bb743aeab563f7d7711e4caa9a0fcf0b45ff58
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="activexobject-object-javascript"></a>Objeto ActiveXObject (JavaScript)
Possibilita e retorna uma referência a um objeto de Automação.  
  
 Este objeto é usado somente para instanciar objetos de Automação. Ele não possui membros.  
  
> [!WARNING]
>  Este objeto é uma extensão da Microsoft e é compatível apenas com o Internet Explorer, e não em aplicativos [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)].  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
newObj = new ActiveXObject(servername.typename[, location])  
```  
  
## <a name="parameters"></a>Parâmetros  
 `newObj`  
 Necessário. O nome da variável à qual `ActiveXObject` é atribuído.  
  
 `servername`  
 Necessário. O nome do aplicativo que fornece o objeto.  
  
 `typename`  
 Necessário. O tipo ou a classe do objeto a ser criado.  
  
 `location`  
 Opcional. O nome do servidor de rede no qual o objeto deve ser criado.  
  
## <a name="remarks"></a>Comentários  
 Os servidores de automação fornecem pelo menos um tipo de objeto. Por exemplo, um aplicativo de processamento de texto pode fornecer um objeto Application, um objeto Document e um objeto Toolbar.  
  
 Talvez você seja capaz de identificar valores de `servername.typename` em um host PC na chave do Registro `HKEY_CLASSES_ROOT`. Por exemplo, aqui estão alguns exemplos dos valores que poderão ser encontrados lá, dependendo dos programas instalados:  
  
-   Excel.Application  
  
-   Excel.Chart  
  
-   Scripting.FileSystemObject  
  
-   WScript.Shell  
  
-   Word.Document  
  
> [!IMPORTANT]
>  Os objetos ActiveX podem apresentar questões de segurança. Para usar o `ActiveXObject`, talvez você precise ajustar as configurações de segurança no Internet Explorer para a zona de segurança relevante. Por exemplo, para a zona Intranet local, geralmente é necessário alterar uma configuração personalizada para “Inicializar e criar script de controles ActiveX não marcados como seguros para script".  
  
 Para identificar membros de um objeto de automação que você pode usar em seu código, talvez seja necessário usar um pesquisador de objetos COM, como o [Visualizador de objeto OLE/COM](http://msdn.microsoft.com/library/d0kh9f4c.aspx), se nenhuma documentação de referência está disponível para o objeto de automação.  
  
 Para criar um objeto de Automação, atribua o novo `ActiveXObject` a uma variável de objeto:  
  
```JavaScript  
var ExcelApp = new ActiveXObject("Excel.Application");  
var ExcelSheet = new ActiveXObject("Excel.Sheet");  
```  
  
 Este código inicia o aplicativo que cria o objeto (nesse caso, uma planilha do Microsoft Excel). Depois que um objeto for criado, faça referência a ele no código usando a variável de objeto que você definiu. No exemplo a seguir, você acessa propriedades e métodos do novo objeto usando a variável de objeto `ExcelSheet` e outros objetos do Excel, incluindo o objeto Application e a coleção ActiveSheet.Cells.  
  
```JavaScript  
// Make Excel visible through the Application object.  
ExcelSheet.Application.Visible = true;  
// Place some text in the first cell of the sheet.  
ExcelSheet.ActiveSheet.Cells(1,1).Value = "This is column A, row 1";  
// Save the sheet.  
ExcelSheet.SaveAs("C:\\TEST.XLS");  
// Close Excel with the Quit method on the Application object.  
ExcelSheet.Application.Quit();  
```  
  
## <a name="requirements"></a>Requisitos  
 Com suporte nos seguintes modos de documento: Quirks, padrões do Internet Explorer 6, padrões do Internet Explorer 7, padrões do Internet Explorer 8, padrões do Internet Explorer 9, padrões do Internet Explorer 10 e padrões do Internet Explorer 11. Sem suporte nos aplicativos [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)]. Consulte [Informações sobre versão](../../javascript/reference/javascript-version-information.md).  
  
> [!NOTE]
>  Não há suporte à criação de `ActiveXObject` em um servidor remoto no [!INCLUDE[jsv9text](../../javascript/includes/jsv9text-md.md)] ou em versões posteriores.  
  
## <a name="see-also"></a>Consulte também  
 [Função GetObject](../../javascript/reference/getobject-function-javascript.md)   
 [Autenticação exclusivas usando o aplicativo de exemplo mágico do HTML5/WCF](http://code.msdn.microsoft.com/Unique-Authentication-f32d2da0)