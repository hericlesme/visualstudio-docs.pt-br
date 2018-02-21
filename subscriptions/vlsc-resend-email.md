---
title: "Assinaturas do Visual Studio - Reenviar emails de atribuição do VLSC"
Author: evanwindom
Ms.author: jaunger
Manager: evelynp
Ms.date: 1/23/2018
Ms.topic: Get-Started-Article
Description: Learn how to resend subscription assignment emails from within VLSC
Ms.prod: vs-subscription
Ms.technology: vs-subscriptions
Searchscope: VS Subscription
ms.openlocfilehash: 338ae08ee1f3e6a819a1faea7bd095c9acd8ecd2
ms.sourcegitcommit: e5bd950df79175a96fe62b3d4b17a3ef536ec4c3
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/16/2018
---
# <a name="how-to-resend-subscription-assignment-emails-from-within-volume-license-service-center-vlsc"></a>Como reenviar emails de atribuição de assinatura de dentro do VLSC (Centro de Serviços de Licença por Volume)

Ocasionalmente, um assinante para o qual uma assinatura foi atribuída solicitará a um administrador o reenvio do email de notificação de atribuição de assinatura.  No novo portal de gerenciamento de assinatura, https://manage.visualstudio.com, isso é um processo simples.  No entanto, se a sua organização ainda estiver usando o VLSC (Centro de Serviço de Licença por Volume), não haverá nenhum recurso para reenviar automaticamente o email de notificação.  

Para reenviar o email de notificação de atribuição do VLSC, um administrador precisa usar a seguinte solução alternativa:

## <a name="resending-the-assignment-email"></a>Reenviando o email de atribuição:

Para que o VLSC gere uma nova notificação, é necessário editar as informações de email do assinante uma vez e, depois, retornar para o email original na mesma transação. Isso fará com que o VLSC reaja como se uma nova assinatura tivesse sido recebida e enviará o Email de Atribuição novamente.

1.  Acesse o [VLSC (Centro de Serviços de Licenciamento por Volume)](https://www.microsoft.com/Licensing/servicecenter/default.aspx) e entre.
2.  Clique na guia **Assinaturas** e escolha **Assinaturas do Visual Studio**.
3.  Clique no **Número do Contrato** associado à assinatura do Visual Studio.
4.  Clique na seta para baixo na barra de Pesquisa. 
5.  Procure o assinante usando o campo **Endereço de Email**.
6.  Localize o assinante nos resultados da pesquisa e clique no sobrenome. 
7.  Clique em **Editar**.
8.  Faça uma edição na assinatura. Por exemplo, remover um caractere do endereço de email do assinante. Clique no botão **Salvar**.
9.  Após a gravação das informações, clique em **Editar** novamente, reverta as alterações que você acabou de fazer e clique em **Salvar**.  

Isso fará com que a assinatura seja tratada como uma nova atribuição, e reenviará o email de notificação de atribuição para o assinante.  