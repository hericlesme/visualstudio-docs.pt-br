---
title: UnInit | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4cd4fc0b-974a-4e61-9ea8-0aaa1a0c52ea
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 285cfb5a68055612fc7d77022b8f9d1d61067ded
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="uninit"></a>UnInit
Finaliza o arquivo de log do gráfico, fecha e libera os recursos que foram usados enquanto o aplicativo foi ativamente gravando informações de gráficos.  
  
## <a name="syntax"></a>Sintaxe  
  
```C++  
void UnInit();  
```  
  
## <a name="remarks"></a>Comentários  
 `UnInit`é chamado automaticamente quando uma instância do `VsgDbg` classe é destruída. Se o `VsgDbg` instância não foi ativamente gravando informações de gráficos, isso não tem nenhum efeito.  
  
 Após `UnInit` foi chamado em uma instância do `VsgDbg` classe gráficos uma novo arquivo de log pode ser criado chamando `Init` e finalizado chamando `UnInit`. Você pode repetir esta quantas vezes você deseja usar o mesmo `VsgDbg` instância para criar o gráfico independente de vários arquivos de log.  
  
## <a name="see-also"></a>Consulte também  
 [Init](init.md)