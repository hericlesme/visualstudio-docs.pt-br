---
title: Implantação do VS Shell
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: e7df1991832e954def71a6cee5bd5516dfd4e961
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
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