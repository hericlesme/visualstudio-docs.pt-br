---
title: ToggleHUD | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7261e01d-3c72-46ce-9fb3-5f33b2ddb901
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b224fdbd4dfadc6af29a0491bba5a18089c260b4
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47463409"
---
# <a name="togglehud"></a>ToggleHUD
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [ToggleHUD](https://docs.microsoft.com/visualstudio/debugger/graphics/togglehud).  
  
Alterna o diagnóstico de gráficos *HUD* de sobreposição (Head-Up Display) ativada ou desativada.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
void ToggleHUD();  
```  
  
## <a name="remarks"></a>Comentários  
 O HUD do diagnóstico de gráficos é exibida no canto superior esquerdo do aplicativo que está em execução no diagnóstico de gráficos. Ele exibe informações de tempo de execução sobre o aplicativo e captura de informações de gráficos e as mensagens que são adicionadas por meio da chamada a [AddMessage](../debugger/addmessage.md) função de membro.  
  
 Para ativar ou desativar o HUD, você não precisa ser ativamente capturando informações de gráficos — ou seja, ele pode ser alternado por meio de uma instância das `VsgDbg` classe, mas o [Init](../debugger/init.md) função de membro não precisa ser chamado primeiro.



