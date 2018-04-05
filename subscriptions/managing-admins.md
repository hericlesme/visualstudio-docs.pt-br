---
title: Gerenciamento de Direitos de Administrador no Portal do Administrador de Assinaturas do Visual Studio
Author: evanwindom
Ms.author: jaunger
Manager: evelynp
Ms.date: 1/19/2018
Ms.topic: Get-Started-Article
Description: Learn how manage admins & super admins in the Visual Studio Subscriptions Administrator Portal.
Ms.prod: vs-subscription
Ms.technology: vs-subscriptions
Searchscope: VS Subscription
ms.openlocfilehash: 83bf27d5aaa99c2095ad8a1fafd7541df90f316b
ms.sourcegitcommit: b18844078a30d59014b48a9c247848dea188b0ee
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2018
---
# <a name="managing-administrator-rights-in-the-visual-studio-subscriptions-administrator-portal"></a>Gerenciamento de Direitos de Administrador no Portal do Administrador de Assinaturas do Visual Studio

## <a name="overview"></a>Visão geral 
No Portal do Administrador de Assinaturas do Visual Studio (https://manage.visualstudio.com), há duas funções de gerenciamento:

**Superadministradores:** ao configurar uma organização pela primeira vez, o Contato Principal ou para Notificações torna-se um superadministrador por padrão. O contato principal ou para notificações pode optar por atribuir superadministradores ou administradores adicionais. Além de gerenciar assinaturas para assinantes individuais, os superadministradores podem adicionar e remover outros administradores e superadministradores. Se houver mais de dois superadministradores no sistema, um superadministrador poderá excluir todos, exceto os dois últimos por segurança. 

**Administradores:** um administrador pode gerenciar os assinantes nos contratos que o superadministrador atribui a ele.  Eles podem atribuir assinaturas a indivíduos, editar assinaturas e reatribuí-las ou removê-las.   (Administradores são indicados por Superadministradores).  

## <a name="adding-an-administrator-with-super-admin-rights"></a>Adicionar um administrador **com** direitos de Superadministrador:

1. Entre no [Portal do Administrador](https://manage.visualstudio.com) de Assinaturas do Visual Studio usando uma conta que tenha direitos de superadministrador.

2. Clique na guia **Gerenciar Administradores** na parte superior da página. (Somente Superadministradores têm acesso a essa guia.  Os administradores sem direitos de superadministrador usam a guia **Gerenciar Assinantes** para gerenciar assinantes individuais).

3. Clique em **Adicionar** para criar um novo administrador. 

4. Preencha todos os detalhes solicitados na janela pop-up Adicionar Administrador.
  - Se a organização já tiver sido registrada no AAD (Azure Active Directory), comece digitando o nome no campo **Nome** e selecione o item correto na lista suspensa. Com novos usuários, digite o nome completo e ignore a notificação *Nenhuma identidade encontrada*.
  - Depois que o usuário correto for identificado, o campo de entrada Endereço de Email será populado automaticamente. Digite o endereço de email do novo administrador, caso ainda não tenha sido fornecido.

5. Selecione o **PCN** que você deseja que o novo administrador gerencie, clicando na lista suspensa em **Contratos**. Se o PCN que você está integrando tiver mais de um contrato, você poderá fornecer ao administrador acesso a alguns dos contratos ou todos eles. 

**Mais informações sobre contratos:** a funcionalidade de lista suspensa em Contratos está desabilitada quando há somente um contrato.  Todos os Contratos são verificados automaticamente quando o usuário que você está configurando recebe direitos de Superadministrador.

6. Clique na caixa **Superadministrador** para habilitar direitos de superadministrador para esse administrador.  

7. Para terminar de adicionar esse administrador, clique em **Adicionar**.

**Possível erro recebido ao adicionar administradores:** alguns usuários podem receber uma mensagem de erro ao tentar adicionar o administrador. Isso costuma ocorrer se o endereço de email do superadministrador que está sendo adicionado não é listado no AAD da empresa. Para terminar de adicionar o novo administrador, basta ignorar o erro e clicar em **Adicionar** novamente. 

8. Quando um superadministrador tiver sido criado, você poderá vê-lo na lista de administradores, e a conta será marcada com uma marca de seleção verde para indicar o status de superadministrador. 

### <a name="optional--add-a-different-notification-email"></a>Opcional: adicione um email de notificação diferente.
Se a organização tiver um endereço/conta diferente para receber emails, agora você terá uma opção para inserir um endereço de "Comunicação". Selecione **Adicionar um email de notificação diferente para receber comunicação**. 

*Exemplo:* Diogo usa o rene@contoso.com quando entra usando as credenciais da empresa.  No entanto, a empresa de Diogo usa apenas esse endereço para gerenciar o acesso ao diretório.  Ao enviar e receber emails, Diogo usa o rene.collado@contoso.com. Portanto, o Superadministrador inseriu em um segundo endereço para garantir que ele receba os emails de boas-vindas.  Se a empresa não estiver configurada dessa forma, inserir o Endereço de Email de Entrada deverá ser suficiente.

## <a name="adding-an-administrator-without-super-admin-rights"></a>Adicionar um administrador **sem** direitos de Superadministrador:

O mesmo processo descrito acima deve ser seguido para adicionar administradores sem direitos de Superadministrador, mas levando em consideração os seguintes aspectos:
-  Ao adicionar Administradores sem direitos de Superadministrador, não é necessário que um endereço de email adicional seja incluído, e a caixa de seleção Superadministrador permanece em branco.
-  Os usuários sem direitos de Superadministrador não recebem o ícone de Verificação Verde na entrada de configuração de perfil em "Gerenciar Administradores".
