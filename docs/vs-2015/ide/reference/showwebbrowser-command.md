---
title: Comando ShowWebBrowser | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- view.showwebbrowser
helpviewer_keywords:
- ShowWebBrowser command
- View.ShowWebBrowser command
ms.assetid: c6a4fbd6-8e9d-45cc-8b2f-93990d065e78
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: de730650216f67d3f620fa85cad0a98148ce2ee3
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47463293"
---
# <a name="showwebbrowser-command"></a>Comando ShowWebBrowser
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [comando ShowWebBrowser](https://docs.microsoft.com/visualstudio/ide/reference/showwebbrowser-command).  
  
  
Exibe a URL especificada em uma janela de navegador da Web, tanto dentro do IDE (ambiente de desenvolvimento integrado) ou externa ao IDE.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
View.ShowWebBrowser URL [/new][/ext]  
```  
  
## <a name="arguments"></a>Arguments  
 `URL`  
 Necessário. URL (Uniform Resource Locator) do site da Web.  
  
## <a name="switches"></a>Opções  
 /new  
 Opcional. Especifica que a página é exibida em uma nova instância do navegador da Web.  
  
 /ext  
 Opcional. Especifica que a página é exibida no navegador da Web padrão fora do IDE.  
  
## <a name="remarks"></a>Comentários  
 O alias do comando **ShowWebBrowser** é **navegue** ou **nav**.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir exibe a home page do MSDN Online em um navegador da Web fora do IDE. Se uma instância do navegador da Web já estiver aberta, ela será usada; caso contrário, uma nova instância será iniciada.  
  
```  
>View.ShowWebBrowser http://msdn.microsoft.com /ext  
```  
  
## <a name="see-also"></a>Consulte também  
 [Comandos do Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Janela Comando](../../ide/reference/command-window.md)   
 [Caixa Localizar/Comando](../../ide/find-command-box.md)   
 [Aliases de comando do Visual Studio](../../ide/reference/visual-studio-command-aliases.md)



