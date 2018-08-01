---
title: Atribuir licenças a assinaturas do Visual Studio | Microsoft Docs
author: TerryGLee
ms.author: tglee
manager: douge
ms.date: 07/16/2018
ms.topic: conceptual
description: Saiba como os administradores podem atribuir licenças aos assinantes
ms.prod: vs-subscription
ms.technology: vs-subscriptions
searchscope: VS Subscription
ms.openlocfilehash: 473933ca94090596f11a6e8abb499621b4430b3f
ms.sourcegitcommit: 5b767247b3d819a99deb0dbce729a0562b9654ba
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/20/2018
ms.locfileid: "39178394"
---
# <a name="assign-licenses-in-the-visual-studio-subscriptions-administrator-portal"></a>Atribuir licenças no portal do administrador de assinaturas do Visual Studio

Como administrador de assinaturas do Visual Studio, você pode usar o portal do administrador para atribuir assinaturas a usuários individuais e grupos de usuários.

Para grupos de usuários, você pode atribuir assinaturas a eles uma de cada vez ou usar o recurso **Adição em Massa** para carregar listas de assinantes com suas informações de assinatura de forma rápida e fácil. 

## <a name="individual-assignments"></a>Atribuições individuais

Veja a seguir como atribuir uma licença de assinatura do Visual Studio a um novo usuário para que ele possa acessar os benefícios da assinatura.

1. Entre no [portal do administrador](https://manage.visualstudio.com).

2. Para atribuir uma licença a único assinante do Visual Studio, na parte superior da tabela, selecione **Adicionar**.

   ![Adicionar um único assinante](media\add-single-subscriber.png)

3. Insira as informações do novo assinante nos campos do formulário. Se sua organização estiver usando o Azure Active Directory, este campo terá uma função de pesquisa para localizar pessoas no diretório atual, permitindo selecionar o usuário correto nos resultados da pesquisa. Quando você selecionar essa pessoa, o nome, o email de conexão e o email de notificação serão populados automaticamente. 

   ![Adicionar um novo endereço de email de notificação](media\add-new-subscriber-notification-email.png)

   Caso deseje que esse assinante tenha acesso a downloads de software quando ele entrar no [Portal de Assinaturas do Visual Studio](https://my.visualstudio.com?wt.mc_id=o~msft~docs), deixe a alternância de downloads habilitada na seção **Configurações de Download**. Se optar por desabilitar downloads, o usuário não terá acesso aos downloads de software, mas ainda terá acesso a todos os outros benefícios incluídos na assinatura.

   ![Acesso a downloads](media\access-to-downloads.png)

   Caso deseje alterar o idioma no qual o assinante recebe informações, faça isso na seção **Opções de Comunicação**.

   ![Alterar o idioma a ser usado para o envio de emails de notificação](media\change-subscriber-communication-preference.png)

   Caso deseje adicionar suas próprias anotações de referência para a assinatura, faça isso na seção **Adicionar referência**.

   ![Adicionar suas próprias anotações de referência a cada assinatura](media\add-subscriber-reference-notes.png) 

    Quando terminar de selecionar as opções e inserir os dados do assinante, escolha **Adicionar** na parte inferior do submenu **Adicionar Assinante**.

   ![Escolher o botão Adicionar](media\add-button.png)

4. Depois que você adicionar o assinante, um Email de Atribuição será enviado automaticamente para o novo assinante com mais instruções. É possível enviar o Email de atribuição novamente a qualquer momento selecionando o assinante e clicando no botão **Reenviar** no menu superior.

   ![Reenviar o email de ativação para qualquer usuário ou para vários usuários sempre que você desejar](media\resend-subscriber-activation-emails.png) 

## <a name="bulk-assignments"></a>Atribuições em massa

1. Para adicionar vários assinantes de uma vez, navegue para a guia **Gerenciar Assinantes**. Na faixa de opções na parte superior, clique em **Adição em Massa**.

  ![Adicionar vários assinantes](media\add-multiple-subscribers.png)

1. A atribuição em massa usa um modelo do Microsoft Excel para carregar os assinantes. Na caixa de diálogo Carregar Vários Assinantes, clique em **Baixar** para baixar o modelo.

  ![Baixar o modelo do Excel para carregar vários assinantes](media\download-template-upload-subscribers.png)

  >![NOTE] Sempre baixe a última versão desse modelo. Se você usar uma versão mais antiga, o upload em massa poderá falhar.

1. Na planilha do Excel, preencha os campos com as informações dos indivíduos aos quais deseja atribuir assinaturas. (*Referência* é um campo opcional.) Salve o arquivo localmente depois que terminar.

  Para que não haja problemas com o upload, observe as seguintes melhores práticas:

    - Verifique se nenhum dos campos do formulário contém vírgulas.
    - Remova os espaços antes e depois de campos de formulário.
    - Verifique se os nomes do usuário não contêm espaços extras entre nomes ou sobrenomes de duas partes (por exemplo, se uma pessoa tiver um nome de duas partes, como "Maria Eduarda", ele deverá ser digitado como "MariaEduarda", porque o sistema não cortará o espaço extra).

1. Retorne ao portal de Administração de Assinaturas do Visual Studio. Na caixa de diálogo **Carregar Vários Assinantes**, clique em **Procurar**.

  ![Navegar para o modelo salvo para carregar vários assinantes](media\bulk-add-browse-saved-template.png)

1. Navegue para o arquivo do Excel que você salvou e, em seguida, clique em **OK**.

  ![Carregar o modelo do Excel para carregar vários assinantes](media\bulk-upload-subscribers.png)

  Uma caixa de diálogo de progresso do upload será exibida.

  Se o modelo contiver erros, o upload falhará e os erros serão mostrados para que você possa corrigir o modelo e tentar o upload em massa novamente.

  ![Mensagem de erro em caso de falha no upload de vários assinantes](media\bulk-add-template-failed.png)

  Quando o upload for bem-sucedido, você verá a lista de assinantes e uma mensagem de confirmação.

  ![Mensagem de confirmação em caso de êxito no upload de vários assinantes](media\bulk-add-template-success.png)
