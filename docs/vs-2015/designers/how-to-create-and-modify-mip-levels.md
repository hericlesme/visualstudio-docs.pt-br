---
title: Como criar e modificar níveis de MIP | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f64d4369-2307-4175-a39a-2e45506f7fa1
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 629b7a2d2b1b80c8a2eede4ebd7a3c016651b2bd
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47472941"
---
# <a name="how-to-create-and-modify-mip-levels"></a>Como criar e modificar níveis MIP
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [como: criar e modificar níveis de MIP](https://docs.microsoft.com/visualstudio/designers/how-to-create-and-modify-mip-levels).  
  
Este documento demonstra como usar o **Editor de Imagens** para gerar e modificar *níveis de MIP* para um nível de detalhe (LoD) de espaço de textura.  
  
## <a name="generating-mip-levels"></a>Gerando níveis MIP  
 *Mapeamento mip* é uma técnica usada para aumentar a velocidade de processamento e reduzir artefatos de suavização em objetos texturizados pré-calculando e armazenando várias cópias de uma textura em tamanhos diferentes. Cada cópia, que é conhecida como um nível de MIP, é metade da largura e altura da cópia anterior. Quando uma textura é processada na superfície de um objeto, o nível de MIP que melhor corresponde à área de espaço de tela da superfície texturizada é escolhido automaticamente. Isso significa que o hardware gráfico não precisa filtrar texturas muito grandes para manter a qualidade visual consistente. Embora o custo de memória de armazenar os níveis de MIP seja 33% maior do que aquele de armazenar a textura original sozinha, os ganhos de desempenho e qualidade de imagem justificam isso.  
  
#### <a name="to-generate-mip-levels"></a>Para gerar os níveis de MIP  
  
1.  Comece com uma textura básica, conforme descrito em [Como criar uma textura básica](../designers/how-to-create-a-basic-texture.md). Para obter melhores resultados, especifique uma textura com largura e altura que sejam uma potência de dois em tamanho, por exemplo, 256, 512, 1024 e assim por diante.  
  
2.  Gere os níveis de MIP. Na barra de ferramentas **Modo do Editor de Imagens**, escolha **Avançado**, **Ferramentas**, **Gerar Mips**.  
  
     Observe que os botões **Ir Para o Próximo Nível de Mip** e **Ir Para o Nível de Mip Anterior** aparecem agora na barra de ferramentas **Modo do Editor de Imagens**. Se a janela **Propriedades** for exibida, observe também que as propriedades somente leitura **Nível de Mip** e **Contagem de Nível de Mip** agora aparecem nas propriedades da imagem.  
  
## <a name="modifying-mip-levels"></a>Modificando níveis MIP  
 Para obter efeitos especiais ou aumentar a qualidade da imagem em níveis específicos de detalhe, você pode modificar cada nível de MIP individualmente. Por exemplo, você pode dar a um objeto de textura uma aparência diferente em uma distância (uma distância maior corresponde a níveis de MIP menores) ou você pode garantir que texturas que contenham texto ou símbolos permaneçam legíveis mesmo com níveis de MIP menores.  
  
#### <a name="to-modify-an-individual-mip-level"></a>Para modificar um nível de MIP individual  
  
1.  Selecione o nível de MIP que você deseja modificar. Na barra de ferramentas **Modo do Editor de Imagens**, use os botões **Ir Para o Próximo Nível de MIP** e **Ir Para o Nível de MIP Anterior** para mover-se entre os níveis de MIP.  
  
2.  Depois de selecionar o nível de MIP que você deseja modificar, você pode usar as ferramentas de desenho para modificá-la sem alterar o conteúdo de outros níveis de MIP. As ferramentas de desenho estão disponíveis na barra de ferramentas **Editor de Imagens**. Depois de selecionar uma ferramenta, você pode alterar suas propriedades na janela **Propriedades**. Para obter informações sobre as ferramentas de desenho e suas propriedades, consulte [Editor de Imagens](../designers/image-editor.md).  
  
> [!NOTE]
>  Se você não precisar modificar o conteúdo dos níveis de MIP individuais – como você poderia fazer para obter certos efeitos – é recomendável que você gere mipmaps com base na textura de origem no momento do build. Isso ajuda a assegurar que os níveis de MIP fiquem em sincronia com a textura de origem porque modificações em um nível de MIP não são propagadas automaticamente para outros níveis. Para obter mais informações sobre como gerar mipmaps no momento do build, consulte [Como exportar uma textura que contenha mipmaps](../designers/how-to-export-a-texture-that-contains-mipmaps.md).  
  
## <a name="see-also"></a>Consulte também  
 [Como criar uma textura básica](../designers/how-to-create-a-basic-texture.md)



