---
title: "Benefício WhiteSource Bolt | Microsoft Docs"
Author: evanwindom
Ms.author: jaunger
Manager: evelynp
Ms.date: 1/11/2017
Ms.topic: Get-Started-Article
Description: Learn how to activate the WhiteSource Bolt subscription included with your Visual Studio subscription.
Ms.prod: vs-subscription
Ms.technology: vs-subscriptions
Searchscope: VS Subscription
ms.openlocfilehash: fe8e731e26765ec17b56383e04362efa25b2f141
ms.sourcegitcommit: b18844078a30d59014b48a9c247848dea188b0ee
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2018
---
#  <a name="whitesource-bolt-in-visual-studio-subscriptions"></a>WhiteSource Bolt em assinaturas do Visual Studio

## <a name="overview"></a>Visão geral

Encontre e corrija vulnerabilidades de software livre e gere relatórios de licença e inventário abrangentes de todos os componentes de software livre em seu build.  Assinaturas do Visual Studio selecionadas incluem seis meses de acesso gratuito. 

## <a name="eligibility"></a>Qualificação

| Nível de Assinatura/Programa                                                  | Benefício               | Renovável?                                                         |
|-------------------------------------------------------------------------------|-----------------------|--------------------------------------------------------------------|
| Visual Studio Enterprise Standard                                             | Seis meses              | Sim                                                                |
| Visual Studio Enterprise anual                                               | Seis meses              | Sim                                                                |
| Visual Studio Enterprise mensal                                              | Não disponível         |                                                                    |
| Visual Studio Professional Standard                                           | Não disponível         |                                                                    |
| Visual Studio Professional anual                                             | Não disponível         |                                                                    | 
| Visual Studio Professional mensal                                            | Não disponível         |                                                                    |
| Visual Studio Test Pro                                                        | Não disponível         |                                                                    |
| Plataformas MSDN                                                                | Não disponível         |                                                                    |
| Visual Studio Dev Essentials                                                  | Não disponível         |                                                                    |
| Visual Studio Enterprise – NFR<sup>1</sup>                                               | Não disponível         |                                                                    |
| Visual Studio Enterprise - FTE                                                | Não disponível         |                                                                    |
| Visual Studio Enterprise ‒ Microsoft Partner Network                          | Seis meses              | Sim                                                                |
| Visual Studio Professional – Microsoft Partner Network                        | Não disponível         |                                                                    |
| Visual Studio Enterprise – Imagine (Standard)                                 | Não disponível         |                                                                    |
| Visual Studio Enterprise – Imagine (Premium)                                  | Não disponível         |                                                                    |
| Visual Studio Enterprise – BizSpark                                           | Não disponível         |                                                                    |
| Microsoft Certified Trainer ‒ Software e Serviços                             | Não disponível         |                                                                    |
| Microsoft Certified Trainer ‒ Desenvolvedor de Software e Serviços                   | Não disponível         |                                                                    |

<sup>1</sup>  *Inclui NFR (Proibida a revenda), MVP (Microsoft Valued Partner), RD (Diretor de Região), VSIP (Visual Studio Industry Partner)*  

Não tem certeza de qual assinatura você está usando?  Conecte-se a [https://my.visualstudio.com/subscriptions](https://my.visualstudio.com/subscriptions?wt.mc_id=o~msft~docs) para ver todas as assinaturas atribuídas a seu endereço de email. Se não vir todas as suas assinaturas, talvez você tenha uma ou mais atribuídas a outro endereço de email.  Você precisará entrar com esse endereço de email para ver as assinaturas. 

## <a name="activation-steps"></a>Etapas de Ativação

1.  Para ativar o benefício WhiteSource Bolt, entre em [https://my.visualstudio.com/benefits](https://my.visualstudio.com/benefits?wt.mc_id=o~msft~docs).

2.  Localize o bloco WhiteSource Bolt na seção de Ferramentas e clique no link **Obter Código** na parte inferior do bloco do benefício.    

    ![Bloco do benefício WhiteSource Bolt](_img\vs-whitesource\vs-whitesource-tile.png)

2.  Você receberá uma notificação exibindo o código de ativação.  **Copie o código para a área de transferência** e, em seguida, clique em **Ativar**. 

    ![Código do benefício WhiteSource ](_img\vs-whitesource\vs-whitesource-code.png)

3.  Na página da Web do WhiteSource, clique no botão **Ativar** ou role para baixo até a seção da página **Ativar sua conta**.  

    ![Ativar o benefício WhiteSource](_img\vs-whitesource\vs-whitesource-activate-page-cropped.png)

4.  Na seção da página **Ativar sua conta**, você será guiado para realizar quatro etapas:
    - [Instalar](https://marketplace.visualstudio.com/items?itemName=whitesource.ws-bolt) a extensão WhiteSource Bolt do Microsoft Visual Studio Marketplace. Se você não tem permissões para instalar as extensões, visite [esta página](https://www.visualstudio.com/docs/marketplace/get-vsts-extensions#request).

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

## <a name="faq"></a>Perguntas Frequentes
*Verifique aqui se há atualizações*

## <a name="support-resources"></a>Recursos de suporte
-  Precisa de ajuda com o WhiteSource Bolt?  Converse com um representante do WhiteSource Bolt ao vivo em https://www.whitesourcesoftware.com/vse_whitesource_bolt/ 
-  Para obter assistência com vendas, assinaturas, contas e cobrança para Assinaturas do Visual Studio, entre em contato com o [Suporte a Assinaturas](https://www.visualstudio.com/subscriptions/support/) do Visual Studio.
-  Tem alguma pergunta sobre o IDE do Visual Studio, o Visual Studio Team Services ou outros produtos ou serviços do Visual Studio?  Acesse o [Suporte do Visual Studio](https://www.visualstudio.com/support/). 

