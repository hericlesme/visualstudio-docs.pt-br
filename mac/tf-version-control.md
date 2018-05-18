---
title: Controle de versão do TF
description: Conexão com o Team Foundation Server ou ao Visual Studio Team Services com o controle de versão do Team Foundation.
author: asb3993
ms.author: amburns
ms.date: 05/03/2018
ms.topic: article
ms.technology: vs-ide-general
ms.assetid: 52D3D26A-4D01-4FD1-AAA1-AE7D7BD39746
ms.openlocfilehash: f892209faeb06ca703d28016457e9ba4ab86ccda
ms.sourcegitcommit: 33c954fbc8e05f7ba54bfa2c0d1bc1f9bbc68876
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/08/2018
---
# <a name="connecting-to-team-foundation-version-control"></a>Conexão com o controle de versão do Team Foundation 

O VSTS (Visual Studio Team Services) e o TFS (Team Foundation Server) fornecem dois modelos de controle de versão: o Git, que o controle de versão distribuído, e o TFVC (Controle de Versão do Team Foundation), que é o controle de versão centralizado. Este artigo fornece uma visão geral e um ponto de partida para usar o Controle de Versão do Team Foundation com o Visual Studio para Mac.

> [!NOTE]
> **Observação**: o suporte para o Controle de Versão do Team Foundation atualmente está em versão prévia e algumas funcionalidades ainda não estão funcionando totalmente. Mais alterações ainda estão por vir!

## <a name="requirements"></a>Requisitos

* Visual Studio para Mac versão 7.5 ou posterior.
* Visual Studio Team Servers ou Team Foundation Server 2013 e posteriores
* Um projeto no Visual Studio Team Services ou no Team Foundation Server, configurado para usar o Controle de Versão do Team Foundation.

## <a name="installation"></a>Instalação

No Visual Studio para Mac, escolha o menu **Visual Studio > Extensões…** Pesquise "Controle de versão do TF" e instale a extensão do **Controle de Versão do Team Foundation**. Reinicie o IDE quando solicitado.

## <a name="using-the-add-in"></a>Usando o suplemento

Após instalar a extensão, selecione o menu **Controle de Versão > TFS/VSTS > Conectar-se ao Controle de Versão do Team Foundation…** 

![Adicionar um servidor TFVC](media/tfvc-add-remove-server.png)


Escolha o Visual Studio Team Services ou o Team Foundation Server para começar:

![Conecte-se com um servidor TFVC](media/tfvc-choose-server-type.png)

Insira suas credenciais: 

![Faça logon em um servidor TFVC](media/tfvc-login.png)

Em seguida, escolha os projetos que deseja acessar: 

![Escolher projetos](media/tfvc-choose-projects.png)

Para continuar, feche as caixas de diálogo e, em seguida, use o menu **Controle de Versão > TFS/VSTS > Source Control Explorer** para pesquisar o código-fonte.

> [!WARNING]
> **Problema conhecido**: nesta versão prévia, na primeira vez em que abrir o Source Control Explorer, você precisará criar um novo espaço de trabalho.

![Source Explorer](media/tfvc-source-explorer.png)

No Source Code Explorer, você pode pesquisar o código-fonte no servidor e executar as seguintes ações:

- Gerenciar espaços de trabalho (criar, editar ou excluir).
- Navegar na estrutura do projeto.
- Mapear projetos.
- Obter projetos.
- Bloquear e desbloquear arquivos.
- Renomear arquivos.
- Excluir arquivos.
- Adicionar novo arquivo.
- Fazer check-out.
- Fazer check-in.
- Exibir alterações de histórico.
- Comparar alterações.

## <a name="creating-a-new-workspace"></a>Criando um novo espaço de trabalho

No Source Control Explorer, clique no botão **Gerenciar Espaços de Trabalho**. 

![Gerenciar Espaços de Trabalho](media/tfvc-manage-workspaces.png)

Clique em **Adicionar** para criar um novo espaço de trabalho.

![Criar Espaço de Trabalho](media/tfvc-create-workspace.png)

Forneça um nome para o espaço de trabalho e, em seguida, clique em **Adicionar Pasta de Trabalho** para mapear o projeto para uma pasta local no computador.

Quando terminar, clique em **OK** e, em seguida, feche a caixa de diálogo Gerenciar Espaços de Trabalho. Agora, você está pronto para obter arquivos por meio do Source Code Explorer e para começar a trabalhar.