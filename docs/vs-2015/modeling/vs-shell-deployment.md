---
title: Implantação do VS Shell | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: be8f2ffe-a322-4ac0-9c9e-873bd28e5d5e
caps.latest.revision: 4
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: e1a1bd92d1a0b91aa01d940695cd780f7e63c098
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47475334"
---
# <a name="vs-shell-deployment"></a>Implantação do VS Shell
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [implantação do VS Shell](https://docs.microsoft.com/visualstudio/modeling/vs-shell-deployment).  
  
Um shell isolado permite que você determine quais Visual Studio funcionalidade que você precisa interagir com sua linguagem específica do domínio e como essa solução deve ser exibidos. Para obter mais informações sobre o shell isolado do Visual Studio, consulte [personalizar o Shell isolado](../extensibility/customizing-the-isolated-shell.md). Você pode encontrar mais informações sobre como personalizar o shell isolado no [personalizar o Shell isolado](http://msdn.microsoft.com/en-us/d75463cd-1155-42e4-8b7a-046ed6becbbf).  
  
### <a name="to-set-a-visual-studio-shell-as-the-deployment-target"></a>Para definir um Shell do Visual Studio como o destino de implantação  
  
1.  No **DslPackage** projeto, abra **source.extension.tt**.  
  
2.  Sob `<SupportedProducts>` inserir:  
  
    ```  
    <IsolatedShell Version="1.0">MyIsolatedShell</IsolatedShell>  
    ```  
  
     Substitua *MyIsolatedShell* com o nome do seu pacote de shell isolado.



