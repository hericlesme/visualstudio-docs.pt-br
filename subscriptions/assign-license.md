---
title: Atribuir licenças a assinaturas do Visual Studio | Microsoft Docs
author: evanwindom
ms.author: jaunger
manager: evelynp
ms.date: 10/03/2017
ms.topic: Get-Started-Article
description: Saiba como os administradores podem atribuir licenças aos assinantes
ms.prod: vs-subscription
ms.technology: vs-subscriptions
searchscope: VS Subscription
ms.openlocfilehash: 4325921bbaa75e0fb8a8a16947c45901b6f01649
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34477373"
---
# <a name="assigning-licenses-in-the-visual-studio-subscriptions-administrator-portal"></a>Atribuindo licenças no portal do administrador de assinaturas do Visual Studio

Como administrador de assinaturas do Visual Studio, você pode usar o portal do administrador de assinaturas do Visual Studio para atribuir assinaturas a usuários individuais.  
Você pode atribuí-las uma de cada vez ou usar o recurso "adição em massa" para carregar listas de assinantes com suas informações de assinatura de forma rápida e fácil. 

## <a name="assigning-a-single-user"></a>Atribuir um único usuário
Se você tiver licenças disponíveis para assinaturas do Visual Studio, será possível atribuir essas licenças a novos usuários para eles acessarem os benefícios da assinatura. 
1.  Entrar no [portal do administrador](https://manage.visualstudio.com)

2.  Para atribuir um único assinante do Visual Studio, na parte superior da tabela, clique em **Adicionar**.

    <img alt="Add subscriber" src="_img\assign-license-add\assign-license-add.png" style="border: 1px solid #CCCCCC" />

3.  Insira as informações do novo assinante nos campos do formulário. Se sua organização estiver usando o Azure Active Directory, este campo terá uma função de pesquisa para localizar pessoas no diretório atual, permitindo selecionar o usuário correto nos resultados da pesquisa. Quando você selecionar a pessoa, o nome, o email de conexão e o email de notificação serão populados automaticamente, como é mostrado abaixo. 

    Se sua organização não estiver usando o Azure AD (Active Directory), mas tiver um email diferente para receber emails do que o usado para entrar, você terá a opção de inseri-lo aqui. Selecione o hiperlink rotulado "Adicionar um email diferente para receber comunicação". 

    **Acesso a downloads:**  
    Se desejar que este assinante tenha acesso a downloads de software quando entrar no [Portal de assinaturas do Visual Studio](https://my.visualstudio.com?wt.mc_id=o~msft~docs), deixe a alternância de downloads habilitada. Se optar por desabilitar downloads, o usuário não terá acesso aos downloads de software, mas ainda terá acesso a todos os outros benefícios incluídos na assinatura. 
    
    Quando terminar de escolher as opções para o assinante, clique em **Adicionar**.

    <img alt="Enter subscriber information" src="_img\assign-license-add\add-subscriber-1.png" style="border: 1px solid #CCCCCC" />
    <img alt="Enter subscriber information" src="_img\assign-license-add\add-subscriber-2.png" style="border: 1px solid #CCCCCC" />

4.  Depois de adicionar o assinante, um email de atribuição será enviado automaticamente para o novo assinante com outras instruções. É possível enviar o Email de atribuição novamente a qualquer momento selecionando o assinante e clicando no botão **Reenviar** no menu superior.

    <img alt="Subscriber added" src="_img\assign-license-add\add-subscriber-complete.png" style="border: 1px solid #CCCCCC" />

## <a name="bulk-assignments"></a>Atribuições em massa
1.  Para adicionar vários assinantes de uma vez, navegue até a guia **Gerenciar assinantes**. Na faixa de opções na parte superior, clique em **Adição em Massa**. 

    <img alt="Bulk add" src="_img\assign-license-add\bulk-assign-add.png" style="border: 1px solid #CCCCCC" />

2. A atribuição em massa usa um modelo do Microsoft Excel para carregar os assinantes. Na caixa de diálogo Carregar Vários Assinantes, clique em **Baixar** para baixar o modelo. Sempre baixe a versão mais recente deste modelo. Se você usar uma versão mais antiga, o upload em massa poderá falhar.

    <img alt="Upload multiple subscribers" src="_img\assign-license-add\bulk-assign-upload.png" style="border: 1px solid #CCCCCC" />

3.  Na planilha do Excel, preencha os campos com as informações dos indivíduos para os quais deseja atribuir assinaturas. Referência é um campo opcional. Se você preencher alguma parte do modelo incorretamente, será exibida uma mensagem de erro descrevendo o problema. Salve o arquivo localmente depois de concluído.
**Para que não haja problemas com o upload, observe as seguintes práticas recomendadas:**
    - Verifique se nenhum dos campos do formulário contém vírgulas.
    - Remova os espaços antes e depois dos campos do formulário, como nomes de usuários.
    - Verifique se os nomes dos usuários não contêm espaços extras entre os nomes ou sobrenomes de duas partes (por exemplo, um nome de duas partes como "Maggie May" não deve ser digitados como "Maggie  May", pois o sistema não removerá o espaço extra.)
    <img alt="Bulk add template" src="_img\assign-license-add\bulk-template.png" style="border: 1px solid #CCCCCC" />

4.  Retorne ao Portal de Administração de Assinaturas do Visual Studio e na caixa de diálogo Carregar Vários Assinantes, clique em **Procurar**. Navegue até o arquivo do Excel que você salvou e clique em **OK**. O andamento do upload será exibido na tela. 

    <img alt="Bulk add upload" src="_img\assign-license-add\bulk-assign-upload-2.png" style="border: 1px solid #CCCCCC" />

Se o modelo contiver erros, o upload falhará e os erros serão mostrados para que você possa corrigir o modelo e tentar o upload em massa novamente.
    <img alt="Upload fail" src="_img\assign-license-add\bulk-assign-upload-fail.png" style="border: 1px solid #CCCCCC" />

Quando o upload for bem-sucedido, você verá a lista de assinantes e uma mensagem de confirmação.

   <img alt="Upload complete" src="_img\assign-license-add\bulk-assign-upload-complete.png" style="border: 1px solid #CCCCCC" />