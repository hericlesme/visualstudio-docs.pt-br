---
title: 'Erro: O compartilhamento de arquivos do Windows foi configurado... | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.error.remote_credentials_prohibited
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: c45a1b74-61ec-4c64-9e2c-13051a4f50a5
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9fc4d3fb02b1c7c9d5003f82fbe42be73c93d6eb
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47464453"
---
# <a name="error-windows-file-sharing-has-been-configured"></a>Erro: o compartilhamento de arquivos do Windows foi configurado...
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [erro: o compartilhamento de arquivos do Windows foi configurado... ](https://docs.microsoft.com/visualstudio/debugger/error-windows-file-sharing-has-been-configured-dot-dot-dot).  
  
O compartilhamento de arquivos do Windows foi configurado de forma que você se conectará ao computador remoto usando um nome do usuário diferente. Isso é incompatível com a depuração remota  
  
 A configuração de compartilhamento de arquivos atual está configurada para conectar ao computador remoto usando um nome do usuário diferente. A depuração remota não é possível nesse cenário.  
  
 Para corrigir esse erro, faça logon no computador usando outro nome de conta ou altere o compartilhamento de arquivos para usar o nome de conta com a qual você está depurando.  
  
 Se você quiser se conectar ao computador remoto usando esse nome de usuário, deverá primeiro desconectar do computador remoto.  
  
### <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1.  Faça logon em seu computador local, o computador do qual você está depurando, usando o outro nome da conta.  
  
     —ou—  
  
     . Desconecte-se do computador remoto e reconfigure o compartilhamento de arquivos para se conectar ao outro computador usando seu nome de conta:  
  
    1.  Sobre o **inicie** , aponte para **Acessórios**e, em seguida, clique em **Prompt de comando**.  
  
    2.  No prompt de comando do Windows, digite:  
  
         `net use /delete computer_name`  
  
    3.  Modificar as configurações de compartilhamento de arquivos usando qualquer um dos métodos documentados na Ajuda do Windows.



