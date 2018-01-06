---
title: Variante de tamanho do visor 1x1 | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3dbc3247-00f5-4644-8ff9-72e9febcf09a
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: ab9f8be1d202f21147afaf9f4f52a3c90c403ed8
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="1x1-viewport-size-variant"></a>Variação de tamanho do visor 1x1
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