---
title: "Copiar (Captura programática) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 30ec235a-0abb-44b9-8852-61bc9e67ce22
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a0b8cb397afd4f1ba58dca30b4314471b4647576
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="copy-programmatic-capture"></a>Copiar (captura programática)
Copia o conteúdo do arquivo de log (.vsglog) de elementos gráficos ativos em um novo arquivo.  
  
## <a name="syntax"></a>Sintaxe  
  
```C++  
void Copy(  
  wchar_t const * szNewVSGLog  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `szNewVSGLog`  
 O nome do arquivo do novo arquivo de log de elementos gráficos.  
  
## <a name="remarks"></a>Comentários  
 Para copiar as informações de gráficos para um novo arquivo, você deve já ter capturado algumas informações de elementos gráficos; Caso contrário, nada acontece.