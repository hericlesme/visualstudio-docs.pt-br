---
title: ToggleHUD | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7261e01d-3c72-46ce-9fb3-5f33b2ddb901
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: baaa776a64d9b778c161ab7e65bb0f15e6c90099
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="togglehud"></a>ToggleHUD
Alterna o diagnóstico de gráficos *HUD* (visor) sobreposição ativado ou desativado.  
  
## <a name="syntax"></a>Sintaxe  
  
```C++  
void ToggleHUD();  
```  
  
## <a name="remarks"></a>Comentários  
 O HUD de diagnóstico de gráficos é exibido no canto superior esquerdo do aplicativo que está sendo executado com o diagnóstico de gráficos. Exibe informações de tempo de execução sobre o aplicativo e sobre a captura de informações de elementos gráficos e mensagens que são adicionadas ao chamar o [AddMessage](addmessage.md) função de membro.  
  
 Para alternar o HUD, você não precisa estar ativamente capturando informações de gráficos — ou seja, ele pode ser alternado por meio de uma instância do `VsgDbg` classe, mas o [Init](init.md) função de membro não precisa ser chamado primeiro.