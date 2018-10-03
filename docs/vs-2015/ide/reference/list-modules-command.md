---
title: Comando Listar Módulos | Microsoft Docs
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
- debug.listmodules
helpviewer_keywords:
- Debug.ListModules command
- ListModules command
- list modules command
ms.assetid: 3cb73774-6ac0-43b2-b781-75ed47175bfd
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 1593879f59642347f58d9c8229aac7d2a9d70261
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47475580"
---
# <a name="list-modules-command"></a>Comando Listar Módulos
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [comando Listar módulos](https://docs.microsoft.com/visualstudio/ide/reference/list-modules-command).  
  
  
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



