---
title: Passo a passo dos ativos de jogos do Azure para as Ferramentas do Visual Studio para Unity | Microsoft Docs
ms.custom: 
ms.date: 10/19/2017
ms.reviewer: crdun
ms.suite: 
ms.technology: tgt-pltfrm-cross-plat
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: C06FAB2E-F592-4EFF-B96A-58858C92DCEB
author: dantogno
ms.author: v-davian
manager: crdun
ms.workload:
- azure
- unity
ms.openlocfilehash: 19b98dc472b9e01529725b95133d289edff6334d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="import-sample-game-assets"></a>Importar ativos do jogo de exemplo

Agora que a funcionalidade básica foi testada e demonstrou que funciona, é hora de importar os ativos do jogo de exemplo.

## <a name="import-package"></a>Importar pacote

1. Baixe o [pacote de ativos de jogo de exemplo](https://github.com/dantogno/UnityAzureSample/blob/master/Azure%20Easy%20tables%20sample%20game%20assets.unitypackage).

2. Verifique se o projeto do Unity está aberto e, em seguida, navegue para o local do download e clique duas vezes no arquivo. Isso abrirá a caixa de diálogo de importação no Unity.

3. Clique em **Todos** e, em seguida, clique em **Importar**. Aguarde até que as barras de progresso resultante sejam concluídas.

  ![Importar pacote](media/vstu_azure-import-sample-assets-image1.png)

## <a name="add-scenes-to-build-settings"></a>Adicionar cenas às Configurações de Build

Depois que a importação dos arquivos for concluída, os arquivos de cena necessários deverão ser adicionados às Configurações de Build do projeto do Unity.

1. Na janela Projeto do Unity, navegue até o diretório **Ativos do jogo de exemplo do Azure Easy Tables/Cenas**.

2. No menu do Unity, selecione **Arquivo > Configurações de Build...** . Isso exibirá a caixa de diálogo Configurações de Build.

3. Arraste os arquivos **HeatmapScene**, **LeaderboardScene**, **MenuScene** e **RaceScene** da janela Projeto para a seção **Cenas em Compilação** da caixa de diálogo Configurações de Build.

  ![Importar pacote](media/vstu_azure-import-sample-assets-image2.png)

4. No menu do Unity, selecione **Arquivo > Salvar Projeto** para garantir que as configurações de build sejam salvas.

## <a name="next-step"></a>Próximas etapas

* [Testar o jogo de exemplo](visual-studio-tools-for-unity-azure-game.md)