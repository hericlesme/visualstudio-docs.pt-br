---
title: VSG_NODEFAULT_INSTANCE | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 19c95b0d-9a4d-441f-9ed7-3acb39e67521
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fad6992daf5e8175089ba8f24a4189ad1957ba7c
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47461837"
---
# <a name="vsgnodefaultinstance"></a>VSG_NODEFAULT_INSTANCE
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [VSG_NODEFAULT_INSTANCE](https://docs.microsoft.com/visualstudio/debugger/graphics/vsg-nodefault-instance).  
  
Define por sua presença se uma instância padrão do [classe VsgDbg](../debugger/vsgdbg-class.md) classe — que fornece a interface de captura programática — é fornecido.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
#define VSG_NODEFAULT_INSTANCE  
```  
  
## <a name="value"></a>Valor  
 Um pré-processador de símbolo que por sua presença ou ausência determina se uma instância padrão do `VsgDbg` classe é fornecida. Se esse símbolo é definido, em seguida, nenhuma instância padrão do `VsgDbg` classe é fornecida; caso contrário, uma instância padrão é fornecida e inicializada antes que o programa é executado.  
  
 A interface de captura programática é fornecido por meio de um ponteiro que tem escopo global, `g_pVsgDbg`.  
  
```  
VsgDbg *g_pVsgDbg;  
```  
  
## <a name="remarks"></a>Comentários  
 A instância padrão geralmente é suficiente, mas para usar a interface de captura programática dentro de uma DLL, quando o dispositivo D3D foi criado fora dessa DLL, você deve criar e gerenciar sua própria instância da `VsgDbg` classe. Se você estiver gerenciando sua própria interface para a API de captura programática dessa maneira, desabilitar a instância padrão definindo `VSG_NODEFAULT_INSTANCE` para evitar a sobrecarga.  
  
 Se a instância padrão não for desabilitada, ele é inicializado automaticamente antes da execução do seu programa e é destruído automaticamente quando seu programa é encerrado. Não é preciso inicializar ou não a essa instância explicitamente.  
  
 Para desabilitar a instância padrão, você deve definir `VSG_NODEFAULT_INSTANCE` antes de incluir `vsgcapture.h` em seu programa.  
  
## <a name="example"></a>Exemplo  
 Este exemplo mostra como desabilitar a instância padrão:  
  
```  
// Define VSG_NODEFAULT_INSTANCE before including vsgcapture.h  
#define VSG_NODEFAULT_INSTANCE  
  
#include <vsgcapture.h>  
```



