---
title: Controle de versão do TF
description: Conexão com o Team Foundation Server ou ao Visual Studio Team Services com o controle de versão do Team Foundation.
author: asb3993
ms.author: amburns
ms.date: 05/03/2018
ms.topic: article
ms.technology: vs-ide-general
ms.assetid: 52D3D26A-4D01-4FD1-AAA1-AE7D7BD39746
ms.openlocfilehash: 58d0fc5c31b02574661f8b86a4ae8bcaf393be3a
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34693767"
---
# <a name="connecting-to-team-foundation-version-control"></a>Conexão com o controle de versão do Team Foundation 

> [!NOTE]
> **Observação**: o suporte para o Controle de Versão do Team Foundation atualmente está em versão prévia e algumas funcionalidades ainda não estão funcionando totalmente. Adoraríamos receber seus comentários sobre problemas na [Comunidade de Desenvolvedores](https://developercommunity.visualstudio.com/spaces/41/index.html). Mais alterações ainda estão por vir!

O VSTS (Visual Studio Team Services) e o TFS (Team Foundation Server) fornecem dois modelos de controle de versão: o Git, que o controle de versão distribuído, e o TFVC (Controle de Versão do Team Foundation), que é o controle de versão centralizado. Este artigo fornece uma visão geral e um ponto de partida para usar o Controle de Versão do Team Foundation com o Visual Studio para Mac.

## <a name="requirements"></a>Requisitos

* Visual Studio para Mac versão 7.5 ou posterior.
* Visual Studio Team Services ou Team Foundation Server 2013 e posterior
* Um projeto no Visual Studio Team Services ou no Team Foundation Server, configurado para usar o Controle de Versão do Team Foundation.

## <a name="installation"></a>Instalação

No Visual Studio para Mac, escolha **Visual Studio > Extensões…** no menu. Na guia **Galeria**, selecione **Controle de Versão > Controle de Versão do Team Foundation para o TFS e VSTS** e clique em **Instalar...**:

  ![Gerenciador de extensões](media/tfvc-install.png) 

Siga os prompts para instalar a extensão. Depois de instalá-la, reinicie o IDE.

## <a name="using-the-add-in"></a>Usando o suplemento

Depois de instalar a extensão, selecione o item de menu **Controle de Versão > TFS/VSTS > Conectar-se ao Controle de Versão do Team Foundation…**. Clique em **Adicionar** para adicionar uma nova conta: 

![Adicionar um servidor TFVC](media/tfvc-add-remove-server.png)

Escolha o Visual Studio Team Services ou o Team Foundation Server para começar:

![Conecte-se com um servidor TFVC](media/tfvc-choose-server-type.png)

Insira suas credenciais e clique em **Fazer logon**: 

![Faça logon em um servidor TFVC](media/tfvc-login.png)

Depois de fazer logon com êxito, selecione os projetos que deseja acessar e pressione **OK**: 

![Escolher projetos](media/tfvc-choose-projects.png)

Selecione o item de menu **Controle de Versão > TFS/VSTS > Source Control Explorer** para abrir o Source Control Explorer, permitindo que você procure a origem.

> [!IMPORTANT]
> **Problema conhecido**: nesta versão prévia, na primeira vez em que abrir o Source Control Explorer, você precisará [criar um espaço de trabalho](#creating-a-new-workspace).

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

Clique no botão **Adicionar** para criar um espaço de trabalho.

![Criar Espaço de Trabalho](media/tfvc-create-workspace.png)

Forneça um nome para o espaço de trabalho e, em seguida, clique em **Adicionar Pasta de Trabalho** para mapear o projeto para uma pasta local no computador.

Quando terminar, clique em **OK** e, em seguida, feche a caixa de diálogo Gerenciar Espaços de Trabalho. Agora, você está pronto para obter arquivos por meio do Source Code Explorer e para começar a trabalhar.

## <a name="troubleshooting"></a>Solução de problemas

### <a name="problems-using-basic-authentication"></a>Problemas no uso da autenticação básica

Há várias opções diferentes disponíveis para realizar a autenticação em um servidor:

- OAuth
- Basic
- NTLM

Para usar a autenticação básica, é necessário habilitar **Credenciais de autenticação alternativas** no VSTS, seguindo as etapas abaixo:

1. Entre como o proprietário da conta em sua conta do VSTS (https://{youraccount}.visualstudio.com).
2. Na barra de ferramentas da conta, selecione o ícone de engrenagem e **Política**: ![opção Configurações de política selecionada](media/tfvc-auth2.png) 
3. Examine as configurações de conexão do aplicativo. Altere essas configurações, com base nas políticas de segurança: ![opção Configurações de política selecionada](media/tfvc-auth.png)  

### <a name="i-do-not-see-anything-in-tfvc"></a>Não vejo nada no TFVC

Para configurar o TFVC (Controle de Versão do Team Foundation) no computador de desenvolvimento, é **necessário** criar um espaço de trabalho, conforme descrito na seção [Criando um espaço de trabalho](#creating-a-new-workspace).

No Source Control Explorer, pressione o botão **Gerenciar Espaços de Trabalho**. Siga as etapas para mapear o projeto de equipe para uma pasta no computador de desenvolvimento.

### <a name="i-do-not-see-any--all-of-my-projects"></a>Não vejo um/nenhum dos meus projetos

Após a autenticação, você deverá ver a lista de projetos. Por padrão, apenas os projetos do TFS são mostrados. Para ver outros tipos de projetos, marque a caixa "Ver todos os projetos".

Tenha em mente que os projetos que estão no servidor não serão exibidos se você não tiver os privilégios corretos.

#### <a name="i-am-getting-the-error-cannot-create-the-workspace-please-try-again"></a>Estou recebendo o erro "Não é possível criar o espaço de trabalho. Tente novamente"

Ao tentar [criar um espaço de trabalho](#creating-a-new-workspace), verifique se as seguintes condições são atendidas:

- Nenhum uso de caracteres inválidos no nome do espaço de trabalho.
- O nome deve ter menos de 64 caracteres.
- O caminho local não pode ser usado por outros espaços de trabalho.