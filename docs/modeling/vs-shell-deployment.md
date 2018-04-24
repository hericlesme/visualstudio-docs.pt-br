---
title: Implantação do VS Shell
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 816997f971e90ddd27f8e24cdc1857559e04ff70
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/20/2018
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