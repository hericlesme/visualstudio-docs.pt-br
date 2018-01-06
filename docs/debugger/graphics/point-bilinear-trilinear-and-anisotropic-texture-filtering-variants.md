---
title: "Ponto, Bilinear, Trilinear e anisotrópico textura variantes de filtragem | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 57d14fc9-b5f7-45ee-9717-48086886742d
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: ed1306d8bca70cd80f50c2980f76c5efc3588279
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="point-bilinear-trilinear-and-anisotropic-texture-filtering-variants"></a>Variantes de filtragem de textura de ponto, bilinear, trilinear e anisotrópico
Substitui o modo de filtragem em amostras adequadas de textura.  
  
## <a name="interpretation"></a>Interpretação  
 Diferentes métodos de amostragem de textura possuem diferentes custos de desempenho e qualidade de imagem. Na ordem crescente de custo, e de qualidade visual, os modos de filtragem são:  
  
1.  Filtragem de ponto (mais barata, pior qualidade visual)  
  
2.  Filtragem bilinear  
  
3.  Filtragem trilinear  
  
4.  Filtragem anisotrópica (mais cara, melhor qualidade visual)  
  
 Se o custo de desempenho de cada variante for significativo ou aumentar com modos de filtragem mais intensos, você pode relacionar o custo à melhor qualidade de imagem. Com base em sua avaliação, você pode aceitar custos de desempenho adicionais para aumentar a qualidade visual ou aceitar uma qualidade visual menor para atingir uma taxa de quadro mais alta ou ganhar mais desempenho, que pode ser usado de outras maneiras.  
  
 Se você achar que o custo de desempenho é insignificante ou permanece estável independentemente do modo de filtragem, por exemplo, quando a GPU de destino possui muito rendimento de sombreador ou largura de banda de memória, considere usar a filtragem anisotrópica para alcançar a melhor qualidade de imagem em seu aplicativo.  
  
## <a name="remarks"></a>Comentários  
 Essas variantes substituem os estados de amostra em chamadas para `ID3D11DeviceContext::PSSetSamplers` nas quais o modo de filtragem fornecido pelo aplicativo é um dos seguintes:  
  
-   `D3D11_FILTER_MIN_MAG_MIP_POINT`  
  
-   `D3D11_FILTER_MIN_MAG_POINT_MIP_LINEAR`  
  
-   `D3D11_FILTER_MIN_POINT_MAG_LINEAR_MIP_POINT`  
  
-   `D3D11_FILTER_MIN_POINT_MAG_MIP_LINEAR`  
  
-   `D3D11_FILTER_MIN_LINEAR_MAG_MIP_POINT`  
  
-   `D3D11_FILTER_MIN_LINEAR_MAG_POINT_MIP_LINEAR`  
  
-   `D3D11_FILTER_MIN_MAG_LINEAR_MIP_POINT`  
  
-   `D3D11_FILTER_MIN_MAG_MIP_LINEAR`  
  
-   `D3D11_FILTER_ANISOTROPIC`  
  
 No **filtragem de textura de ponto** variant, o modo de filtro fornecida pelo aplicativo é substituído pelo `D3D11_FILTER_MIN_MAG_MIP_POINT`; no **Bilinear filtragem de textura** variant, ele é substituído pelo `D3D11_FILTER_MIN_MAG_LINEAR_MIP_POINT`; e, no **filtragem de textura Trilinear** variant, ele é substituído pelo `D3D11_FILTER_MIN_MAG_MIP_LINEAR`.  
  
 No **textura anisotrópico** variant, o modo de filtro fornecida pelo aplicativo é substituído pelo `D3D11_FILTER_ANISOTROPIC`, e o máximo Anisotropy é definido como 16.  
  
## <a name="restrictions-and-limitations"></a>Restrições e limitações  
 No Direct3D, o nível de recurso 9.1 especifica uma anisotropia máxima de 2x. Porque o **textura anisotrópico** variante tenta usar anisotropy de 16 x exclusivamente, reprodução falhará quando a análise de quadros é executada em um dispositivo 9.1 do nível de recurso. Dispositivos contemporâneos que são afetados por essa limitação incluem os tablets Windows Surface RT e Surface 2 baseados em ARM. GPUs mais antigas que ainda podem ser encontradas em alguns computadores também podem ser afetadas, mas elas são consideradas bastante obsoletas e cada vez mais incomuns.  
  
## <a name="example"></a>Exemplo  
 O **filtragem de textura de ponto** variant pode ser reproduzida usando código como este:  
  
```  
D3D11_SAMPLER_DESC sampler_description;  
  
// ... other sampler description setup ...  
  
sampler_description.Filter = D3D11_FILTER_MIN_MAG_MIP_POINT;  
  
d3d_device->CreateSamplerState(&sampler_desc, &sampler);  
d3d_context->PSSetSamplers(0, 1, &sampler  
```  
  
## <a name="example"></a>Exemplo  
 O **Bilinear filtragem de textura** variant pode ser reproduzida usando código como este:  
  
```  
D3D11_SAMPLER_DESC sampler_description;   
  
// ... other sampler description setup ...  
  
sampler_description.Filter = D3D11_FILTER_MIN_MAG_LINEAR_MIP_POINT;  
  
d3d_device->CreateSamplerState(&sampler_desc, &sampler);  
d3d_context->PSSetSamplers(0, 1, &sampler  
```  
  
## <a name="example"></a>Exemplo  
 O **Trilinear filtragem de textura** variant pode ser reproduzida usando código como este:  
  
```  
D3D11_SAMPLER_DESC sampler_description;   
  
// ... other sampler description setup ...  
  
sampler_description.Filter = D3D11_FILTER_MIN_MAG_MIP_LINEAR;  
  
d3d_device->CreateSamplerState(&sampler_desc, &sampler);  
d3d_context->PSSetSamplers(0, 1, &sampler  
```  
  
## <a name="example"></a>Exemplo  
 O **textura anisotrópico** variant pode ser reproduzida usando código como este:  
  
```  
D3D11_SAMPLER_DESC sampler_description;   
  
// ... other sampler description setup ...  
  
sampler_description.Filter = D3D11_FILTER_ANISOTROPIC;  
sampler_description.MaxAnisotropy = 16;  
  
d3d_device->CreateSamplerState(&sampler_desc, &sampler);  
d3d_context->PSSetSamplers(0, 1, &sampler  
```