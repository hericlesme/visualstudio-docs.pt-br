---
title: DONT_SAVE_VSGLOG_TO_TEMP | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f27ab0e6-9575-4ca0-9901-37d3e5c3a2f5
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 264f67eb9a1fc7f8af739d7eea329de05230c7a8
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="dontsavevsglogtotemp"></a>DONT_SAVE_VSGLOG_TO_TEMP
Define sua presença se o arquivo de log do gráfico é salvo para o diretório de arquivos temporários do usuário.  
  
## <a name="syntax"></a>Sintaxe  
  
```C++  
#define DONT_SAVE_VSGLOG_TO_TEMP  
```  
  
## <a name="value"></a>Valor  
 Um símbolo do pré-processador que determina se os elementos gráficos o arquivo de log por sua presença ou ausência é salvo para o diretório de arquivos temporários do usuário. Se este símbolo está definido, o nome de arquivo definido por `VSG_DEFAULT_RUN_FILENAME` é relativo ao diretório atual do aplicativo capturado, ou é um caminho absoluto; caso contrário, o nome de arquivo definido por `VSG_DEFAULT_RUN_FILENAME` é relativo ao diretório de arquivos temporários do usuário e não pode ser um caminho absoluto.  
  
## <a name="remarks"></a>Comentários  
 Dependendo dos privilégios do usuário, o arquivo de log do gráfico não poderá ser salvo em um local arbitrário. É recomendável que você prefere salvar os logs de elementos gráficos no diretório de arquivos temporários do usuário ou de outro local válida, se você não tiver certeza se o local em que você escolheria pode ser gravado pelo usuário.  
  
 Para impedir que o arquivo de log de elementos gráficos que estão sendo salvos no diretório de arquivos temporários, você deve definido `DONT_SAVE_VSGLOG_TO_TEMP` antes de incluir `vsgcapture.h`.  
  
## <a name="example"></a>Exemplo  
 Este exemplo mostra como salvar o arquivo de log de elementos gráficos em um caminho absoluto no computador host.  
  
```  
// Define DONT_SAVE_VSGLOG_TO_TEMP and VSG_DEFAULT_RUN_FILENAME before including vsgcapture.h  
#define DONT_SAVE_VSGLOG_TO_TEMP  
#define VSG_DEFAULT_RUN_FILENAME L"C:\\Graphics Diagnostics Captures\\default.vsglog"  
  
#include <vsgcapture.h>  
  
```  
  
## <a name="see-also"></a>Consulte também  
 [VSG_DEFAULT_RUN_FILENAME](vsg-default-run-filename.md)