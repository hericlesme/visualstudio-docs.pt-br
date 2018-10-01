---
title: Como exportar um sombreador | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0bd48bf4-9792-4456-a545-e462a2be668d
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: bc5969dfd900f3974a1a70e5adefdea6d13ad648
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47463895"
---
# <a name="how-to-export-a-shader"></a>Como exportar um sombreador
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [como: exportar um sombreador](https://docs.microsoft.com/visualstudio/designers/how-to-export-a-shader).  
  
Este documento demonstra como usar o Designer de Sombreador para exportar um sombreador da DGSL (Directed Graph Shader Language) para poder usá-lo em seu aplicativo.  
  
 Este documento demonstra esta atividade:  
  
-   Exportar um sombreador  
  
## <a name="exporting-a-shader"></a>Exportar um sombreador  
 Depois de criar um sombreador usando o Designer de Sombreador é necessário exportá-lo em um formato que seja compreendido pela API de gráficos antes de usá-lo em seu aplicativo. Você pode exportar um sombreador de maneiras diferentes para atender a necessidades diferentes.  
  
#### <a name="to-export-a-shader"></a>Para exportar um sombreador  
  
1.  No [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], abra uma arquivo do **Visual Shader Graph (.dgsl)**.  
  
     Se você não tem um arquivo do **Visual Shader Graph (.dgsl)** para abrir, crie um conforme descrito em [Como criar um sombreador de cor básico](../designers/how-to-create-a-basic-color-shader.md).  
  
2.  Na barra de ferramentas do **Designer de Sombreador**, escolha **Avançado**, **Exportar** e **Exportar como**. A caixa de diálogo **Exportar Sombreador** é exibida.  
  
3.  Na lista suspensa **Salvar como tipo**, escolha o formato que você deseja exportar.  
  
     Aqui estão os formatos que você pode escolher:  
  
     **Sombreador de Pixel HLSL (\*.hlsl)**  
     Exporta o sombreador como código-fonte HLSL (High Level Shader Language). Essa opção possibilita modificar o sombreador posteriormente, mesmo depois que ele for implantado em um aplicativo. Isso pode tornar mais fácil depurar e corrigir o código com base em problemas de usuários finais, mas também torna mais fácil para um usuário modificar o sombreador de formas indesejáveis, por exemplo, para obter uma vantagem injusta em um jogo de competição. Isso também pode aumentar o tempo de carregamento do sombreador.  
  
     **Sombreador de Pixel Compilado (\*.cso)**  
     Exporta o sombreador como um código de bytes HLSL. Essa opção possibilita modificar o sombreador posteriormente, mesmo depois que ele for implantado em um aplicativo. Isso pode tornar mais fácil depurar e corrigir o código com base em problemas de usuários finais, mas como o sombreador é pré-compilado, ele não incorre em sobrecarga adicional de tempo de execução quando o sombreador é carregado pelo aplicativo. Usuários suficientemente habilidosos ainda podem modificar o sombreador de formas indesejáveis, mas a compilação do sombreador torna isso muito mais difícil.  
  
     **Cabeçalho C++ (\*.h)**  
     Exporta o sombreador como um cabeçalho de estilo C que define uma matriz de bytes que contém o código de bytes HLSL. Essa opção pode fazer com que a depuração e correção do código com base em problemas do usuário final se tornem mais demoradas porque o aplicativo tem que ser recompilado para testar a correção. No entanto, como esta opção torna difícil, mas não impossível, a modificação do sombreador depois de ser implantado em um aplicativo, ela apresenta maior dificuldade para um usuário que deseja modificar o sombreador de formas indesejáveis.  
  
4.  Na caixa de combinação **Nome de arquivo**, especifique um nome para o sombreador exportado e, em seguida, escolha o botão **Salvar**.  
  
## <a name="see-also"></a>Consulte também  
 [Como criar um sombreador de cor básico](../designers/how-to-create-a-basic-color-shader.md)   
 [Designer de Sombreador](../designers/shader-designer.md)



