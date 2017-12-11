---
title: "Benefício WhiteSource Bolt"
Author: evanwindom
Ms.author: jaunger
Manager: evelynp
Ms.date: 10/3/2017
Ms.topic: Get-Started-Article
Description: Learn how to activate the WhiteSource Bolt subscription included with your Visual Studio subscription.
Ms.prod: vs-subscription
Ms.technology: vs-subscriptions
Searchscope: VS Subscription
ms.openlocfilehash: e8b5e08178ac35e57350052e6a9076dc0f80dca6
ms.sourcegitcommit: b7d3b90d0be597c9d01879338dd2678c881087ce
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/01/2017
---
#  <a name="activating-the-whitesource-bolt-benefit-in-visual-studio-subscriptions"></a>Ativando o benefício WhiteSource Bolt nas assinaturas do Visual Studio

Encontre e corrija vulnerabilidades de software livre e gere relatórios de licença e inventário abrangentes de todos os componentes de software livre em seu build.  Sua assinatura Enterprise inclui uma assinatura gratuita de seis meses. 

1.  Para usar o benefício WhiteSource Bolt, clique no link **Obter Código** na parte inferior do bloco do benefício.    

    ![Bloco do benefício WhiteSource Bolt](_img\vs-whitesource\vs-whitesource-tile.png)

2.  Você receberá uma notificação exibindo o código de ativação.  **Copie o código para a área de transferência** e, em seguida, clique em **Ativar**. 

    ![Código do benefício WhiteSource ](_img\vs-whitesource\vs-whitesource-code.png)

3.  Na página da Web do WhiteSource, clique no botão **Ativar** ou role para baixo até a seção da página **Ativar sua conta**.  

    ![Ativar o benefício WhiteSource](_img\vs-whitesource\vs-whitesource-activate-page-cropped.png)

4.  Na seção da página **Ativar sua conta**, você será guiado para realizar quatro etapas:
- [Instalar](https://marketplace.visualstudio.com/items?itemName=whitesource.ws-bolt) a extensão WhiteSource Bolt do Microsoft Visual Studio Marketplace. Se você não tem permissões para instalar as extensões, visite [esta página](https://www.visualstudio.com/en-us/docs/marketplace/get-vsts-extensions#request).

    Clique no botão verde **Instalar** se você estiver usando o VSTS ou no botão **Baixar** se estiver usando o Team Foundation Server.  Neste exemplo, usaremos o VSTS. 

    ![Extensão de instalação do benefício WhiteSource](_img\vs-whitesource\vs-whitesource-download-install.png)

- Em seguida, selecione a conta do VSTS que você deseja usar e clique em **Confirmar**.  (Se você ainda não tiver configurado o VSTS, visite a página [Benefícios](https://my.visualstudio.com/benefits) e ative o benefício VSTS.)

    ![Confirmar conta do benefício WhiteSource](_img\vs-whitesource\vs-whitesource-confirm-account.png)

- Você receberá uma confirmação de que a extensão está instalada e pronta para ser usada.  Clique em **Começar a usar** para retornar à página do WhiteSource Bolt e continuar.  

    ![Instalação do benefício WhiteSource concluída](_img\vs-whitesource\vs-whitesource-install-complete.png)

5.  Abra o painel do projeto do VSTS (Visual Studio Team Services), clique no menu **Build e lançamento** e escolha **WhiteSource Bolt**.

    ![Adicionar extensão do benefício WhiteSource](_img\vs-whitesource\vs-whitesource-installed-cropped.png)

6. Cole o código de ativação no bloco do benefício WhiteSource Bolt e clique em **Ativar**. Cada código de ativação pode ser usado para ativar um único projeto. 

    ![Código de ativação do benefício WhiteSource](_img\vs-whitesource\vs-whitesource-activate-code-cropped.png)

7.  Agora a ativação está concluída e você terá 180 dias restantes na sua assinatura. 
8.  Será necessário adicionar a extensão do WhiteSource Bolt como uma das etapas de build.  Há um vídeo disponível na [página do WhiteSource Bolt](https://www.whitesourcesoftware.com/whitesource_bolt_visualstudio_2017/#activate) que mostra como fazer isso.  
9. Depois de executar o build, os seguintes relatórios e painéis abrangentes serão gerados automaticamente:
- Painel de vulnerabilidades de segurança
- Relatório de vulnerabilidades de segurança
- Relatório de bibliotecas desatualizadas
- Painel de riscos e conformidade de licença
- Relatório de inventário
