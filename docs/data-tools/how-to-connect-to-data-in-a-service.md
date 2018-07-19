---
title: Como conectar a dados em um serviço
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- data [Visual Studio], connecting to Web services
- data sources, creating from Web services
- data [Visual Studio], reading from Web services
- reading data, from Web services
- Web services, reading data
- Web services, as data sources
- Web services, connecting
ms.assetid: a6b54353-05fe-4e5c-8631-90231fc95504
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: d6f90a99a387452500686af332edb1d112a88f82
ms.sourcegitcommit: e9d1018a01af62c3dc5aeb6b325faba7e20bd496
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/28/2018
ms.locfileid: "37089112"
---
# <a name="how-to-connect-to-data-in-a-service"></a>Como: conectar-se aos dados em um serviço

Você conecta seu aplicativo para os dados retornados de um serviço executando o [Data Source Configuration Wizard](../data-tools/media/data-source-configuration-wizard.png) e selecionando **serviço** sobre o **escolher um tipo de fonte de dados**página.

Após a conclusão do assistente, uma referência de serviço é adicionada ao seu projeto e fica imediatamente disponível na [janela fontes de dados](add-new-data-sources.md).

> [!NOTE]
> Os itens que aparecem na **fontes de dados** janela são dependentes das informações que o serviço retorna. Alguns serviços não podem fornecer informações suficientes para que o **Data Source Configuration Wizard** criar objetos associáveis. Por exemplo, se o serviço retorna um conjunto de dados não tipado, nenhum item aparecerá na **janela fontes de dados** após concluir o assistente. Isso ocorre porque os conjuntos de dados não tipados não fornecem esquema, portanto, o assistente não tem informações suficientes para criar a fonte de dados.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="to-connect-your-application-to-a-service"></a>Conectar seu aplicativo a um serviço

1.  Sobre o **dados** menu, clique em **Add New Data Source**.

2.  Selecione **serviço** sobre o **escolher um tipo de fonte de dados** página e, em seguida, clique em **próxima**.

3.  Insira o endereço do serviço que você deseja usar ou clique em **Discover** para localizar serviços na solução atual e, em seguida, clique em **vá**.

4.  Opcionalmente, você pode digitar um novo **Namespace** no lugar do valor padrão.

    > [!NOTE]
    > Clique em **Advanced** para abrir o [caixa de diálogo Configurar referência de serviço](../data-tools/configure-service-reference-dialog-box.md).

5.  Clique em **Okey** para adicionar uma referência de serviço ao seu projeto.

6.  Clique em **Finalizar**.

     A fonte de dados é adicionada para o **fontes de dados** janela.

## <a name="next-steps"></a>Próximas etapas

Para adicionar funcionalidade ao seu aplicativo, selecione um item na **fontes de dados** janela e arraste-o para um formulário para criar controles associados. Para obter mais informações, consulte [associar controles a dados no Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md).

## <a name="see-also"></a>Consulte também

- [Associar controles WPF a um WCF Data Service](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md)
- [Serviços do Windows Communication Foundation e WCF data services no Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)