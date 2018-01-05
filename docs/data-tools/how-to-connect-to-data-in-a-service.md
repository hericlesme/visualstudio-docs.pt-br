---
title: "Como: conectar a dados em um serviço | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data [Visual Studio], connecting to Web services
- data sources, creating from Web services
- data [Visual Studio], reading from Web services
- reading data, from Web services
- Web services, reading data
- Web services, as data sources
- Web services, connecting
ms.assetid: a6b54353-05fe-4e5c-8631-90231fc95504
caps.latest.revision: "32"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.workload: data-storage
ms.openlocfilehash: 58d22a756edd625a9c664862d05de5fe405fd9f0
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-connect-to-data-in-a-service"></a>Como conectar a dados em um serviço
Conectar seu aplicativo para os dados retornados de um serviço executando o [Assistente de configuração de fonte de dados](../data-tools/media/data-source-configuration-wizard.png) e selecionando **Service** no **escolher um tipo de fonte de dados**página.  
  
 Após a conclusão do assistente, uma referência de serviço é adicionada ao seu projeto e fica imediatamente disponível no [janela fontes de dados](add-new-data-sources.md).  
  
> [!NOTE]
>  Os itens que aparecem no **fontes de dados** janela são dependentes das informações que o serviço retorna. Alguns serviços não podem fornecer informações suficientes para o **Assistente de configuração de fonte de dados** para criar objetos ligáveis. Por exemplo, se o serviço retorna um dataset não tipado, então nenhum item aparecerá no **janela fontes de dados** após concluir o assistente. Isso ocorre porque datasets sem tipo não fornecem esquema, então o assistente não tem informações suficientes para criar a fonte de dados.  
  
[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
### <a name="to-connect-your-application-to-a-service"></a>Para conectar seu aplicativo a um serviço  
  
1.  Sobre o **dados** menu, clique em **adicionar nova fonte de dados**.  
  
2.  Selecione **Service** no **escolher um tipo de fonte de dados** página e, em seguida, clique em **próximo**.  
  
3.  Insira o endereço do serviço que você deseja usar ou clique em **Discover** para localizar serviços na solução atual e, em seguida, clique em **vá**.  
  
4.  Opcionalmente, um novo **Namespace** podem ser digitados no lugar do valor padrão.  
  
    > [!NOTE]
    >  Clique em **avançado** para abrir o [configurar a caixa de diálogo de referência de serviço](../data-tools/configure-service-reference-dialog-box.md).  
  
5.  Clique em **Okey** para adicionar uma referência de serviço ao seu projeto.  
  
6.  Clique em **Finalizar**.  
  
     A fonte de dados é adicionada para o **fontes de dados** janela.  
  
## <a name="next-steps"></a>Próximas etapas  
  
#### <a name="to-add-functionality-to-your-application"></a>Para adicionar funcionalidade ao seu aplicativo  
  
-   Selecione um item no **fontes de dados** janela e arraste-o para um formulário para criar controles associados. Para obter mais informações, consulte [associar controles a dados no Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md).  
  
## <a name="see-also"></a>Consulte também  
 [Associar controles WPF a um WCF data Services](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md)   
 [Serviços do Windows Communication Foundation e WCF Data Services no Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)