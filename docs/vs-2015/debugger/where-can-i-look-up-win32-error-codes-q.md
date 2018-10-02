---
title: Onde posso pesquisar códigos de erro Win32? | Microsoft Docs
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
- vc.errors
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- error codes, Win32
- Win32, error codes
ms.assetid: 8fb4ff42-b8eb-4152-b49e-b802d194b05e
caps.latest.revision: 19
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 86735dae123d0fdedc59f4205af349b86cc6efd0
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47463257"
---
# <a name="where-can-i-look-up-win32-error-codes"></a>Onde posso pesquisar códigos de erro Win32?
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [onde é possível procurar o códigos de erro do Win32?](https://docs.microsoft.com/visualstudio/debugger/where-can-i-look-up-win32-error-codes-q).  
  
WINERROR.H no diretório INCLUDE da instalação do sistema padrão contém as definições do código de erro para as funções de API do Win32.  
  
 Você pode pesquisar um código de erro digitando o código a **Watch** janela ou o **QuickWatch** caixa de diálogo. Por exemplo:  
  
```  
0x80000004,hr  
```  
  
## <a name="see-also"></a>Consulte também  
 [Perguntas frequentes do código nativo de depuração](../debugger/debugging-native-code-faqs.md)   
 [Depurando código nativo](../debugger/debugging-native-code.md)



