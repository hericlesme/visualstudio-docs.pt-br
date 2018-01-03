---
title: "Comando Listar Módulos | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: debug.listmodules
helpviewer_keywords:
- Debug.ListModules command
- ListModules command
- list modules command
ms.assetid: 3cb73774-6ac0-43b2-b781-75ed47175bfd
caps.latest.revision: "6"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: bd752aca6bc52393da14da58c805d303c57673d4
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="list-modules-command"></a>Comando Listar Módulos
Lista os módulos do processo atual.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
Debug.ListModules [/Address:yes|no] [/Name:yes|no] [/Order:yes|no]  
[/Path:yes|no] [/Process:yes|no] [/SymbolFile:yes|no]  
[/SymbolStatus:yes|no] [/Timestamp:yes|no] [/Version:yes|no]  
```  
  
#### <a name="parameters"></a>Parâmetros  
 /Address:`yes|no`  
 Opcional. Especifica se os endereços de memória dos módulos devem ser exibidos. O valor padrão é `yes`.  
  
 /Name:`yes|no`  
 Opcional. Especifica se os nomes dos módulos devem ser exibidos. O valor padrão é `yes`.  
  
 /Order:`yes|no`  
 Opcional. Especifica se a ordem dos módulos deve ser exibida. O valor padrão é `no`.  
  
 /Path:`yes|no`  
 Opcional. Especifica se os caminhos dos módulos devem ser exibidos. O valor padrão é `yes`.  
  
 /Process:`yes|no`  
 Opcional. Especifica se os processos dos módulos devem ser exibidos. O valor padrão é `no`.  
  
 /SymbolFile:`yes|no`  
 Opcional. Especifica se os arquivos de símbolo dos módulos devem ser exibidos. O valor padrão é `no`.  
  
 /SymbolStatus:`yes|no`  
 Opcional. Especifica se os status de símbolo dos módulos devem ser exibidos. O valor padrão é `yes`.  
  
 /Timestamp:`yes|no`  
 Opcional. Especifica se os carimbos de data/hora dos módulos devem ser exibidos. O valor padrão é `no`.  
  
 /Version:`yes|no`  
 Opcional. Especifica se as versões dos módulos devem ser exibidas. O valor padrão é `no`.  
  
## <a name="remarks"></a>Comentários  
  
## <a name="example"></a>Exemplo  
 Este exemplo lista os nomes, endereços e carimbos de data/hora do módulo para o processo atual.  
  
```  
Debug.ListModules /Address:yes /Name:yes /Order:no /Path:no /Process:no /SymbolFile:no /SymbolStatus:no /Timestamp:yes /Version:no  
```  
  
## <a name="see-also"></a>Consulte também  
 [Comandos do Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Janela Comando](../../ide/reference/command-window.md)   
 [Como usar a janela Módulos](../../debugger/how-to-use-the-modules-window.md)