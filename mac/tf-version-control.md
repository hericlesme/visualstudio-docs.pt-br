---
title: Controle de versão do TF
description: Conexão com o Team Foundation Server ou ao Visual Studio Team Services com o controle de versão do Team Foundation.
author: conceptdev
ms.author: crdun
ms.date: 05/03/2018
ms.topic: article
ms.technology: vs-ide-general
ms.assetid: 52D3D26A-4D01-4FD1-AAA1-AE7D7BD39746
ms.openlocfilehash: 101f002f6c311fe5aaefa78c246602fd45514603
ms.sourcegitcommit: 2597236a481afbaf1ad4915743898ee1aee49760
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/10/2018
ms.locfileid: "43223976"
---
# <a name="connecting-to-team-foundation-version-control"></a>Conexão com o controle de versão do Team Foundation 

> [!NOTE]
> **Observação**: o suporte para o Controle de Versão do Team Foundation atualmente está em versão prévia e algumas funcionalidades ainda não estão funcionando totalmente. Adoraríamos receber seus comentários sobre problemas na [Comunidade de Desenvolvedores](https://developercommunity.visualstudio.com/spaces/41/index.html). Mais alterações ainda estão por vir!

O VSTS (Visual Studio Team Services) e o TFS (Team Foundation Server) fornecem dois modelos de controle de versão: o Git, que o controle de versão distribuído, e o TFVC (Controle de Versão do Team Foundation), que é o controle de versão centralizado. Este artigo fornece uma visão geral e um ponto de partida para usar o Controle de Versão do Team Foundation com o Visual Studio para Mac.

## <a name="requirements"></a>Requisitos

* Visual Studio Community, Professional ou Enterprise para Mac versão 7.5 ou posterior.
* Visual Studio Team Services ou Team Foundation Server 2013 e posterior.
* Um projeto no Visual Studio Team Services ou no Team Foundation Server, configurado para usar o Controle de Versão do Team Foundation.

## <a name="installation"></a>Instalação

No Visual Studio para Mac, escolha **Visual Studio > Extensões…** no menu. Na guia **Galeria**, selecione **Controle de Versão > Controle de Versão do Team Foundation para o TFS e VSTS** e clique em **Instalar...**:

  ![Gerenciador de extensões](media/tfvc-install.png) 

Siga os prompts para instalar a extensão. Depois de instalá-la, reinicie o IDE.

## <a name="updating-the-extension"></a>Atualizando a extensão

Periodicamente, são feitas atualizações na extensão do TFVC. Para acessar as atualizações, escolha **Visual Studio > Extensões...** no menu e selecione a guia **Atualizações**. Selecione a extensão na lista e pressione o botão **Atualizar**:

  ![Gerenciador de extensão mostrando a atualização](media/tfvc-update.png) 

Pressione **Instalar** na próxima caixa de diálogo para desinstalar o pacote antigo e instalar um novo.

Para obter informações sobre as novidades em cada versão, confira as [Notas de Versão](https://docs.microsoft.com/visualstudio/releasenotes/vs2017-mac-preview-relnotes#team-foundation-version-control-extension--release-notes).

## <a name="using-the-add-in"></a>Usando o suplemento

Depois de instalar a extensão, selecione o item de menu **Controle de Versão > TFS/VSTS > Abrir do Repositório Remoto…** 

Escolha o Visual Studio Team Services ou o Team Foundation Server para começar e pressione **Continuar**:

  ![Conectar a um servidor](media/tfvc-choose-server-type.png)

### <a name="vsts-authentication"></a>Autenticação do VSTS

Quando você seleciona um projeto que está hospedado no VSTS, é solicitado que você insira os detalhes da conta Microsoft:

  ![Conectar a um servidor do VSTS](media/tfvc-vsts-login.png)

### <a name="tfs-authentication"></a>Autenticação do TFS

Para conectar-se ao TFS, insira os detalhes do servidor e suas credenciais da conta. Insira um domínio para usar a autenticação NTLM, caso contrário, deixe em branco para usar a autenticação básica. Selecione **Adicionar Servidor**: 

![Entrar em um servidor TFS](media/tfvc-login.png)

## <a name="selecting-a-project"></a>Selecionando um projeto

Depois que você se autenticar com êxito, será exibida uma lista de repositórios associados à conta na caixa de diálogo **Abrir do Controle do Código-Fonte**:

  ![Caixa de diálogo Abrir do Controle do Código-Fonte com projetos exibidos](media/tfvc-vsts-projects.png)

Essa caixa de diálogo é organizada com os seguintes nós:

- Conta ou coleção do VSTS – exibe todas as contas conectadas à conta Microsoft com as quais você entrou
- Projetos de Equipe – em cada VSTS, você pode ter vários projetos de equipe. Um projeto de equipe é onde o código-fonte, itens de trabalho e builds automatizadas são hospedados.

Neste ponto, você pode pesquisar e filtrar pelo nome de um projeto ou de uma conta.

### <a name="adding-a-new-server"></a>Adicionando um novo servidor

Para adicionar um novo servidor à lista, pressione o botão **Adicionar Host** na caixa de diálogo **Abrir do Controle do Código-Fonte**:

![Botão de adição realçado para adicionar o novo servidor à lista](media/tfvc-add-new-server.png)

Selecione o provedor na lista e insira suas credenciais:

![Caixa de diálogo mostrando a opção de provedor de controle do código-fonte](media/tfvc-add-new-creds.png)

## <a name="creating-a-new-workspace"></a>Criando um novo espaço de trabalho

Para começar a trabalhar com um projeto, você precisa ter um _espaço de trabalho_. Se você ainda não tem um espaço de trabalho, crie um na caixa de combinação **Espaço de trabalho** na caixa de diálogo **Abrir do Controle do Código-Fonte**:

![Opção da caixa de combinação Criar espaço de trabalho](media/tfvc-create-new-workspace.png)

Defina o nome e o caminho local para seu novo espaço de trabalho e selecione **Criar Espaço de Trabalho**:

![Inserindo um nome e um caminho local para o novo espaço de trabalho](media/tfvc-local-workspace.png)

## <a name="using-the-source-code-explorer"></a>Usando o Source Code Explorer

Depois de criar um espaço de trabalho e mapear o projeto, você poderá começar a trabalhar com o _Source Code Explorer_.

Para abrir o Source Code Explorer selecione **Controle de Versão > TFS/VSTS > Source Control Explorer**:

![Item de menu para abrir o Source Code Explorer](media/tfvc-source-control-explorer.png)

O Source Code Explorer permite que você navegue em todos os projetos mapeados e em seus arquivos e pastas. Ele também permite que você execute todas as ações básicas de controle do código-fonte, como:

- Obter a versão mais recente
- Obter uma versão específica
- Fazer check-out e check-out de arquivos
- Bloquear e desbloquear arquivos
- Adicionar, excluir e renomear arquivos
- Exibir histórico
- Comparar alterações.

Muitas dessas ações estão disponíveis por meio de ações de contexto no projeto:

![Ações de menu de contexto para um projeto](media/tfvc-sourcecode-actions.png)

## <a name="managing-workspaces"></a>Gerenciando espaços de trabalho

Se você ainda não criou um espaço de trabalho, conforme a descrição na seção [Criando um espaço de trabalho](#creating-a-new-workspace), o Source Code Explorer estará vazio:

![Source Code Explorer vazio](media/tfvc-setup-empty-sce.png) 

Para configurar seu projeto remoto com um espaço de trabalho local, use as seguintes etapas:

1. Selecione o **Servidor** na caixa de combinação.
1. Observe que não há "nenhum espaço de trabalho" e o caminho local está como "Não Mapeado". Selecione o link **Não Mapeado** para exibir a caixa de diálogo **Criar Espaço de Trabalho**.
1. Forneça um nome para o espaço de trabalho e, em seguida, clique em **Adicionar Pasta de Trabalho** para mapear o projeto para uma pasta local no seu computador:
    
    ![Caixa de diálogo Criar Espaço de Trabalho, mostrando as opções padrão](media/tfvc-workspace1.png) 

1. Selecione a pasta "$" para mapear todos os projetos de equipe em seu servidor para o mesmo espaço de trabalho ou selecione um projeto individual e clique em **OK**:
    
    ![Navegue para a caixa de diálogo de pasta mostrando todos os projetos](media/tfvc-workspace2.png) 

1. Selecione o local em seu computador local para onde deseja mapear os projetos e clique em **Selecionar Pasta**.
1. Confirme os detalhes do novo espaço de trabalho pressionando **OK**
    
    ![Caixa de diálogo Criar Espaço de Trabalho, com a pasta de trabalho adicionada](media/tfvc-workspace3.png) 

Depois que o espaço de trabalho for configurado, ele poderá ser alterado ou removido clicando no botão **Gerenciar Espaços de Trabalho** no Source Code Explorer.

![Gerenciar Espaços de Trabalho](media/tfvc-workspace4.png)

## <a name="troubleshooting"></a>Solução de problemas

### <a name="problems-using-basic-authentication"></a>Problemas no uso da autenticação básica

As opções a seguir podem ser usadas para a autenticação no servidor:

- OAuth
- Basic
- NTLM

Para usar a autenticação básica é necessário habilitar **Credenciais de autenticação alternativas** no VSTS, seguindo as etapas abaixo:

1. Entre como o proprietário da conta em sua conta do VSTS (https://{youraccount}.visualstudio.com).
2. Na barra de ferramentas da conta, selecione o ícone de engrenagem e escolha **Política**:
    
    ![Opção de configurações de política selecionada](media/tfvc-auth2.png) 

3. Examine as configurações de conexão do aplicativo. Altere essas configurações, com base em suas políticas de segurança:
    
    ![Opção de configurações de política selecionada](media/tfvc-auth.png)  

### <a name="i-do-not-see-anything-in-tfvc"></a>Não vejo nada no TFVC

Para definir o TFVC (Controle de Versão do Team Foundation) no computador de desenvolvimento, você **precisa** criar um espaço de trabalho, conforme a descrição na seção [Gerenciando espaços de trabalho](#managing-workspaces).

No Source Control Explorer, pressione o botão **Gerenciar Espaços de Trabalho**. Siga as etapas para mapear o projeto de equipe para uma pasta no computador de desenvolvimento.

### <a name="i-do-not-see-any--all-of-my-projects"></a>Não vejo um/nenhum dos meus projetos

Após a autenticação, você deverá ver a lista de projetos. Por padrão, apenas os projetos do TFS são mostrados. Para ver outros tipos de projetos, marque a caixa "Ver todos os projetos".

Tenha em mente que os projetos que estão no servidor não serão exibidos se você não tiver os privilégios corretos.

#### <a name="i-am-getting-the-error-cannot-create-the-workspace-please-try-again"></a>Estou recebendo o erro "Não é possível criar o espaço de trabalho. Tente novamente"

Ao tentar [criar um espaço de trabalho](#creating-a-new-workspace), verifique se as seguintes condições são atendidas:

- Nenhum uso de caracteres inválidos no nome do espaço de trabalho.
- O nome deve ter menos de 64 caracteres.
- O caminho local não pode ser usado por outros espaços de trabalho.