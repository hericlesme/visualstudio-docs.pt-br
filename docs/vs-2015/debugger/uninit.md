---
title: UnInit | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4cd4fc0b-974a-4e61-9ea8-0aaa1a0c52ea
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4cd66d7329fa4bfc288f3d60879e45cc86ded94e
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47463493"
---
# <a name="uninit"></a>UnInit
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [UnInit](https://docs.microsoft.com/visualstudio/debugger/graphics/uninit).  
  
Finaliza o arquivo de log de gráficos, fecha e libera os recursos que foram usados enquanto o aplicativo ativamente estava gravando informações de gráficos.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
void UnInit();  
```  
  
## <a name="remarks"></a>Comentários  
 `UnInit` é chamado automaticamente quando uma instância da `VsgDbg` classe seja destruída. Se o `VsgDbg` instância não estava gravando ativamente informações de gráficos, isso não tem nenhum efeito.  
  
 Após `UnInit` foi chamado em uma instância da `VsgDbg` classe, uma gráfico novo arquivo de log pode ser criado chamando `Init` e finalização, chamando `UnInit`. Você pode repetir isso quantas vezes você deseja usar o mesmo `VsgDbg` instância para criar gráficos independentes de vários arquivos de log.  
  
## <a name="see-also"></a>Consulte também  
 [Init](../debugger/init.md)



