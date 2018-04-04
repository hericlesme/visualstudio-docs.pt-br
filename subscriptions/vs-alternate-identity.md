---
title: Identidades para assinantes do Visual Studio
Author: evanwindom
Ms.author: jaunger
Manager: evelynp
Ms.date: 3/15/2018
Ms.topic: Get-Started-Article
Description: How to add an alternate identity for your Visual Studio subscription, to use for VSTS and Azure.
Ms.prod: vs-subscription
Ms.technology: vs-subscriptions
Searchscope: VS Subscription
ms.openlocfilehash: 70bfd305ec35b562fb722fb853016c3df4240ff8
ms.sourcegitcommit: 67374acb6d24019a434d96bf705efdab99d335ee
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/22/2018
---
# <a name="identities-for-visual-studio-subscribers"></a>Identidades para assinantes do Visual Studio

Quando você ativar sua assinatura do Visual Studio, será vinculada a identidade (ou o logon) que você usou durante a ativação com a assinatura do Visual Studio. Dessa forma, você poderá ser reconhecido no [portal do assinante do Visual Studio](https://my.visualstudio.com?wt.mc_id=o~msft~docs), no VSTS e no Azure.

No VSTS, o status da sua assinatura do Visual Studio é verificado sempre que você faz logon e você recebe automaticamente os recursos de cada conta da qual é membro. Como esses recursos são incluídos como um benefício do assinante, você pode ser adicionado gratuitamente como membro de qualquer conta do VSTS ao usar uma identidade vinculada à sua assinatura do Visual Studio.

No Azure, o status da assinatura do Visual Studio é verificado quando você ativa o [crédito mensal do Azure](https://azure.microsoft.com/pricing/member-offers/credit-for-visual-studio-subscribers/), que é um benefício do assinante.

No [portal do assinante do Visual Studio](https://my.visualstudio.com?wt.mc_id=o~msft~docs), talvez você possa adicionar uma **alternativa identidade**, além da identidade usada durante a ativação. No momento, é permitido adicionar uma identidade alternativa quando uma conta da Microsoft é usada para ativar a assinatura. Dessa forma, também é possível adicionar uma conta corporativa ou de estudante (usada para fazer logon no Visual Studio, no Office 365 ou na rede corporativa ou de estudante), o que permite acessar o VSTS usando sua conta pessoal e sua conta corporativa ou de estudante.

## <a name="how-to-add-an-alternate-identity-to-your-visual-studio-subscription"></a>Como adicionar uma identidade alternativa à sua assinatura do Visual Studio

1. Entre no [portal do assinante do Visual Studio](https://my.visualstudio.com?wt.mc_id=o~msft~docs).

  > Se for solicitado que você escolha "conta pessoal" ou "conta corporativa ou de estudante", escolha "conta pessoal" (a sua conta da Microsoft).
  >
  > Às vezes, é preciso escolher porque sua conta da Microsoft e sua conta corporativa ou de estudante compartilham o mesmo endereço de email. Apesar de ambas as identidades usarem o mesmo endereço de email, elas ainda são identidades separadas, com perfis, configurações de segurança e permissões diferentes.
  >
  > A partir de 30 de março de 2018 não será mais possível criar uma conta da Microsoft usando um email que use um domínio gerenciado no Azure Active Directory. Você ainda poderá entrar usando esse email como uma conta corporativa.

2. Acesse a guia **Assinaturas**.

  ![Escolher assinaturas](_img/vs-alternate-identity/choose-subscriptions-my-visual-studio-com-portal.png)

3. Em **Links Relacionados**, acesse **Adicionar conta alternativa**.

  ![Em Links Relacionados, acesse Adicionar conta alternativa](_img/vs-alternate-identity/add-alternate-account-my-visual-studio-com-portal.png)

4. Insira sua conta corporativa ou de estudante e escolha **Adicionar**.

  ![Inserir sua conta corporativa ou de estudante](_img/vs-alternate-identity/enter-alternate-account-my-visual-studio-com-portal.png)

5. Use sua conta corporativa ou de estudante para entrar em sua conta do VSTS (```https://{youraccount}.visualstudio.com```). Pode haver um pequeno atraso para que as informações sejam propagadas, portanto, verifique novamente 15 minutos mais tarde. 

## <a name="faq"></a>Perguntas Frequentes

### <a name="q--why-doesnt-vsts-recognize-me-as-a-visual-studio-subscriber"></a>P: Por que o VSTS não me reconhece como um assinante do Visual Studio?
R: O VSTS deverá reconhecer sua assinatura automaticamente quando você entrar usando sua identidade principal ou alternativa. Caso contrário, você poderá tentar algumas coisas:

* Verifique se você tem uma assinatura ativa do Visual Studio que [inclua o VSTS como um benefício](vs-vsts.md).

* Confirme se você está usando um logon ou uma identidade que seja a identidade principal ou alternativa da sua assinatura do Visual Studio.

* Visite o [portal do assinante do Visual Studio](https://my.visualstudio.com?wt.mc_id=o~msft~docs) pelo menos uma vez antes de entrar no VSTS.

Se o VSTS ainda não reconhecer sua assinatura, [contate o suporte](https://www.visualstudio.com/team-services/support/)

