---
title: Comando Log Command Window Output | Microsoft Docs
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
- tools.logcommandwindowoutput
helpviewer_keywords:
- log Command window output command
- View.LogCommandWindowOutput command
ms.assetid: d4ecec35-5af4-4954-8d60-2cd24583fbb4
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 9f6cdef31ec8988612815a76c30198e97ddf4c26
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47475526"
---
# <a name="log-command-window-output-command"></a>Comando Saída da Janela Log de Comando
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [Log de comando de saída de janela de comando](https://docs.microsoft.com/visualstudio/ide/reference/log-command-window-output-command).  
  
  
Copia todas as entradas e saídas da janela **Comando** para um arquivo.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
Tools.LogCommandWindowOutput [filename] [/on|/off] [/overwrite]  
```  
  
## <a name="arguments"></a>Arguments  
 `filename`  
 Opcional. Nome do arquivo de log. Por padrão, o arquivo é criado na pasta de perfil do usuário. Se o nome do arquivo já existir, o log será acrescentado ao final do arquivo existente. Se nenhum arquivo for especificado, o último arquivo especificado será usado. Não se houver nenhum arquivo anterior, será criado um arquivo de log padrão, chamado cmdline.log.  
  
> [!TIP]
>  Para alterar o local em que o arquivo de log é salvo, digite o caminho completo do arquivo entre aspas se o caminho contiver espaços.  
  
## <a name="switches"></a>Opções  
 /on  
 Opcional. Inicia o log para a janela **Comando** no arquivo especificado e anexa o arquivo com as novas informações.  
  
 /off  
 Opcional. Parar o log para a janela **Comando**.  
  
 /overwrite  
 Opcional. Se o arquivo especificado no argumento `filename` corresponder a um arquivo existente, o arquivo será substituído.  
  
## <a name="remarks"></a>Comentários  
 Se nenhum arquivo for especificado, o arquivo cmdline.log será criado por padrão. Por padrão, o alias para esse comando é Log.  
  
## <a name="examples"></a>Exemplos  
 Este exemplo cria um novo arquivo de log, cmdlog, e inicia o log de comando.  
  
```  
>Tools.LogCommandWindowOutput cmdlog  
```  
  
 Este exemplo interrompe os comandos de log.  
  
```  
>Tools.LogCommandWindowOutput /off  
```  
  
 Este exemplo retoma o log de comandos no arquivo de log usado anteriormente.  
  
```  
>Tools.LogCommandWindowOutput /on  
```  
  
## <a name="see-also"></a>Consulte também  
 [Comandos do Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Janela Comando](../../ide/reference/command-window.md)   
 [Caixa Localizar/Comando](../../ide/find-command-box.md)   
 [Aliases de comando do Visual Studio](../../ide/reference/visual-studio-command-aliases.md)



