---
title: Como compartilhar um ambiente de desenvolvimento | Microsoft Docs
author: ghogen
ms.author: ghogen
ms.date: 3/12/2018
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-azure
description: Desenvolvimento rápido no Kubernetes com contêineres e microsserviços no Azure
keywords: Docker, Kubernetes, Azure, AKS, Serviço de Contêiner do Azure, contêineres
manager: douge
ms.openlocfilehash: 43d23caa039340345372076d02b3c4989cde5b01
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="share-a-development-environment"></a>Compartilhar um ambiente de desenvolvimento

Com o Connected Environment, você pode compartilhar seu ambiente de desenvolvimento com outras pessoas da equipe. Cada desenvolvedor pode trabalhar em seu próprio espaço sem medo de interromper outras pessoas. Além disso, trabalhar em conjunto em um único ambiente pode permitir que você teste o código de ponta a ponta sem precisar criar códigos fictícios nem simular dependências. Confira o guia [Saiba mais sobre o desenvolvimento em equipe](../get-started-nodejs-06.md) para obter mais informações.

Para configurar um ambiente para vários desenvolvedores:
1. [Crie um Connected Environment no Azure](../get-started.md). Você precisará ter acesso de Proprietário ou Colaborador na assinatura do Azure selecionada.
1. Configure o **grupo de recursos** do ambiente para [conceder acesso de Colaborador](https://docs.microsoft.com/en-us/azure/active-directory/role-based-access-control-configure) a cada membro da equipe. Você pode verificar o grupo de recursos de um ambiente executando este comando: `vsce env list`
1. Peça para os membros da equipe **selecionarem o ambiente** a ser usado para o desenvolvimento.
     * **Linha de comando ou VS Code**: para ver os Connected Environments aos quais você tem acesso: `vsce env list`. Para selecionar um ambiente: `vsce env select`.
     * **IDE do Visual Studio**: abra um projeto no Visual Studio e selecione **Connected Environment para AKS** na lista suspensa de configurações de inicialização. Na caixa de diálogo exibida, selecione um ambiente de desenvolvimento existente.

![Menu suspenso de configurações do Visual Studio](../images/LaunchSettings.png)