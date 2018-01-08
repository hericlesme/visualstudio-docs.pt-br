---
title: "Implantação do VS Shell | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: be8f2ffe-a322-4ac0-9c9e-873bd28e5d5e
caps.latest.revision: "2"
author: alancameronwills
ms.author: awills
manager: douge
ms.workload: multiple
ms.openlocfilehash: aeb4ca2153d4c060862d31e53202312f061bf1ef
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="vs-shell-deployment"></a>Implantação do VS Shell
Um shell isolado permite que você determine que o Visual Studio funcionalidade que você precisa interagir com a linguagem específica de domínio e como essa solução deve ser exibidos. Para obter mais informações sobre o shell do Visual Studio isolado, consulte [Personalizando o Shell isolado](../extensibility/customizing-the-isolated-shell.md). Você pode encontrar mais informações sobre como personalizar o shell isolado no [Personalizando o Shell isolado](http://msdn.microsoft.com/en-us/d75463cd-1155-42e4-8b7a-046ed6becbbf).  
  
### <a name="to-set-a-visual-studio-shell-as-the-deployment-target"></a>Para definir um Shell do Visual Studio como o destino de implantação  
  
1.  No **DslPackage** projeto, abra **source.extension.tt**.  
  
2.  Em `<SupportedProducts>` inserir:  
  
    ```  
    <IsolatedShell Version="1.0">MyIsolatedShell</IsolatedShell>  
    ```  
  
     Substituir *MyIsolatedShell* com o nome do seu pacote de shell isolado.