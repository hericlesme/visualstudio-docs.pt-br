---
title: Solucionando problemas de referências de serviço
ms.date: 11/04/2016
ms.topic: troubleshooting
f1_keywords:
- msvse_wcf.Err.ReferenceGroup_NamespaceConflictsOther
- msvse_wcf.Err.AddSvcRefDlg_NothingSelectedOnGo
- msvse_wcf.Err.ErrorOnOK
- msvse_wcf.cfg.ConfigurationErrorsException
helpviewer_keywords:
- service references [Visual Studio], troubleshooting
- WCF services, troubleshooting
ms.assetid: 3b531120-1325-4734-90c6-6e6113bd12ac
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: c244489f21dec3783aed9d970b46805d204a1104
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="troubleshoot-service-references"></a>Solucionar problemas de referências de serviço

Este tópico lista os problemas comuns que podem ocorrer quando você estiver trabalhando com o Windows Communication Foundation (WCF) ou do WCF Data Services no Visual Studio.

## <a name="error-returning-data-from-a-service"></a>Erro retornando dados de um serviço

Ao retornar um `DataSet` ou `DataTable` de um serviço, você receberá uma exceção "a cota de tamanho máximo para mensagens recebidas foi excedida". Por padrão, o `MaxReceivedMessageSize` para algumas associações é definida como um valor relativamente pequeno para limitar a exposição a ataques de negação de serviço. Você pode aumentar esse valor para evitar a exceção. Para obter mais informações, consulte <xref:System.ServiceModel.HttpBindingBase.MaxReceivedMessageSize%2A>.

Para corrigir esse erro:

1.  Em **Solution Explorer**, duas vezes no arquivo App. config para abri-lo.

2.  Localize o `MaxReceivedMessageSize` propriedade e alterá-lo para um valor maior.

## <a name="cannot-find-a-service-in-my-solution"></a>Não é possível localizar um serviço na minha solução

Quando você clica o **Discover** no botão de **adicionar referências de serviço** caixa de diálogo, um ou mais projetos de biblioteca de serviços WCF na solução não aparecem na lista de serviços. Isso pode ocorrer se uma biblioteca de serviços foi adicionada à solução, mas ainda não foi compilada.

Para corrigir esse erro:

-   Em **Solution Explorer**, com o botão direito do projeto de biblioteca de serviços WCF e clique em **criar**.

## <a name="error-accessing-a-service-over-a-remote-desktop"></a>Erro ao acessar um serviço em uma área de trabalho remota

Quando um usuário acessa um serviço WCF hospedado na Web sobre uma conexão de área de trabalho remota e o usuário não tem permissões administrativas, a autenticação NTLM é usada. Se o usuário não tem permissões administrativas, o usuário pode receber a seguinte mensagem de erro: "a solicitação HTTP está autorizada no esquema de autenticação de cliente 'Anonymous'. O cabeçalho de autenticação recebido do servidor foi 'NTLM'."

Para corrigir esse erro:

1.  No projeto de site da Web, abra o **propriedades** páginas.

2.  No **iniciar opções** guia, desmarque o **autenticação NTLM** caixa de seleção.

    > [!NOTE]
    > Você deve desativar a autenticação NTLM somente para sites que contêm exclusivamente serviços WCF. Segurança para serviços WCF é gerenciada por meio da configuração no arquivo Web. config. Isso torna a autenticação NTLM desnecessários.

## <a name="access-level-for-generated-classes-setting-has-no-effect"></a>Nível de acesso para Classes geradas configuração não tem nenhum efeito.

Definindo o **nível para as classes geradas de acesso** opção o **configurar referências de serviço** caixa de diálogo para **interno** ou **amigo** Talvez não funcionem sempre. Embora a opção parece estar definida na caixa de diálogo, as classes de suporte resultantes são geradas com um nível de acesso de `Public`.

Isso é uma limitação conhecida de determinados tipos, como aqueles serializado usando o <xref:System.Xml.Serialization.XmlSerializer>.

## <a name="error-debugging-service-code"></a>Código de serviço de depuração de erro

Quando você entra no código para um serviço WCF no código do cliente, você poderá receber um erro relacionado a ausência de símbolos. Isso pode ocorrer quando um serviço que fazia parte de sua solução foi movido ou removido da solução.

Quando você adicionar primeiro uma referência a um serviço WCF que faz parte da solução atual, uma dependência de compilação explícita é adicionada entre o projeto de serviço e o projeto de cliente de serviço. Isso garante que o cliente sempre acessa binários de serviço atualizado, que é especialmente importante para cenários como depuração no código do cliente em código de serviço de depuração.

Se o projeto de serviço é removido da solução, essa dependência de compilação explícita é invalidada. O Visual Studio não pode mais garantir que o projeto de serviço é recompilado conforme necessário.

Para corrigir esse erro, você deve recriar manualmente o projeto de serviço:

1.  No menu **Ferramentas**, clique em **Opções**.

2.  No **opções** caixa de diálogo caixa, expanda **projetos e soluções**e, em seguida, selecione **geral**.

3.  Verifique se o **configurações de compilação de Show advanced** caixa de seleção está selecionada e, em seguida, clique em **Okey**.

4.  Carregar o projeto de serviço do WCF.

5.  No **do Configuration Manager** caixa de diálogo, defina o **configuração de solução ativa** para **depurar**. Para obter mais informações, consulte [Como criar e editar configurações](../ide/how-to-create-and-edit-configurations.md).

6.  Em **Solution Explorer**, selecione o projeto de serviço do WCF.

7.  No **criar** menu, clique em **recriar** para recompilar o projeto de serviço do WCF.

## <a name="wcf-data-services-do-not-display-in-the-browser"></a>WCF Data Services não são exibidos no navegador

Quando ele tenta exibir uma representação XML dos dados em um [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)], Internet Explorer pode interpretar incorretamente os dados como um RSS feed. Certifique-se de que a opção para exibir os feeds RSS está desabilitada.

Para corrigir esse erro, desabilite feeds RSS:

1.  No Internet Explorer, no **ferramentas** menu, clique em **opções da Internet**.

2.  No **conteúdo** guia o **Feeds** seção, clique em **configurações**.

3.  No **configurações Feed** caixa de diálogo, desmarque o **ativar o modo de exibição de leitura de feed** caixa de seleção e, em seguida, clique em **Okey**.

4.  Clique em **Okey** para fechar o **opções da Internet** caixa de diálogo.

## <a name="see-also"></a>Consulte também

- [Serviços do Windows Communication Foundation e WCF Data Services no Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)