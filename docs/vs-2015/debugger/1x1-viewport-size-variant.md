---
title: Tamanho do visor 1x1 | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3dbc3247-00f5-4644-8ff9-72e9febcf09a
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7c0052a2d59dbcef1d7ea32eab789ab955750f3f
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47476245"
---
# <a name="1x1-viewport-size-variant"></a>Variação de tamanho do visor 1x1
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [variante de tamanho do visor 1 x 1](https://docs.microsoft.com/visualstudio/debugger/graphics/1x1-viewport-size-variant).  
  
Reduz as dimensões do visor em todos os destinos de renderização para 1 x 1 pixels.  
  
## <a name="interpretation"></a>Interpretação  
 Um visor menor reduz a quantidade de pixels a serem sombreados, mas não reduz a quantidade de vértices a serem processadas. Ao definir as dimensões do visor para 1 × 1, você elimina o sombreamento dos pixels de seu aplicativo.  
  
 Se essa variante tiver um ganho de desempenho considerável, é sinal de que o aplicativo consome muita taxa de enchimento. Isso pode indicar que a resolução escolhida está muito alta para a plataforma de destino ou que o aplicativo leva muito tempo para sombrear pixels que serão substituídos (excedente) mais tarde. Esse resultado sugere que o desempenho do aplicativo melhora quando você reduz o tamanho do framebuffer ou a quantidade de excedentes.  
  
## <a name="remarks"></a>Comentários  
 As dimensões do visor são redefinidas para 1 × 1 pixel após cada chamada de `ID3D11DeviceContext::OMSetRenderTargets` ou `ID3D11DeviceContext::RSSetViewports`.  
  
## <a name="example"></a>Exemplo  
 Essa variante pode ser reproduzida por um código como este:  
  
```  
D3D11_VIEWPORT viewport;  
viewport.TopLeftX = 0;  
viewport.TopLeftY = 0;  
viewport.Width = 1;  
viewport.Height = 1;  
d3d_context->RSSetViewports(1, &viewport);  
```



