---
title: 'Erro: O compartilhamento de arquivos do Windows foi configurado... | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.error.remote_credentials_prohibited
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: c45a1b74-61ec-4c64-9e2c-13051a4f50a5
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: afda40aea2340f85d27218b5a9cd7c4f09f64201
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="error-windows-file-sharing-has-been-configured"></a>Erro: o compartilhamento de arquivos do Windows foi configurado...
O compartilhamento de arquivos do Windows foi configurado de forma que você se conectará ao computador remoto usando um nome do usuário diferente. Isso é incompatível com a depuração remota  
  
 A configuração de compartilhamento de arquivos atual está configurada para conectar ao computador remoto usando um nome do usuário diferente. A depuração remota não é possível nesse cenário.  
  
 Para corrigir esse erro, faça logon no computador usando outro nome de conta ou altere o compartilhamento de arquivos para usar o nome de conta com a qual você está depurando.  
  
 Se você quiser se conectar ao computador remoto usando esse nome de usuário, deverá primeiro desconectar do computador remoto.  
  
### <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1.  Faça logon em seu computador local, o computador do qual você está depurando, usando o outro nome da conta.  
  
     —ou—  
  
     . Desconecte-se do computador remoto e reconfigure o compartilhamento de arquivos para se conectar ao outro computador usando seu nome de conta:  
  
    1.  Sobre o **iniciar** , aponte para **Acessórios**e, em seguida, clique em **Prompt de comando**.  
  
    2.  No prompt de comando do Windows, digite:  
  
         `net use /delete computer_name`  
  
    3.  Modificar as configurações de compartilhamento de arquivos usando qualquer um dos métodos documentados na Ajuda do Windows.