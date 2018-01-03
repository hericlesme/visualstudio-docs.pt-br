---
title: "Passo a passo da configuração do Azure para as Ferramentas do Visual Studio para Unity | Microsoft Docs"
ms.custom: 
ms.date: 10/19/2017
ms.reviewer: crdun
ms.suite: 
ms.technology: tgt-pltfrm-cross-plat
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: BAE62C27-CA7A-4466-8738-3DB880221CE1
author: dantogno
ms.author: v-davian
manager: crdun
ms.workload:
- azure
- unity
ms.openlocfilehash: 25424ea06c01224bb1b35f783be82a857b991adf
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="configure-easy-tables-in-azure"></a>Configurar Tabelas Fáceis no Azure

As Tabelas Fáceis são um recurso dos [Aplicativos Móveis do Azure](https://azure.microsoft.com/services/app-service/mobile/) que permitem a configuração e o gerenciamento de tabelas SQL diretamente na GUI (interface gráfica do usuário) do Portal do Azure. Os Aplicativos Móveis do Azure são compatíveis com muitos recursos, mas o escopo deste exemplo é limitado à leitura e gravação de dados armazenados em um back-end de Aplicativo Móvel do Azure por meio de um projeto do Unity.

## <a name="create-a-new-azure-mobile-app"></a>Criar um novo Aplicativo Móvel do Azure

Entre no [Portal do Azure](https://ms.portal.azure.com). Se você não tem uma assinatura do Azure, a [avaliação gratuita](https://azure.microsoft.com/en-us/free/) ou os créditos incluídos com o [Visual Studio Dev Essentials](https://www.visualstudio.com/dev-essentials/) serão mais do que suficientes para realizar este passo a passo.

**Uma vez no portal:**

1. Selecione **Novo > Web + Celular > Aplicativo Móvel > Criar**.

  ![Criar um novo Aplicativo Móvel](media/vstu_azure-configure-easy-tables-image1.png)

2. Configurar o novo Aplicativo Móvel:

  * **Nome do aplicativo**. Isso criará a URL usada para se conectar ao back-end do Aplicativo Móvel do Azure. Você deve escolher um nome exclusivo, indicado pela marca de seleção verde.

  * **Assinatura**. Escolha a assinatura que o novo Aplicativo Móvel usará para cobrança.

  * **Grupo de recursos**. Os grupos de recursos permitem o gerenciamento mais fácil de recursos relacionados. Por padrão, o Azure cria um novo grupo de recursos com o mesmo nome que o novo aplicativo. A configuração padrão funciona bem para o passo a passo.

  *  **Localização/Plano do Serviço de Aplicativo**. O plano de serviço determina a capacidade de computação, o local e o custo dos recursos que o Azure usa para hospedar seu novo Aplicativo Móvel. Por padrão o Azure criará um novo plano de serviço com algumas configurações padrão. Essa é a opção mais simples para este passo a passo. No entanto, você pode usar este menu para personalizar o tipo de preço ou a localização geográfica de um novo plano do serviço. Além disso, as configurações para um plano de serviço podem ser modificadas depois da implantação.

  ![Criar um novo Aplicativo Móvel](media/vstu_azure-configure-easy-tables-image2.png)

3. Selecione **Criar** e aguarde alguns minutos para o Azure implantar o novo recurso. Você verá uma notificação no Portal do Azure quando a implantação for concluída.

## <a name="add-a-new-data-connection"></a>Adicionar uma nova conexão de dados

4. Depois que a implantação for concluída, clique no botão **Todos os recursos** e, em seguida, selecione o Aplicativo Móvel recém-criado.

  ![Selecionar o novo Aplicativo Móvel](media/vstu_azure-configure-easy-tables-image3.png)

5. Na folha recém-aberta, role para baixo no menu do lado esquerdo e clique no botão **Tabelas Fáceis**, listado sob o cabeçalho **MOBILE**.

  ![Selecionar Tabelas Fáceis](media/vstu_azure-configure-easy-tables-image4.png)

6. Clique no aviso azul **Precisa configurar as Tabelas Fáceis/APIs Fáceis?**, exibido na parte superior da folha Tabelas Fáceis.

  ![Clicar no aviso configurar Tabelas Fáceis](media/vstu_azure-configure-easy-tables-image5.png)

7. Clique no aviso que diz **Você precisa de um banco de dados para usar Tabelas Fáceis. Clique aqui para criar um**.

  ![Clicar no aviso de criação de banco de dados](media/vstu_azure-configure-easy-tables-image6.png)

8. Na folha Conexões de Dados, clique no botão **Adicionar**.

  ![Clicar no botão Adicionar](media/vstu_azure-configure-easy-tables-image7.png)

9. Em Adicionar uma folha de conexão de dados, selecione **Banco de Dados SQL**.

  ![Selecionar Banco de Dados SQL](media/vstu_azure-configure-easy-tables-image8.png)

10. Será aberta uma folha para a configuração de um novo banco de dados SQL e SQL Server:

  * **Nome**. Insira um nome para o banco de dados.

  * **Servidor de destino**. Clique em **Servidor de destino** para abrir a folha Novo servidor.

      * **Nome do servidor**. Insira um nome para o servidor.

      * **Logon e senha do administrador do servidor**. Crie um nome de usuário e uma senha para o administrador do servidor.

      * **Local**. Escolha um local próximo para o servidor.

      * Certifique-se de que a caixa de seleção **Permitir que os serviços do Azure acessem o servidor** permaneça marcada.

      * Clique em **Selecionar** para concluir a configuração do servidor.

    * **Tipo de preço**. Deixe a configuração padrão para o passo a passo. Isso pode ser modificado posteriormente.

    * **Agrupamento**. Deixe a configuração padrão.

    * Clique em **Selecionar** para concluir a configuração do banco de dados.

    ![Configurar o banco de dados e o SQL Server](media/vstu_azure-configure-easy-tables-image9.png)

11. De volta na folha Adicionar conexão de dados, clique em **Cadeia de Conexão**. Quando a folha de Cadeia de conexão for exibida, deixe as configurações padrão e clique em **OK**.

  ![Clicar em Cadeia de Conexão](media/vstu_azure-configure-easy-tables-image9.1.png)

12. Na folha Adicionar conexão de dados, o texto "MS_TableConnectionString" já não deve estar mais em itálico. Clique em **OK** e aguarde alguns minutos para que o Azure crie a nova conexão de dados. Uma notificação será recebida quando o processo for concluído.

  ![Clicar em OK](media/vstu_azure-configure-easy-tables-image9.2.png)

## <a name="complete-the-easy-table-initialization"></a>Concluir a inicialização da Tabela Fácil

13. Depois que a nova conexão de dados for criada com êxito, clique no botão **Todos os recursos** e navegue novamente de volta até o Aplicativo Móvel. É importante realizar esta etapa para atualizar o aviso de configuração da Tabela Fácil.

14. Role para baixo e selecione **Tabelas Fáceis** e, mais uma vez, selecione o aviso azul **Precisa configurar as Tabelas Fáceis/APIs Fáceis?**.

  ![Clicar no aviso das Tabelas Fáceis](media/vstu_azure-configure-easy-tables-image5.png)

15. Agora a folha que aparece deve indicar que "Já tem uma conexão de dados" abaixo do cabeçalho **1**. No cabeçalho **2**, clique na caixa de seleção que diz **Confirmo que isto substituirá o conteúdo do site.** Agora clique em **Inicializar Aplicativo** e aguarde alguns minutos para que o Azure conclua o processo de inicialização. Uma notificação anunciará quando esse processo for concluído.

  ![Clicar em Iniciar Aplicativo](media/vstu_azure-configure-easy-tables-image10.png)

## <a name="next-step"></a>Próximas etapas

* [Criar Tabelas Fáceis](visual-studio-tools-for-unity-azure-setup.md)
