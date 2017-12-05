---
title: Passo a passo do Azure para as Ferramentas do Visual Studio para Unity | Microsoft Docs
ms.custom: 
ms.date: 10/19/2017
ms.reviewer: crdun
ms.suite: 
ms.technology: tgt-pltfrm-cross-plat
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7921D4C7-5526-42F5-8E03-82D3E33A893F
author: dantogno
ms.author: v-davian
manager: crdun
ms.openlocfilehash: a7e12508537a3bcda1df7997ba9e390b75b9beaf
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/09/2017
---
# <a name="using-azure-easy-tables-with-unity-walkthrough"></a>Passo a passo de como usar o Azure Easy Tables com o Unity

![Captura de tela de jogo de exemplo](media/vstu_azure-test-sample-game-image2.png)

## <a name="introduction"></a>Introdução

O Azure oferece uma solução escalonável para armazenar telemetria e outros dados de jogos na nuvem. Com o lançamento do Unity 2017, o suporte do Unity para o .NET 4.6 torna a integração ao Azure mais simples do que nunca ao permitir o uso do SDK do Azure Mobile Client.

Estas etapas guiarão você pelo processo de configurar um projeto do Unity que aproveite o Azure para salvar dados de telemetria e placar de líderes na nuvem.

> [!NOTE]
> Este projeto requer o tempo de execução de script "experimental" do .NET 4.6 no Unity 2017. [A Unity declarou que em breve esse será o padrão](https://forum.unity3d.com/threads/future-plans-for-the-mono-runtime-upgrade.464327/), no entanto, por ora, ele ainda está rotulado como "experimental" e você poderá ter problemas.

> Este passo a passo documenta um exemplo para se conectar a um back-end do Aplicativo Móvel do Azure de um build de PC do Unity. No momento da redação deste documento, existem problemas conhecidos que impedem este projeto de funcionar em plataformas Mac e Android. Embora sejam problemas conhecidos que serão corrigidos, não sabemos quando isso ocorrerá. Para saber mais, acesse o [fórum de script experimental](https://forum.unity3d.com/forums/experimental-scripting-previews.107/) do Unity.

## <a name="download-the-completed-project"></a>Baixar o projeto concluído

O projeto concluído está disponível no GitHub. No entanto, o passo a passo assumirá que você está começando em um projeto novo, vazio e fornecerá links para baixar ativos quando necessário.

## <a name="walkthrough-steps"></a>Etapas de passo a passo

1. [Configurar Tabelas Fáceis no Azure](visual-studio-tools-for-unity-azure-configure.md)
2. [Criar Tabelas Fáceis](visual-studio-tools-for-unity-azure-setup.md)
3. [Preparar o ambiente de desenvolvimento](visual-studio-tools-for-unity-azure-prepare.md)
4. [Criar classes de modelo de dados](visual-studio-tools-for-unity-azure-data.md)
5. [Implementar o MobileServiceClient do Azure](visual-studio-tools-for-unity-azure-mobile-client.md)
6. [Atualizar o repositório de certificados de segurança do Unity Mono](visual-studio-tools-for-unity-azure-security.md)
7. [Testar a conexão de cliente](visual-studio-tools-for-unity-azure-connection.md)
7. [Importar ativos do jogo de exemplo](visual-studio-tools-for-unity-azure-game-assets.md)
8. [Testar o jogo de exemplo](visual-studio-tools-for-unity-azure-game.md)
9. [Explicação sobre o RaceScene](visual-studio-tools-for-unity-azure-racescene.md)
10. [Explicação sobre HeatmapScene](visual-studio-tools-for-unity-azure-heatmapscene.md)
11. [Explicação sobre LeaderboardScene](visual-studio-tools-for-unity-azure-leaderboardscene.md)


## <a name="next-step"></a>Próximas etapas
* [Configurar Tabelas Fáceis no Azure](visual-studio-tools-for-unity-azure-configure.md)
