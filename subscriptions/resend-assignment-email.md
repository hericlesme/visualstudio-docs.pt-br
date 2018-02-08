---
title: "Como reenviar emails de atribuição de assinatura no VLSC | Microsoft Docs"
Author: evanwindom
Ms.author: jaunger
Manager: evelynp
Ms.date: 12/29/2017
Ms.topic: Get-Started-Article
Description: Learn how to resend the subscription assignment to a subscriber from within VLSC
Ms.prod: vs-subscription
Ms.technology: vs-subscriptions
Searchscope: VS Subscription
ms.openlocfilehash: 7162435044a578a94249774305f2c6b8b6438219
ms.sourcegitcommit: b18844078a30d59014b48a9c247848dea188b0ee
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2018
---
# <a name="how-to-resend-subscription-assignment-emails-from-vlsc"></a>Como reenviar emails de atribuição de assinatura no VLSC:

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
> - Este procedimento não é necessário para reenviar emails de atribuição a assinaturas atribuídas por meio de https://manage.visualstudio.com.  Para reenviar emails de atribuição a assinantes no portal, basta selecionar os assinantes e clicar no botão **Reenviar** na parte superior da lista de assinantes.  