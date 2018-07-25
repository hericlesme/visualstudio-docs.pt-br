---
title: Benefício WhiteSource Bolt | Microsoft Docs
author: evanwindom
ms.author: jaunger
manager: evelynp
ms.date: 01/11/2017
ms.topic: Get-Started-Article
description: Saiba como ativar a assinatura do WhiteSource Bolt incluída em sua assinatura do Visual Studio.
ms.prod: vs-subscription
ms.technology: vs-subscriptions
searchscope: VS Subscription
ms.openlocfilehash: 37b71d51a62ab83f604c084ec2b5a1fda7594c14
ms.sourcegitcommit: 4667e6ad223642bc4ac525f57281482c9894daf4
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/20/2018
ms.locfileid: "36280293"
---
#  <a name="whitesource-bolt-in-visual-studio-subscriptions"></a>WhiteSource Bolt em assinaturas do Visual Studio

Encontre e corrija vulnerabilidades de software livre e gere relatórios de licença e inventário abrangentes de todos os componentes de software livre em seu build. Algumas assinaturas do Visual Studio incluem seis meses de acesso gratuito.

## <a name="activation-steps"></a>Etapas de ativação

1.  Para ativar o benefício WhiteSource Bolt, entre em [https://my.visualstudio.com/benefits](https://my.visualstudio.com/benefits?wt.mc_id=o~msft~docs).

2.  Localize o bloco WhiteSource Bolt na seção de Ferramentas e clique no link **Obter Código** na parte inferior do bloco do benefício.

    ![Bloco do benefício WhiteSource Bolt](_img\vs-whitesource\vs-whitesource-tile.png)

2.  Você receberá uma notificação exibindo o código de ativação.  **Copie o código para a área de transferência** e, em seguida, clique em **Ativar**.

    ![Código do benefício WhiteSource ](_img\vs-whitesource\vs-whitesource-code.png)

3.  Na página da Web do WhiteSource, clique no botão **Ativar** ou role para baixo até a seção da página **Ativar sua conta**.

    ![Ativar o benefício WhiteSource](_img\vs-whitesource\vs-whitesource-activate-page-cropped.png)

4.  Na seção da página **Ativar sua conta**, você será guiado para realizar quatro etapas:

    - [Instalar](https://marketplace.visualstudio.com/items?itemName=whitesource.ws-bolt) a extensão WhiteSource Bolt do Microsoft Visual Studio Marketplace. Se você não tem permissões para instalar as extensões, confira [Instalar extensões gratuitas para o VSTS](/vsts/marketplace/install-vsts-extension?view=vsts).

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

## <a name="eligibility"></a>Qualificação

| Nível de Assinatura                                                 |     Canais                                            | Benefício                                                          | Renovável?    |
|--------------------------------------------------------------------|---------------------------------------------------------|------------------------------------------------------------------|---------------|
| Visual Studio Enterprise (Padrão, nuvem anual)   | VL, Azure, Retail, NFR<sup>1</sup> selecionado | Seis meses       |  Sim          |
| Visual Studio Professional (Padrão, nuvem anual) | VL, Azure, Retail                                       | Indisponível                                                           |NA         |
| Visual Studio Test Professional (Padrão)                         | VL, Retail                                              | Não disponível                                             |  NA         |
| Plataformas MSDN (Padrão)                                          | VL, Retail                                              | Não disponível                                              | NA         |
| Visual Studio Dev Essentials | NA  | Não disponível |NA |
| Visual Studio Enterprise, Visual Studio Professional (nuvem mensal) | Azure                                       | Não disponível                                                           |NA|

<sup>1</sup>  *Inclui: Microsoft Partner Network (Enterprise).  Exclui: NFR (Proibida a revenda), VSIP (Visual Studio Industry Partner), FTE, MCT Software & Services Developer, BizSpark, Imagine, MVP (Microsoft Valued Partner), RD (diretor regional), MCT Software & Services, Microsoft Partner Network (Professional).*

Não tem certeza de qual assinatura você está usando?  Conecte-se ao [https://my.visualstudio.com/subscriptions](https://my.visualstudio.com/subscriptions?wt.mc_id=o~msft~docs) para ver todas as assinaturas atribuídas ao seu endereço de email. Se não vir todas as suas assinaturas, talvez você tenha uma ou mais atribuídas a outro endereço de email.  Você precisará entrar com esse endereço de email para ver as assinaturas.

## <a name="support-resources"></a>Recursos de suporte

-  Precisa de ajuda com o WhiteSource Bolt?  Converse com um representante do Bolt WhiteSource em https://www.whitesourcesoftware.com/vse_whitesource_bolt/
-  Para obter assistência com vendas, assinaturas, contas e cobrança para Assinaturas do Visual Studio, entre em contato com o [Suporte a Assinaturas](https://visualstudio.microsoft.com/subscriptions/support/) do Visual Studio.
-  Tem alguma pergunta sobre o IDE do Visual Studio, o Visual Studio Team Services ou outros produtos ou serviços do Visual Studio?  Acesse o [Suporte do Visual Studio](https://visualstudio.microsoft.com/support/).