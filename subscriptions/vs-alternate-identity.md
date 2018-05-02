---
title: Identidades para assinantes do Visual Studio
author: evanwindom
ms.author: jaunger
manager: evelynp
ms.date: 04/10/2018
ms.topic: conceptual
description: Como adicionar uma identidade alternativa à sua assinatura do Visual Studio para ser usada com o VSTS e o Azure
ms.prod: vs-subscription
ms.technology: vs-subscriptions
searchscope: vs subscription
ms.openlocfilehash: 9a83f78f35b9533c554c81cecd181c00eca05568
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="identities-for-visual-studio-subscribers"></a>Identidades para assinantes do Visual Studio

Quando você ativar sua assinatura do Visual Studio, será vinculada a identidade (ou o logon) que você usou durante a ativação com a assinatura do Visual Studio. Dessa forma, você poderá ser reconhecido no [portal do assinante do Visual Studio](https://my.visualstudio.com?wt.mc_id=o~msft~docs), no VSTS (Visual Studio Team Services) e no Azure.

No VSTS, o status da sua assinatura do Visual Studio é verificado sempre que você faz logon e você recebe automaticamente os recursos de cada conta da qual é membro.
Como esses recursos são incluídos como um benefício do assinante, você pode ser adicionado gratuitamente como membro de qualquer conta do VSTS ao usar uma identidade vinculada à sua assinatura do Visual Studio.

No Azure, o status da assinatura do Visual Studio é verificado quando você ativa o [crédito mensal do Azure](https://azure.microsoft.com/pricing/member-offers/credit-for-visual-studio-subscribers/), que é um benefício do assinante.

No [portal do assinante do Visual Studio](https://my.visualstudio.com?wt.mc_id=o~msft~docs), talvez você possa adicionar uma **alternativa identidade**, além da identidade usada durante a ativação. No momento, é permitido adicionar uma identidade alternativa quando uma conta da Microsoft é usada para ativar a assinatura. Dessa forma, também é possível adicionar uma conta corporativa ou de estudante (usada para fazer logon no Visual Studio, no Office 365 ou na rede corporativa ou de estudante), o que permite acessar o VSTS usando sua conta pessoal e sua conta corporativa ou de estudante.

## <a name="add-an-alternate-account-to-your-visual-studio-subscription"></a>Adicionar uma conta alternativa à sua assinatura do Visual Studio

Adicionar uma conta alternativa à sua assinatura do Visual Studio permite que você acesse os benefícios da assinatura, como o VSTS (Visual Studio Team Services) e o Azure, com uma identidade diferente daquela à qual a assinatura está atribuída. No passado, essa funcionalidade estava disponível somente se a sua assinatura do VS (Visual Studio) fosse atribuída a uma conta da Microsoft (MSA). Nós estendemos essa funcionalidade para contas corporativas ou de estudante no Azure AD (Azure Active Directory).

Isso não fornece uma cópia da assinatura para a outra conta; apenas possibilita acessar os dois benefícios com a conta alternativa.

Para todas as assinaturas, é possível adicionar uma "conta corporativa ou de estudante" para que você possa usar essa conta com benefícios que exigem um logon (VS IDE, VSTS e Azure).

### <a name="prerequisites"></a>Pré-requisitos

* [Permissões de proprietário de conta ou de administrador de coleção de projeto no VSTS](https://docs.microsoft.com/en-us/vsts/accounts/faq-add-delete-users#find-owner).

* Para usar a conta alternativa, sua assinatura associada à conta deverá incluir o Visual Studio Team Services ou o Microsoft Azure.

> [!Note]
> Você pode continuar usando os benefícios de assinatura com a ID alternativa, mas a assinatura ainda está associada à sua conta original.

### <a name="add-the-alternate-account"></a>Adicionar a conta alternativa

1. Entre no Visual Studio com sua conta da Microsoft (https://{suaconta}.visualstudio.com).

2. Vá atá **Assinaturas**.

  ![Adicionar conta alternativa – ir para assinaturas no VS](_img/vs-alternate-identity/my-vs-subscriptions.png)

3. Escolha **Adicionar conta alternativa**.

  ![Escolher adicionar conta alternativa ](_img/vs-alternate-identity/choose-add-alternate-account.png)

4. Adicione sua conta corporativa ou de estudante.

  ![Adicionar conta corporativa ou de estudante](_img/vs-alternate-identity/enter-alternate-account-my-visual-studio-com-portal.png)

5. Use sua conta corporativa ou de estudante para entrar no Visual Studio (https://{youraccount}.visualstudio.com).

  ![Use sua conta corporativa ou de estudante](_img/vs-alternate-identity/sign-in-with-alternate-account.png)

  Sua conta alternativa é adicionada à assinatura do Visual Studio, permitindo que as duas identidades utilizem os benefícios da assinatura que exigem que você entre com a conta alternativa (IDE, VSTS e Azure).

Para obter mais informações sobre como adicionar uma conta alternativa, consulte a página [Perguntas Frequentes sobre meu Visual Studio](https://www.visualstudio.com/my/myvsfaq#alternate).

## <a name="faq"></a>Perguntas Frequentes

### <a name="q--why-doesnt-vsts-recognize-me-as-a-visual-studio-subscriber"></a>P: Por que o VSTS não me reconhece como um assinante do Visual Studio?
R: O VSTS deverá reconhecer sua assinatura automaticamente quando você entrar usando sua identidade principal ou alternativa. Caso contrário, você poderá tentar algumas coisas:

* Verifique se você tem uma assinatura ativa do Visual Studio que [inclua o VSTS como um benefício](vs-vsts.md).

* Confirme se você está usando um logon ou uma identidade que seja a identidade principal ou alternativa da sua assinatura do Visual Studio.

* Visite o [portal do assinante do Visual Studio](https://my.visualstudio.com?wt.mc_id=o~msft~docs) pelo menos uma vez antes de entrar no VSTS.

Se o VSTS ainda não reconhecer sua assinatura, [contate o suporte](https://www.visualstudio.com/team-services/support/)
