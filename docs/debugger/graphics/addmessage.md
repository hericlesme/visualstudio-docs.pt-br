---
title: AddMessage | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 102a0404-a00c-4566-93f3-01bc8df63280
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 0841e622b0fe7c0d01d374da21a12a151c59021d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="addmessage"></a>AddMessage
Adiciona uma mensagem personalizada para o diagnóstico de gráficos *HUD* (visor).  
  
## <a name="syntax"></a>Sintaxe  
  
```C++  
void AddMessage(  
  wchar_t const * szMessage  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `szMessage`  
 A mensagem a ser adicionada para o HUD.  
  
## <a name="remarks"></a>Comentários  
 O HUD de diagnóstico de gráficos é exibido no canto superior esquerdo do aplicativo que está sendo executado com o diagnóstico de gráficos. Exibe informações de tempo de execução sobre o aplicativo e sobre a captura de informações de elementos gráficos e mensagens que são adicionadas ao chamar essa função.  
  
 Para adicionar uma mensagem para o HUD, você não precisa estar ativamente capturando informações de gráficos — ou seja, uma mensagem pode ser adicionada por meio de uma instância do `VsgDbg` classe, mas o [Init](init.md) função de membro não ser chamado primeiro. Mensagens são exibidas somente no HUD, eles não são registrados no arquivo de log de elementos gráficos.