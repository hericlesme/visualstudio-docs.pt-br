---
title: "Como reenviar emails de atribuição de assinatura do Manage.visualstudio.com ou VLSC | Microsoft Docs"
Author: evanwindom
Ms.author: jaunger
Manager: evelynp
Ms.date: 2/13/2018
Ms.topic: Get-Started-Article
Description: Learn how to resend the subscription assignment to subscribers from manage.visualstudio.com or VLSC
Ms.prod: vs-subscription
Ms.technology: vs-subscriptions
Searchscope: VS Subscription
ms.openlocfilehash: 0ba7d6e36c25ced78b0c6b25688e5eb5b26eb04a
ms.sourcegitcommit: a07b789cc41ed72664f2c700c1f114476e7b0ddd
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/19/2018
---
# <a name="how-to-resend-subscription-assignment-emails"></a>Como reenviar emails de atribuição de assinatura:

As etapas necessárias para reenviar um email de atribuição dependem de qual portal você está usando para gerenciar suas assinaturas. 

## <a name="resending-assignment-emails-from-within-managevisualstudiocom"></a>Reenviar emails de atribuição de dentro de manage.visualstudio.com

O processo para reenviar emails de atribuição de dentro do portal de manage.visualstudio.com é muito simples:

1. Visite o portal [manage.visualstudio.com](https://manage.visualstudio.com) e entre. 
2. Use a guia **Filtro** para pesquisar o assinante para o qual deseja reenviar o email de atribuição. (Para obter mais informações sobre filtragem, consulte [Pesquisar uma assinatura](/visualstudio/subscriptions/search-license).)
3. Clique nos assinantes.  Você pode usar Ctrl+clique ou Shift+clique para selecionar vários assinantes.
4. Clique em **Reenviar** na parte superior dos resultados da pesquisa.  

## <a name="resending-assignment-emails-from-within-vlsc"></a>Reenviar emails de atribuição de dentro do VLSC
Quando uma assinatura é atribuída a um assinante no VLSC e o assinante solicita que o email de atribuição seja reenviado, você pode fazer isso editando as informações de email do assinante e alterando-as de volta para o endereço original. Isso disparará automaticamente o reenvio do email de atribuição.

Siga as instruções abaixo para reenviar o email de atribuição:


1. Acesse o VLSC (Centro de Serviços de Licenciamento por Volume) e entre.
2. Nas páginas de Administração do VLSC, clique em **Assinaturas** e em **Assinaturas do Visual Studio**.
3. Clique no **Número do Contrato** associado à assinatura do Visual Studio.
4. Clique na seta para baixo na barra de **Pesquisa**.  
5. Procure o assinante usando o campo Endereço de Email.
6. Na lista de resultados, clique no **Sobrenome** do assinante.
7. Clique em **Editar**.
8. Faça uma edição na assinatura. A alteração específica que você faz não importa: basta haver uma alteração.  Por exemplo, remover um caractere do endereço de email do assinante: remova o "m" de .com. Clique no botão **Salvar**
9. Depois que as informações forem salvas, clique no botão **Editar** novamente e corrija o caractere ausente do email. Clique em **Salvar**.
   
Isso fará com que o VLSC reconheça que não houve alterações na assinatura e reenvie o email de atribuição ao email listado no portal. 

> [!NOTE]
> - As assinaturas atribuídas recentemente gerarão automaticamente o email de atribuição. As opções acima só são necessárias quando um usuário solicita uma nova notificação de email de atribuição ou a notificação não é enviada por qualquer motivo.
