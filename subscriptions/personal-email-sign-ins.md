---
title: Emails pessoais exibidos no VLSC
author: evanwindom
ms.author: jaunger
manager: evelynp
ms.date: 01/23/2018
ms.topic: Get-Started-Article
description: 'As assinaturas do Visual Studio: por que estou vendo endereços do Hotmail ou do Gmail para os assinantes?'
ms.prod: vs-subscription
ms.technology: vs-subscriptions
searchscope: VS Subscription
ms.openlocfilehash: cfe035d82976e3df683f4e3a35bd9d7f3c8cf9e2
ms.sourcegitcommit: 3724338a5da5a6d75ba00452b0a607388b93ed0c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2018
---
# <a name="visual-studio-subscriptions--why-am-i-seeing-hotmail-or-gmail-addresses-for-my-subscribers"></a>Assinaturas do Visual Studio: por que estão aparecendo endereços do Hotmail ou do Gmail para os assinantes? 

À medida que as empresas migram do VLSC (Volume Licensing Service Center) para o novo [Portal de Administração de Assinaturas](https://manage.visualstudio.com) do Visual Studio, os administradores podem ficar surpresos ao descobrir que o "Endereço de Email de Entrada" para alguns assinantes mostra um endereço de email de terceiros, como Hotmail, Gmail ou Yahoo.

## <a name="cause"></a>Causa

Esse cenário ocorre devido aos processos de entrada que estavam associados à experiência herdada de Assinante do MSDN. Os usuários foram migrados do VLSC para o novo portal sem modificações. Alguns administradores talvez não soubessem que os usuários estavam usando contas pessoais para acessar os benefícios de assinatura. Antes das migrações de assinante do Visual Studio, que foram concluídas em 2016, havia duas ações necessárias para usar com êxito uma assinatura do Visual Studio:
1. O administrador "atribuiu" a assinatura a um assinante individual, usando o endereço de email corporativo ou de estudante.
2. O assinante "ativou" a assinatura.

Durante o processo de ativação do assinante: a conta da Microsoft (MSA) foi necessária para entrar. Se o assinante não tiver tentado tornar a conta corporativa ou de estudante (por exemplo, John@contoso.com) uma MSA, ele poderá criar uma nova MSA ou usar uma existente. Isso fez com que o "Endereço de Email de Entrada" fosse diferente do "Endereço de Email Atribuído".

> [!NOTE] 
> A nova experiência de assinante em [https://my.visualstudio.com](https://my.visualstudio.com?wt.mc_id=o~msft~docs) é compatível com os tipos de identidade corporativa/de estudante da conta da Microsoft (MSA).

Por fim, como a migração do administrador obtém dados do VLSC sobre o "endereço de email de entrada" do assinante para popular a nova experiência de gerenciamento de assinante, administradores migrados recentemente podem ver essas contas pessoais anteriormente despercebidas devido a alterações na interface do usuário que tornam essas informações mais visíveis.

## <a name="solution"></a>Solução

Para corrigir o problema, você precisará editar as informações do assinante para atualizar os endereços de email de entrada.  Podem ser feitas edições em assinantes individuais ou em massa. Para obter mais informações, acesse [Editar uma assinatura](/visualstudio/subscriptions/edit-license).  

Depois de atualizar os endereços de email de assinantes, convém notificá-lo de que as informações de logon foram alteradas.  