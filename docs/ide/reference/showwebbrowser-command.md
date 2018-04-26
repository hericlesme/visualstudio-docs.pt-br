---
title: Comando ShowWebBrowser
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- view.showwebbrowser
helpviewer_keywords:
- ShowWebBrowser command
- View.ShowWebBrowser command
ms.assetid: c6a4fbd6-8e9d-45cc-8b2f-93990d065e78
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c1396cd28244a655d18f6e09f4795dd099a11ca7
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="showwebbrowser-command"></a>Comando ShowWebBrowser
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

- [Comandos do Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Janela Comando](../../ide/reference/command-window.md)
- [Caixa Localizar/Comando](../../ide/find-command-box.md)
- [Aliases de comando do Visual Studio](../../ide/reference/visual-studio-command-aliases.md)