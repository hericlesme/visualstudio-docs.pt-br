---
title: Emails pessoais exibidos no VLSC
Author: evanwindom
Ms.author: jaunger
Manager: evelynp
Ms.date: 1/23/2018
Ms.topic: Get-Started-Article
Description: "Visual Studio Subscriptions – Why Am I Seeing Hotmail or Gmail Addresses for My Subscribers?"
Ms.prod: vs-subscription
Ms.technology: vs-subscriptions
Searchscope: VS Subscription
ms.openlocfilehash: 2bfe2f39d432be5fc6ff7b24be2a218d02fce961
ms.sourcegitcommit: b18844078a30d59014b48a9c247848dea188b0ee
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2018
---
# <a name="visual-studio-subscriptions--why-am-i-seeing-hotmail-or-gmail-addresses-for-my-subscribers"></a>As assinaturas do Visual Studio: por que estou vendo endereços do Hotmail ou do Gmail para os assinantes? 

À medida que as empresas migram do VLSC (Volume Licensing Service Center) para o novo [Portal de Administração de Assinaturas](https://manage.visualstudio.com) do Visual Studio, os administradores podem ficar surpresos ao descobrir que o "Endereço de Email de Entrada" para alguns assinantes mostra um endereço de email de terceiros, como Hotmail, Gmail ou Yahoo.

## <a name="cause"></a>Causa

Esse cenário ocorre devido aos processos de entrada que estavam associados à experiência de Assinante do MSDN herdada. Os usuários foram migrados do VLSC para o novo portal sem modificações. Alguns administradores talvez não soubessem que os usuários estavam usando contas pessoais para acessar os benefícios de assinatura. Antes das migrações de assinante do Visual Studio, que foram concluídas em 2016, havia duas ações necessárias para usar com êxito uma assinatura do Visual Studio:
1. O administrador "atribuiu" a assinatura a um assinante individual, usando o endereço de email corporativo ou de estudante.
2. O assinante "ativou" a assinatura.

Durante o processo de ativação de assinante:
1. Uma MSA (conta da Microsoft) era necessária para entrar.
2. Se o assinante não tiver tentado tornar a conta corporativa ou de estudante (por exemplo, John@contoso.com) uma MSA, ele poderá criar uma nova MSA ou usar uma existente.
3. Isso fez com que o "Endereço de Email de Entrada" fosse diferente do "Endereço de Email Atribuído".

> [!NOTE] 
> A nova experiência de assinante em [https://my.visualstudio.com](https://my.visualstudio.com?wt.mc_id=o~msft~docs) dá suporte a tipos de identidade Corporativa ou de Estudante e à MSA (conta da Microsoft).

Por fim, como a migração do administrador obtém dados do VLSC sobre o "endereço de email de entrada" do assinante para popular a nova experiência de gerenciamento de assinante, administradores migrados recentemente podem ver essas contas pessoais anteriormente despercebidas devido a alterações na interface do usuário que tornam essas informações mais visíveis.

## <a name="solution"></a>Solução

Para corrigir o problema, você precisará editar as informações do assinante para atualizar os endereços de email de entrada.  Podem ser feitas edições em assinantes individuais ou em massa. Para obter mais informações, acesse [Editar uma assinatura](/visualstudio/subscriptions/edit-license).  

Depois de atualizar os endereços de email de assinantes, convém notificá-lo de que as informações de logon foram alteradas.  