---
title: Criar um relatório de desempenho de teste de carga do Visual Studio usando o Microsoft Word | Microsoft Docs
ms.date: 10/19/2016
ms.topic: article
helpviewer_keywords:
- load tests, reporting
- load tests, creating Word reports
ms.assetid: 3b864c75-2699-48c1-a2b4-9651f108c267
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-ide-test
ms.openlocfilehash: 39a9770debd4c907d8d80a0f7b3559e42fb99a21
ms.sourcegitcommit: 900ed1e299cd5bba56249cef8f5cf3981b10cb1c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/19/2018
---
# <a name="how-to-manually-create-a-load-test-performance-report-using-microsoft-word"></a>Como criar manualmente um relatório de desempenho de teste de carga usando o Microsoft Word

Você pode criar manualmente relatórios de teste de carga do Microsoft Word copiando e colando dados da exibição de gráficos e da exibição resumida Resultados de Teste de Carga. Os dados que são apresentados na exibição resumida e na exibição de gráficos são aplicados no formato HTML quando são copiados.

> [!TIP]
> Você pode copiar texto sem formatação da exibição de tabelas e de capturas de tela da exibição de detalhes no Microsoft Word, mas o texto não é aplicado no formato HTML e exigirá formatação e edição adicionais.

> [!TIP]
> Também é possível gerar relatórios organizados do Microsoft Excel automaticamente. Para obter mais informações, consulte [Como criar relatórios de desempenho de teste de carga usando o Microsoft Excel](../test/how-to-create-load-test-performance-reports-using-microsoft-excel.md).

## <a name="copy-summary-view-data"></a>Copiar dados da exibição resumida

1.  Se a exibição resumida não estiver sendo mostrada nos Resultados de Teste de Carga, clique em **Resumo** na barra de ferramentas.

2.  Na exibição resumida, clique com o botão direito do mouse e selecione **Selecionar Tudo**.

3.  Na exibição resumida, clique com o botão direito do mouse e selecione **Copiar**. Isso renderiza os dados da exibição resumida como formato HTML na área de transferência.

4.  No Microsoft Word, cole os dados da exibição resumida no local desejado.

5.  Agora é possível modificar, formatar e excluir aspectos do conteúdo copiado para que ele atenda às suas necessidades de relatório.

## <a name="copy-graph-view-data"></a>Copiar dados de exibição de gráfico

1.  Se a exibição de gráficos não estiver sendo mostrada nos Resultados de Teste de Carga, clique em **Gráficos** na barra de ferramentas.

2.  (Opcional) Amplie o gráfico específico que você deseja copiar no documento do Microsoft Word, conforme mostrado na ilustração a seguir. Para obter mais informações, consulte [Como ampliar uma região do gráfico](../test/how-to-zoom-in-on-a-region-of-the-graph-in-load-test-results.md).

     ![Controle de zoom de exibição de gráfico](../test/media/ltest_zoomcontrol.png "LTest_ZoomControl")

3.  No gráfico que deseja copiar no documento do Microsoft Word, clique com o botão direito do mouse e selecione **Copiar**.

4.  No Microsoft Word, cole o gráfico e os dados da tabela associada no local desejado.

    > [!WARNING]
    > Não é possível copiar o gráfico de uma área de trabalho remota e colá-lo em outro computador, pois somente as informações da tabela associada ao gráfico serão copiadas, e não a imagem do gráfico. A imagem do gráfico é armazenada no diretório temporário do computador do qual ela foi copiada e o segundo computador não pode desreferenciar esse diretório.

## <a name="see-also"></a>Consulte também

- [Relatando resultados de teste de carga para comparações de testes ou análise de tendências](../test/compare-load-test-results.md)
- [Como criar relatórios de desempenho de teste de carga usando o Microsoft Excel](../test/how-to-create-load-test-performance-reports-using-microsoft-excel.md)