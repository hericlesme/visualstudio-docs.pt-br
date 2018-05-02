---
title: Coletar detalhes completos de usuários virtuais para testes de carga no Visual Studio
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, virtual user activity chart, configuring
- virtual user activity chart, configuring
ms.assetid: cb22e43b-af4d-4e09-9389-3c3fa00786f7
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: cac171d6f0e1bcd91a89be799497b84dc15fc5a5
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-configure-load-tests-to-collect-full-details-to-enable-virtual-user-activity-in-test-results"></a>Como configurar testes de carga para coletar detalhes completos para habilitar a atividade de usuário virtual em resultados de teste

Para usar o Gráfico de Atividade de Usuário Virtual para o teste de carga, configure o teste de carga para coletar detalhes completos. Para configurar o teste de carga para fazer isso, selecione a configuração **Todos os detalhes individuais** para a propriedade **Armazenamento de detalhes de medição de tempo** associada ao teste de carga. Nesse modo, o teste de carga coletará informações detalhadas sobre cada teste, página e transação.

 Se você estiver atualizando um projeto de uma versão anterior do teste de carga do Visual Studio, use as etapas no seguinte procedimento para habilitar a coleta de detalhes completos.

 A configuração **Todos os detalhes individuais** para a propriedade **Armazenamento de detalhes de medição de tempo** pode ser definida com qualquer uma das seguintes opções:

-   **Todos os detalhes de individuais:** coleta e armazena dados de tempo individuais para cada teste, transação e página emitidos durante o teste.

    > [!NOTE]
    > A opção **Todos os detalhes individuais** deve ser selecionada para habilitar informações de dados de usuário virtual em seus resultados de teste de carga.

-   **Nenhum:** não coleta detalhes de medição de tempo individuais. No entanto, os valores médios permanecem disponíveis.

-   **Apenas estatísticas:** armazena dados de tempo individuais, mas somente como dados em percentis. Isso economiza recursos de espaço.

## <a name="to-configure-the-timing-details-storage-property-in-a-load-test"></a>Para configurar a propriedade de armazenamento de detalhes de medição de tempo em um teste de carga

1.  Abra um teste de carga no Editor de testes de carga.

2.  Expanda o nó **Configurações de execução** no teste de carga.

3.  Escolha as configurações de execução que deseja definir, por exemplo **Configurações de Execução1[Ativas]**.

4.  Abra a janela Propriedades. No menu **Exibir**, selecione **Janela de Propriedades**.

5.  Na categoria **Resultados**, escolha a propriedade **Armazenamento de detalhes de medição de tempo** e selecione **Todos os detalhes individuais**.

     Após ter definido a configuração de **Todos os detalhes individuais** para a propriedade de **Armazenamento de detalhes de medição de tempo**, você poderá executar o teste de carga e exibir o Gráfico de Atividade de Usuário Virtual. Para obter mais informações, consulte [Como analisar o que usuários virtuais estão fazendo durante um teste de carga](../test/how-to-analyze-virtual-user-activity-during-a-load-test.md).

## <a name="see-also"></a>Consulte também

- [Analisando a atividade de usuário virtual na exibição Detalhes](../test/analyze-load-test-virtual-user-activity-in-the-details-view.md)
- [Passo a passo: usando o gráfico de atividade de usuário virtual para isolar problemas](../test/walkthrough-use-the-virtual-user-activity-chart-to-isolate-issues.md)