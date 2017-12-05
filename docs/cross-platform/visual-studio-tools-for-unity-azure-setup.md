---
title: "Passo a passo de configuração do Azure para as Ferramentas do Visual Studio para Unity | Microsoft Docs"
ms.custom: 
ms.date: 10/19/2017
ms.reviewer: crdun
ms.suite: 
ms.technology: tgt-pltfrm-cross-plat
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: FFE17FC6-0B47-4A00-A125-01BD49E3873C
author: dantogno
ms.author: v-davian
manager: crdun
ms.openlocfilehash: 447f32c2e736084a08223b56f4188ca7c8abeea5
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/09/2017
---
# <a name="create-easy-tables"></a>Criar Tabelas Fáceis

Agora que você tem um Aplicativo Móvel no Azure com as Tabelas Fáceis inicializada, é hora de criar as tabelas que manterão o controle dos dados enviados de um jogo em Unity.

## <a name="setup-the-crash-heatmap-table"></a>Configuração da tabela de mapa de calor de colisões

1. No Portal do Azure, clique em Todos os recursos e, em seguida, selecione o Aplicativo Móvel que você configurou para as Tabelas Fáceis nas etapas anteriores.

  ![Selecionar Aplicativo Móvel](media/vstu_azure-setup-table-schema-image1.png)

2. Role para baixo até o cabeçalho **MOBILE** e selecione **Tabelas Fáceis**. Não deve haver mais nenhum aviso sobre a inicialização de seu aplicativo para Tabelas Fáceis.  

  ![Selecionar Tabelas Fáceis](media/vstu_azure-setup-table-schema-image2.png)

3. Clique no botão **Adicionar**.

  ![Clique em Adicionar](media/vstu_azure-setup-table-schema-image3.png)

4. Nomeie a tabela como "**CrashInfo**" e clique em **OK**. Deixe o restante das opções com suas configurações padrão.

  > [!WARNING]
  > Esse nome deverá corresponder ao nome da classe de modelo de dados criada posteriormente no passo a passo.

  ![Nomear e clicar em OK](media/vstu_azure-setup-table-schema-image4.png)

5. Uma notificação anunciará quando a nova tabela tiver sido criada.

> [!NOTE]
> Com as Tabelas Fáceis, o esquema da tabela é, na verdade, criado dinamicamente conforme os dados são adicionados. Isso significa que as colunas de dados adequadas não precisam ser configuradas manualmente durante esta etapa.

## <a name="setup-the-leaderboard-table"></a>Configurar a tabela de placar de líderes

1. Volte para a folha de Tabelas Fáceis e clique em **Adicionar** para adicionar uma segunda tabela.

  ![Adicionar uma segunda tabela](media/vstu_azure-setup-table-schema-image10.png)

2. Nomeie a nova tabela como "**HighScoreInfo**" e clique em **OK**. Deixe o restante das opções com as configurações padrão.

  > [!WARNING]
  > Esse nome deverá corresponder ao nome da classe de modelo de dados criada posteriormente no passo a passo.

  ![Nomear e clicar em OK](media/vstu_azure-setup-table-schema-image11.png)

3. Uma notificação anunciará quando a nova tabela tiver sido criada.


## <a name="next-step"></a>Próximas etapas

* [Preparar o ambiente de desenvolvimento](visual-studio-tools-for-unity-azure-prepare.md)
