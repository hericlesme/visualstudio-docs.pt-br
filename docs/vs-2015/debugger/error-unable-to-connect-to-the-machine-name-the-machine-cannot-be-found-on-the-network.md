---
title: 'Erro: Não é possível conectar à máquina &lt;nome&gt;. Não foi possível encontrar o computador na rede. | Microsoft Docs'
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
- vs.debug.remote.dcom_disabled
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- DCOM, unable to connect error
ms.assetid: b584b5db-ef52-45ed-8561-1314da3cc5b8
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fbd5299c8bd14581a9228b7aa0491af6455b1fda
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47465414"
---
# <a name="error-unable-to-connect-to-the-machine-ltnamegt-the-machine-cannot-be-found-on-the-network"></a>Erro: Não é possível conectar à máquina &lt;nome&gt;. Não foi possível encontrar o computador na rede.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [erro: não é possível conectar à máquina &lt;nome&gt;. A máquina não pode ser encontrada na rede. ](https://docs.microsoft.com/visualstudio/debugger/error-unable-to-connect-to-the-machine-name-the-machine-cannot-be-found-on-the-network).  
  
Esse comportamento ocorre se uma das seguintes condições for verdadeira:  
  
-   Sua conexão com o computador remoto foi interrompida.  
  
-   Sua conta de usuário no computador remoto está desabilitada.  
  
-   Sua senha no computador remoto expirou.  
  
### <a name="to-resolve-this-behavior"></a>Para resolver esse comportamento:  
  
-   Verifique se o computador local e o computador remoto estão na mesma rede. Para fazer isso, use o Microsoft Windows Explorer (ou Pesquisador de Arquivos) para tentar acessar o computador remoto.  
  
     — e —  
  
-   Verifique se a conta de usuário que você está usando para se conectar ao computador remoto está habilitada.  
  
     — e —  
  
-   Verifique se a senha que você está usando para se conectar ao computador remoto está válida e não expirou.  
  
## <a name="see-also"></a>Consulte também  
 [Configurar as ferramentas remotas no dispositivo](http://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c)   
 [Preparação e configurações do depurador](../debugger/debugger-settings-and-preparation.md)



