---
title: Integração ao Portal de Administração de Assinaturas do Visual Studio depois que sua organização tiver sido migrada
Author: evanwindom
Ms.author: jaunger
Manager: evelynp
Ms.date: 07/12/2018
Ms.topic: Get-Started-Article
Description: Learn how to successfully onboard your organization for Visual Studio subscriptions after migrating to the administration portal.
Ms.prod: vs-subscription
Ms.technology: vs-subscriptions
Searchscope: VS Subscription
ms.openlocfilehash: c6f0f3de58f2f9f7d532a7b1b84520644fbdb1c7
ms.sourcegitcommit: 25a62c2db771f938e3baa658df8b1ae54a960e4f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/24/2018
ms.locfileid: "39234750"
---
# <a name="onboarding-to-the-visual-studio-subscriptions-administration-portal-after-your-organization-was-migrated"></a>Integração ao Portal de Administração de Assinaturas do Visual Studio depois que sua organização tiver sido migrada 

Se você tiver gerenciado as Assinaturas do Visual Studio no VLSC (Centro de Serviços de Licenciamento por Volume) e tiver visitado recentemente o site para gerenciar assinaturas, observará que o gerenciamento de assinatura não está mais disponível no VLSC. Seu processo para gerenciar assinaturas seria semelhante a isso:

![Assinaturas do VLSC](_img/post-migration-onboarding/vlsc-subscriptions.png)

Ao chegar à página de assinaturas, você provavelmente clicaria no link a seguir. 

![Link de resumo da relação](_img/post-migration-onboarding/relationship-summary-link.png)

Isso antes o levaria para a página onde as assinaturas são gerenciadas.   No entanto, as assinaturas agora são gerenciadas por meio de um novo portal chamado de Portal de Administração de Assinaturas do Visual Studio.  Há várias etapas que precisam ser realizadas pelo contato principal ou de notificações para o Contrato de Licenciamento por Volume da sua organização. No caso em que o contato principal ou de notificações não tiver concluído esse processo ou não estiver mais disponível, há alguns cenários possíveis. O exemplo a seguir irá direcioná-lo pelas etapas necessárias para obter acesso ao gerenciamento de assinaturas. 

Você pode encontrar um dos vários cenários a seguir:
1.  [O contato principal não concluiu o processo de integração](#Onboarding-not-completed-by-Primary-Contact)<sup>1</sup> 
2.  [O contato principal concluiu a integração, mas não o adicionou como administrador.  Suas credenciais foram listadas no VLSC.](#Primary-Contact-did-not-provide-you-administrator-access) 
3.  [O contato principal concluiu a integração, mas não o adicionou como administrador e suas credenciais não foram listadas no VLSC](#Your-credentials-were-not-listed-in-VLSC-prior-to-migration)  

<sup>1</sup> Se você for o contato principal ou de notificações e não tiver concluído o processo de integração, precisará seguir as etapas no cenário um para configurar a sua organização. 

Veja a seguir exemplos das telas que você deverá ver e as etapas que poderá tomar para cada um dos cenários. 

## <a name="onboarding-not-completed-by-primary-contact"></a>A integração não foi concluída pelo contato principal

Se o contato principal não tiver concluído a experiência de integração, você deverá ver a tela a seguir. Se você tiver acesso ao [VLSC (Centro de Serviços de Licenciamento por Volume)](https://www.microsoft.com/Licensing/servicecenter/default.aspx), poderá concluir esse processo e obter acesso para gerenciar assinaturas. Você precisará do [Número público de cliente (PCN)](find-pcn.md) da sua organização, que pode ser encontrado no VLSC. 

Se o contato principal não tiver concluído o processo de integração, basta digitar o [PCN](find-pcn.md) no campo e selecionar "Enviar convite". 

![Enviar Email de Convite](_img/post-migration-onboarding/send-invitation.png)

Depois de clicar no botão para enviar o convite, você receberá um email com um link exclusivo para concluir o processo de integração. Você precisará clicar no link no email, entrar com seu endereço de email e mais uma vez, digitar o PCN. O link exclusivo do email é o que permite que você tenha acesso ao Portal de Administração de Assinaturas do Visual Studio. Você poderá acessar e gerenciar assinaturas. 

![Email de sucesso](_img/post-migration-onboarding/email-success.png)


## <a name="primary-contact-did-not-provide-you-administrator-access"></a>O contato principal não forneceu a você acesso de administrador

Se o seu contato principal tiver concluído o processo de integração e suas credenciais estavam anteriormente no VLSC, mas o contato principal não tiver fornecido acesso, você verá a notificação a seguir depois de entrar no [Portal de Administração de Assinaturas do Visual Studio](https://manage.visualstudio.com/).  Para se tornar administrador, você precisará entrar em contato com um dos superadministradores da sua organização listados na tela.

![Lista de administradores](_img/post-migration-onboarding/admin-list.png)

## <a name="your-credentials-were-not-listed-in-vlsc-prior-to-migration"></a>Suas credenciais não estavam listadas no VLSC antes da migração

Se seu contato principal tiver concluído a integração, mas não o tiver adicionado como usuário e suas credenciais não tiverem sido listadas anteriormente no VLSC, você verá a notificação abaixo ao tentar acessar o [Portal de Administração de Assinaturas do Visual Studio](https://manage.visualstudio.com/). Você precisará entrar em contato com seu [Contato principal](find-primary-contact.md) para ter acesso ao portal. 

![Não consegue encontrar seu nome](_img/post-migration-onboarding/cant-find-you.png)