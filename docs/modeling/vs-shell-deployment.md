---
title: "Implantação do VS Shell | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.topic: article
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: eb5446c8c3090624f327c234a1b518dc1928b6c9
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/09/2018
---
# <a name="vs-shell-deployment"></a>Implantação do VS Shell

Um shell isolado permite que você determine que o Visual Studio funcionalidade que você precisa interagir com a linguagem específica de domínio e como essa solução deve ser exibidos. Para obter mais informações sobre o shell do Visual Studio isolado, consulte [Personalizando o Shell isolado](../extensibility/customizing-the-isolated-shell.md).

## <a name="to-set-a-visual-studio-shell-as-the-deployment-target"></a>Para definir um Shell do Visual Studio como o destino de implantação
  
1.  No **DslPackage** projeto, abra **source.extension.tt**.  
  
2.  Em `<SupportedProducts>` inserir:  
  
    ```  
    <IsolatedShell Version="1.0">MyIsolatedShell</IsolatedShell>  
    ```  
  
     Substituir *MyIsolatedShell* com o nome do seu pacote de shell isolado.