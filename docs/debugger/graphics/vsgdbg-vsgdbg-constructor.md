---
title: 'Vsgdbg:: Vsgdbg (construtor) | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 670651e6-5e79-4845-b0c2-671beb7055a8
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 095fb9d8477a649c72204c018f28fe6636a3903f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="vsgdbgvsgdbg-constructor"></a>VsgDbg::VsgDbg (Construtor)
Constrói uma instância do `VsgDbg` classe com ou sem Preparando o componente no aplicativo de diagnóstico de gráficos para capturar e registrar informações de gráficos por padrão, com base no parâmetro booliano especificado ativamente.  
  
## <a name="syntax"></a>Sintaxe  
  
```C++  
VsgDbg(  
  bDefaultInit  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `bDefaultInit`  
 `true`para especificar que o componente no aplicativo de diagnóstico de gráficos deve estar preparado para capturar ativamente e gravar informações de elementos gráficos. `false` para especificar que o aplicativo não deve estar preparado para capturar e registrar informações de elementos gráficos no momento ativamente.  
  
## <a name="remarks"></a>Comentários  
 Quando o construtor for chamado com `bDefaultInit` definida como `true`, o nome do arquivo do arquivo de log do gráfico é determinado por como o `DONT_SAVE_VSGLOG_TO_TEMP` e `VSG_DEFAULT_RUN_FILENAME` símbolos de pré-processamento são definidos antes de `vsgcapture.h` está incluído em seu aplicativo.  
  
 Quando o construtor for chamado com `bDefaultInit` definida como `false`, o componente no aplicativo de diagnóstico de gráficos pode estar preparado para capturar ativamente e registram as informações de elementos gráficos em um momento posterior, chamando o `Init` função.  
  
## <a name="see-also"></a>Consulte também  
 [VsgDbg:: ~ VsgDbg (destruidor)](vsgdbg-tilde-vsgdbg-destructor.md)   
 [Init](init.md)   
 [DONT_SAVE_VSGLOG_TO_TEMP](dont-save-vsglog-to-temp.md)   
 [VSG_DEFAULT_RUN_FILENAME](vsg-default-run-filename.md)