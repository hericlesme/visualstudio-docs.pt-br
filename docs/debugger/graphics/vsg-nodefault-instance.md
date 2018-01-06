---
title: VSG_NODEFAULT_INSTANCE | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 19c95b0d-9a4d-441f-9ed7-3acb39e67521
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 7f94aa50908097b161929e51f260d3bcc058bd5a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="vsgnodefaultinstance"></a>VSG_NODEFAULT_INSTANCE
Define sua presença se uma instância padrão do [classe VsgDbg](vsgdbg-class.md) classe — que fornece a interface de captura programática — é fornecido.  
  
## <a name="syntax"></a>Sintaxe  
  
```C++  
#define VSG_NODEFAULT_INSTANCE  
```  
  
## <a name="value"></a>Valor  
 Pré-processador de um símbolo que por sua presença ou ausência determina se uma instância padrão do `VsgDbg` classe é fornecida. Se este símbolo for definido, em seguida, nenhuma instância padrão do `VsgDbg` classe é fornecida; caso contrário, uma instância padrão é fornecida e inicializada antes que o programa for executado.  
  
 A interface de programação de captura é fornecida através de um ponteiro que tem escopo global, `g_pVsgDbg`.  
  
```  
VsgDbg *g_pVsgDbg;  
```  
  
## <a name="remarks"></a>Comentários  
 A instância padrão é geralmente suficiente, mas para usar a interface de programação de captura dentro de uma DLL quando o dispositivo D3D foi criado fora dessa DLL, você deve criar e gerenciar sua própria instância do `VsgDbg` classe. Se você estiver gerenciando sua própria interface para a API de captura programática dessa maneira, desabilitar a instância padrão definindo `VSG_NODEFAULT_INSTANCE` para evitar a sobrecarga.  
  
 Se a instância padrão não for desabilitada, ele é inicializado automaticamente antes da execução do seu programa e é destruído automaticamente quando o programa for finalizado. Não é necessário que inicializar ou não a essa instância explicitamente.  
  
 Para desabilitar a instância padrão, você deve definir `VSG_NODEFAULT_INSTANCE` antes de você incluir `vsgcapture.h` em seu programa.  
  
## <a name="example"></a>Exemplo  
 Este exemplo mostra como desabilitar a instância padrão:  
  
```  
// Define VSG_NODEFAULT_INSTANCE before including vsgcapture.h  
#define VSG_NODEFAULT_INSTANCE  
  
#include <vsgcapture.h>  
```