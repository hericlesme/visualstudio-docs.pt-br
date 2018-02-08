---
Title: Assign licenses to Visual Studio Subscriptions | Microsoft Docs
Author: evanwindom
Ms.author: jaunger
Manager: evelynp
Ms.date: 10/3/2017
Ms.topic: Get-Started-Article
Description: Learn how administrators can assign licenses to subscribers
Ms.prod: vs-subscription
Ms.technology: vs-subscriptions
Searchscope: VS Subscription
ms.openlocfilehash: b82f02b968398d0a8d1ce4872ce00e8447a2ae4d
ms.sourcegitcommit: b18844078a30d59014b48a9c247848dea188b0ee
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2018
---
# <a name="assigning-licenses-in-the-visual-studio-subscriptions-administrator-portal"></a>Atribuir licenças no portal do administrador de assinaturas do Visual Studio

## <a name="assigning-a-single-user"></a>Atribuir um único usuário
Se você tiver licenças disponíveis para assinaturas do Visual Studio, será possível atribuir essas licenças a novos usuários para eles acessarem os benefícios da assinatura. 
1.  Para atribuir um único assinante do Visual Studio, na parte superior da tabela, clique em **Adicionar**.

    ![Adicionar assinante](_img\assign-license-add\assign-license-add.png)

2.  Insira as informações do novo assinante nos campos do formulário. Se sua organização estiver usando o Azure Active Directory, este campo terá uma função de pesquisa para localizar pessoas no diretório atual, permitindo selecionar o usuário correto nos resultados da pesquisa. Quando você selecionar a pessoa, o nome, o email de conexão e o email de notificação serão populados automaticamente, como é mostrado abaixo. 

Se sua organização tiver um email diferente para receber emails do que o usado para entrar, haverá a opção de inseri-lo aqui. Selecione o hiperlink que indica "Email de comunicação diferente do email de conexão?". 

Se desejar que este assinante tenha acesso a downloads de software quando entrar no [Portal de assinaturas do Visual Studio](https:/my.visualstudio.com?wt.mc_id=o~msft~docs), deixe a caixa de seleção Downloads marcada. Se optar por desmarcar esta caixa, o usuário não terá acesso aos downloads de software, mas ainda terá acesso a todos os outros benefícios incluídos na assinatura. Quando terminar, clique em **Adicionar**.

   ![Inserir informações do assinante](_img\assign-license-add\add-subscriber-1.png)

   ![Inserir informações do assinante](_img\assign-license-add\add-subscriber-2.png)

3.  Depois de adicionar o assinante, um email de atribuição será enviado automaticamente para o novo assinante com outras instruções. É possível enviar o Email de atribuição novamente a qualquer momento selecionando o assinante e clicando no botão **Reenviar** no menu superior.

    ![Assinante adicionado](_img\assign-license-add\add-subscriber-complete.png)

## <a name="bulk-assignments"></a>Atribuições em massa
1.  Para adicionar vários assinantes de uma vez, navegue até a guia Assinantes. Na faixa de opções na parte superior, clique em **Adição em Massa**. 

    ![Adição em Massa](_img\assign-license-add\bulk-assign-add.png)

2. A atribuição em massa usa um modelo do Microsoft Excel para carregar os assinantes. Na caixa de diálogo Carregar Vários Assinantes, clique em **Baixar** para baixar o modelo. Sempre baixe a versão mais recente deste modelo. Se você usar uma versão mais antiga, o upload em massa poderá falhar.

    ![Carregar vários assinantes](_img\assign-license-add\bulk-assign-upload.png)

3.  Na planilha do Excel, preencha os campos com as informações dos indivíduos para os quais deseja atribuir assinaturas. Referência é um campo opcional. Se você preencher alguma parte do modelo incorretamente, será exibida uma mensagem de erro descrevendo o problema. Salve o arquivo no disco rígido quando terminar.
**Para que não haja problemas com o upload, observe as seguintes práticas recomendadas:**
    - Verifique se nenhum dos campos do formulário contém vírgulas.
    - Remova os espaços antes e depois dos campos do formulário, como nomes de usuários.
    - Verifique se os nomes dos usuários não contêm espaços extras entre os nomes ou sobrenomes de duas partes (por exemplo, nomes de duas partes como "Maggie May" não devem ser digitados como "Maggie  May", pois o sistema não removerá o espaço extra)

   ![Modelo de adição em massa](_img\assign-license-add\bulk-template.png)

4.  Retorne ao Portal de Administração de Assinaturas do Visual Studio e na caixa de diálogo Carregar Vários Assinantes, clique em **Procurar**. Navegue até o arquivo do Excel que você salvou e clique em **OK**. O andamento do upload será exibido na tela. 

    ![Upload de adição em massa](_img\assign-license-add\bulk-assign-upload-2.png)

Se o modelo contiver erros, o upload falhará e os erros serão mostrados para que você possa corrigir o modelo e tentar o upload em massa novamente.

   ![Falha do upload](_img\assign-license-add\bulk-assign-upload-fail.png)

Quando o upload for bem-sucedido, você verá a lista de assinantes e uma mensagem de confirmação.

   ![Upload concluído](_img\assign-license-add\bulk-assign-upload-complete.png)