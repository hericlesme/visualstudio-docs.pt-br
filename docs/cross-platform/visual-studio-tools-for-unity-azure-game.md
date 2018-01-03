---
title: Passo a passo do jogo do Azure para as Ferramentas do Visual Studio para Unity | Microsoft Docs
ms.custom: 
ms.date: 10/19/2017
ms.reviewer: crdun
ms.suite: 
ms.technology: tgt-pltfrm-cross-plat
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: DA86FC7F-E456-4DFC-84BF-D780421508B9
author: dantogno
ms.author: v-davian
manager: crdun
ms.workload:
- azure
- unity
ms.openlocfilehash: 7d0a7da4093b8f90ab76dee55f1ec9ad6dc21679
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="test-the-sample-game"></a>Testar o jogo de exemplo

O jogo de exemplo é um jogo de corrida simples que registra dados sobre o comportamento do jogador e os armazena no Azure Easy Tables. O jogo de exemplo também inclui cenas que leem os dados do Azure e os visualizam para o jogador.

Esta seção explicará de forma simples como jogar o jogo de exemplo e garantir que ele está funcionando corretamente. As próximas seções apresentarão mais detalhes, explicando como funciona o jogo de exemplo.

## <a name="starting-the-game"></a>Iniciar o jogo

1. Na janela do Projeto do Unity, navegue até a pasta **Ativos/Ativos do jogo de exemplo do Azure Easy Tables/Cenas**.

2. Clique duas vezes em **MenuScene** para abri-lo.

3. Na janela Jogo do Unity, clique no **menu suspenso de taxa de proporção** e selecione **16:9**.

  ![Definir a taxa de proporção](media/vstu_azure-test-sample-game-image1.png)

4. Clique no botão **Reproduzir** para executar o jogo no editor do Unity.


## <a name="complete-a-race"></a>Concluir uma corrida

Antes de exibir o placar de líderes ou o mapa de calor, é melhor criar alguns dados de exemplo concluindo a corrida pelo menos uma vez.

1. Com o jogo em execução no editor do Unity, clique no botão **Correr!** para iniciar uma nova corrida.

2. Use o **WASD** ou as **teclas de direção** para dirigir o carro e conclua uma volta em sentido horário na pista. Por exemplo, bata em algumas paredes ao longo da pista. A saída depurada no console do Unity deve indicar quando uma colisão foi registrada.

  >[!NOTE]
  > Se você virar o carro e não conseguir continuar, clique em **Reiniciar**. Os dados são enviados para o Azure somente depois que uma volta é completada.

  ![Iniciar uma corrida](media/vstu_azure-test-sample-game-image2.png)

3. Depois de cruzar a linha de chegada quadriculada, o jogo deverá exibir uma mensagem de **Fim**. Neste ponto, os dados de colisões serão enviados ao Azure.

4. Caso tenha completado uma das dez voltas mais rápidas, você será solicitado a inserir um nome para registrar uma pontuação alta. Insira seu nome e clique em **Enviar**.

  ![Iniciar uma corrida](media/vstu_azure-test-sample-game-image3.png)

## <a name="view-the-heatmap"></a>Exibir o mapa de calor

1. Clique no botão **Exibir Mapa de Calor de Colisões** na cena da corrida ou selecione **Mapa de Calor de Colisões** no menu principal.

2. A cena do mapa de calor carrega os dados da tabela CrashInfo no Azure e exibe uma esfera vermelha transparente nos locais em que os jogadores colidiram com as paredes do circuito de corrida. Se ocorrerem várias colisões em uma área com sobreposição, as esferas devem aparecer mais brilhantes.

  ![Mapa de calor](media/vstu_azure-test-sample-game-image4.png)

## <a name="view-the-leaderboard"></a>Exibir o placar de líderes

1. Clique no botão **Placar de Líderes** na cena da corrida ou no menu principal.

2. A cena do placar de líderes exibe os dados de pontuação mais alta da tabela HighScoreInfo do Azure e mostra o nome do jogador e o tempo da volta para cada entrada de pontuação alta.

  ![Placar de líderes](media/vstu_azure-test-sample-game-image5.png)

## <a name="next-step"></a>Próximas etapas

* [Explicação sobre o RaceScene](visual-studio-tools-for-unity-azure-racescene.md)
