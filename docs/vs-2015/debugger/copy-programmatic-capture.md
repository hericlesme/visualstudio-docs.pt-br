---
title: Copiar (Captura programática) | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 30ec235a-0abb-44b9-8852-61bc9e67ce22
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 171dd04a4f2c933272a7addc787554f611b1449f
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47467556"
---
# <a name="copy-programmatic-capture"></a>Copiar (captura programática)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [copiar (Captura programática)](https://docs.microsoft.com/visualstudio/debugger/graphics/copy-programmatic-capture).  
  
Copia o conteúdo do arquivo de log (. vsglog) de elementos gráficos ativos em um novo arquivo.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
void Copy(  
  wchar_t const * szNewVSGLog  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `szNewVSGLog`  
 O nome do arquivo do novo arquivo de log de gráficos.  
  
## <a name="remarks"></a>Comentários  
 Para copiar as informações de gráficos para um novo arquivo, você deve já capturou algumas informações de gráficos; Caso contrário, nada acontece.



