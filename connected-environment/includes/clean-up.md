---
ms.topic: include
ms.openlocfilehash: 94e82185b05900101f91e4b368bb30d2aaceac03
ms.sourcegitcommit: 928885ace538bef5b25961358d4f166d648f196a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/27/2018
ms.locfileid: "32030813"
---
## <a name="clean-up"></a>Limpar
Para excluir completamente um Connected Environment do Azure, incluindo todos os serviços em execução que ele contém, use o comando `vsce env rm`. Tenha em mente que essa ação é irreversível.

O exemplo a seguir lista os Connected Environments em sua assinatura ativa do Azure e, em seguida, exclui o ambiente chamado 'myenv' que está no grupo de recursos 'myenv-rg'.

```cmd
vsce env list
vsce env rm --name myenv --resource-group myenv-rg
```

