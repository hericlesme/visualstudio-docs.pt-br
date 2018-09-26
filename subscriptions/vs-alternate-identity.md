---
title: Identidades para assinantes do Visual Studio
author: evanwindom
ms.author: jaunger
manager: evelynp
ms.date: 04/10/2018
ms.topic: conceptual
description: Como adicionar uma identidade alternativa à sua Assinatura do Visual Studio para ser usada com o Azure DevOps Services e o Azure
ms.prod: vs-subscription
ms.technology: vs-subscriptions
searchscope: vs subscription
ms.openlocfilehash: 15b364cc8375d4e0e64b20ad7e8a6b19ba4140f5
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44283555"
---
# <a name="identities-for-visual-studio-subscribers"></a>Identidades para assinantes do Visual Studio

Quando você ativar sua assinatura do Visual Studio, será vinculada a identidade (ou o logon) que você usou durante a ativação com a assinatura do Visual Studio. Dessa forma, você poderá ser reconhecido no [portal do assinante do Visual Studio](https://my.visualstudio.com?wt.mc_id=o~msft~docs), no Azure DevOps Services e no Azure.

No Azure DevOps Services, o status da sua Assinatura do Visual Studio é verificado sempre que você faz logon e você recebe automaticamente as funcionalidades de cada conta da qual é membro.
Como essas funcionalidades são incluídas como um benefício do assinante, você pode ser adicionado gratuitamente como membro de qualquer conta do Azure DevOps Services ao usar uma identidade vinculada à sua Assinatura do Visual Studio.

No Azure, o status da assinatura do Visual Studio é verificado quando você ativa o [crédito mensal do Azure](https://azure.microsoft.com/pricing/member-offers/credit-for-visual-studio-subscribers/), que é um benefício do assinante.

No [portal do assinante do Visual Studio](https://my.visualstudio.com?wt.mc_id=o~msft~docs), talvez você possa adicionar uma **alternativa identidade**, além da identidade usada durante a ativação. No momento, é permitido adicionar uma identidade alternativa quando uma conta da Microsoft é usada para ativar a assinatura. Dessa forma, também é possível adicionar uma conta corporativa ou de estudante (usada para fazer logon no Visual Studio, no Office 365 ou na rede corporativa ou de estudante), o que permite acessar o Azure DevOps Services usando sua conta pessoal e sua conta corporativa ou de estudante.

## <a name="add-an-alternate-account-to-your-visual-studio-subscription"></a>Adicionar uma conta alternativa à sua assinatura do Visual Studio

Adicionar uma conta alternativa à sua Assinatura do Visual Studio permite que você acesse os benefícios da assinatura, como o Azure DevOps Services e o Azure, com uma identidade diferente daquela à qual a assinatura está atribuída. No passado, essa funcionalidade estava disponível somente se a sua assinatura do VS (Visual Studio) fosse atribuída a uma conta da Microsoft (MSA). Nós estendemos essa funcionalidade para contas corporativas ou de estudante no Azure AD (Azure Active Directory).

Isso não fornece uma cópia da assinatura para a outra conta; apenas possibilita acessar os dois benefícios com a conta alternativa.

Para todas as assinaturas, é possível adicionar uma "conta corporativa ou de estudante" para que você possa usar essa conta com benefícios que exigem um logon (VS IDE, Azure DevOps Services e Azure).


### <a name="add-the-alternate-account"></a>Adicionar a conta alternativa


1. Entre no portal do Assinante do Visual Studio com sua Conta Microsoft (https://my.visualstudio.com).

2. Vá atá **Assinaturas**.

    > [!div class="mx-imgBorder"]
    > ![Adicionar conta alternativa – ir para assinaturas no VS](_img/vs-alternate-identity/my-vs-subscriptions.png)

3. Escolha **Adicionar conta alternativa**.
    > [!div class="mx-imgBorder"]
    > ![Escolher adicionar conta alternativa](_img/vs-alternate-identity/choose-add-alternate-account.png)

4. Adicione sua conta corporativa ou de estudante.
    > [!div class="mx-imgBorder"]
    > ![Adicionar conta corporativa ou de estudante](_img/vs-alternate-identity/enter-alternate-account-my-visual-studio-com-portal.png)

5. Use sua conta corporativa ou de estudante para entrar no Azure DevOps Services (https://{suaconta}.visualstudio.com).
    > [!div class="mx-imgBorder"]
    > ![Use sua conta corporativa ou de estudante](_img/vs-alternate-identity/sign-in-with-alternate-account.png)

Sua conta alternativa é adicionada à Assinatura do Visual Studio, permitindo que as duas identidades utilizem os benefícios da assinatura que exigem que você entre com a conta alternativa (IDE, Azure DevOps Services e Azure).

## <a name="faq"></a>Perguntas Frequentes

### <a name="q--why-doesnt-azure-devops-services-recognize-me-as-a-visual-studio-subscriber"></a>P: Por que o Azure DevOps Services não me reconhece como um assinante do Visual Studio?

R: O Azure DevOps Services deverá reconhecer sua assinatura automaticamente quando você entrar usando sua identidade principal ou alternativa. Caso contrário, você poderá tentar algumas coisas:

* Verifique se você tem uma Assinatura do Visual Studio ativa que [inclua o Azure DevOps Services como um benefício](vs-azure-devops.md).

* Confirme se você está usando um logon ou uma identidade que seja a identidade principal ou alternativa da sua assinatura do Visual Studio.

* Visite o [portal do assinante do Visual Studio](https://my.visualstudio.com?wt.mc_id=o~msft~docs) pelo menos uma vez antes de entrar no Azure DevOps Services.

Se o Azure DevOps Services ainda não reconhecer sua assinatura, [contate o suporte](https://visualstudio.microsoft.com/team-services/support/)
