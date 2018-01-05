---
title: "Como: adicionar, atualizar ou remover uma referência de serviço de dados WCF | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- service references [Visual Studio]
- WCF Data Service reference
- WCF data service references
- ADO.NET service references
- ADO.NET Data Service reference
ms.assetid: 892ebf37-3af4-472e-8744-92837677d611
caps.latest.revision: "11"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.workload: data-storage
ms.openlocfilehash: c35fdaabf3de306af0541fb4781a085a3c409ff8
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-add-update-or-remove-a-wcf-data-service-reference"></a>Como adicionar, atualizar ou remover uma referência de WCF Data Services
Um *referência de serviço* permite que um projeto para acessar um ou mais [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)]. Use o **adicionar referência de serviço** caixa de diálogo para pesquisar [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] na solução atual, localmente, em uma rede local ou na Internet.  
  
[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
## <a name="adding-a-service-reference"></a>Adicionando uma referência de serviço  
  
#### <a name="to-add-a-reference-to-an-external-service"></a>Para adicionar uma referência para um serviço externo  
  
1.  Em **Solution Explorer**, clique no nome do projeto que você deseja adicionar o serviço e, em seguida, clique em **adicionar referência de serviço**.  
  
     O **adicionar referência de serviço** caixa de diálogo é exibida.  
  
2.  No **endereço** caixa, digite a URL para o serviço e, em seguida, clique em **vá** para procurar o serviço. Se o serviço implementar segurança de nome e a senha do usuário, você receberá um nome de usuário e senha.  
  
    > [!NOTE]
    >  Você deve referenciar apenas serviços de uma fonte confiável. Adicionando referências de uma fonte não confiável pode comprometer a segurança.  
  
     Você também pode selecionar a URL a partir de **endereço** lista, que armazena as URLs de 15 anteriores na qual os metadados de serviço válida foi encontrado.  
  
     Uma barra de progresso é exibida quando a pesquisa está sendo executada. Você pode parar a pesquisa a qualquer momento clicando em **parar**.  
  
3.  No **serviços** lista, expanda o nó para o serviço que você deseja usar e selecione um conjunto de entidades.  
  
4.  No **Namespace** , digite o namespace que você deseja usar para a referência.  
  
5.  Clique em **Okey** para adicionar a referência ao projeto.  
  
     Um cliente de serviço (proxy) é gerado e metadados que descreve o serviço é adicionado ao arquivo App. config.  
  
#### <a name="to-add-a-reference-to-a-service-in-the-current-solution"></a>Para adicionar uma referência a um serviço na solução atual  
  
1.  Em **Solution Explorer**, clique no nome do projeto que você deseja adicionar o serviço e, em seguida, clique em **adicionar referência de serviço**.  
  
     O **adicionar referência de serviço** caixa de diálogo é exibida.  
  
2.  Clique em **descobrir**.  
  
     Todos os serviços (ambos [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] e serviços WCF) na solução atual são adicionadas a **serviços** lista.  
  
3.  No **serviços** lista, expanda o nó para o serviço que você deseja usar e selecione um conjunto de entidades.  
  
4.  No **Namespace** , digite o namespace que você deseja usar para a referência.  
  
5.  Clique em **Okey** para adicionar a referência ao projeto.  
  
     Um cliente de serviço (proxy) é gerado e metadados que descreve o serviço é adicionado ao arquivo App. config.  
  
## <a name="updating-a-service-reference"></a>Atualizando uma referência de serviço  
 O modelo de dados de entidade para um [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] , às vezes, será alterado. Quando isso acontece, a referência de serviço deve ser atualizada.  
  
#### <a name="to-update-a-service-reference"></a>Para atualizar uma referência de serviço  
  
-   Em **Solution Explorer**, com o botão direito na referência de serviço e, em seguida, clique em **referência de serviço de atualização**.  
  
     Uma caixa de diálogo de progresso é exibida enquanto a referência é atualizada de seu local original e o cliente do serviço será gerada novamente para refletir as alterações nos metadados.  
  
## <a name="removing-a-service-reference"></a>Remover uma referência de serviço  
 Se uma referência de serviço não estiver sendo usada, você poderá ser removido de sua solução.  
  
#### <a name="to-remove-a-service-reference"></a>Para remover uma referência de serviço  
  
-   Em **Solution Explorer**, com o botão direito na referência de serviço e, em seguida, clique em **excluir**.  
  
     O cliente do serviço será removido da solução e os metadados que descrevem o serviço serão removido do arquivo App. config.  
  
    > [!NOTE]
    >  Qualquer código que faz referência a referência de serviço precisará ser removido manualmente.  
  
## <a name="see-also"></a>Consulte também  
 [Serviços do Windows Communication Foundation e WCF Data Services no Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)