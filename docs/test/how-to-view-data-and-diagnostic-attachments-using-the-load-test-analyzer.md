---
title: Exibir anexos de dados e diagnóstico para testes de carga no Visual Studio | Microsoft Docs
ms.date: 10/19/2016
ms.topic: article
helpviewer_keywords:
- load tests, data and diagnostics attachments
ms.assetid: 73309bdd-437a-4eb0-88c8-702c3e24b9b0
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-ide-test
ms.openlocfilehash: 5d955412195a32a69e069ccac2b40456a9ffb986
ms.sourcegitcommit: 900ed1e299cd5bba56249cef8f5cf3981b10cb1c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/19/2018
---
# <a name="how-to-view-data-and-diagnostic-attachments-using-the-load-test-analyzer"></a>Como exibir anexos de dados e diagnóstico usando o Analisador de Teste de Carga

Antes de executar um teste de carga, você pode selecionar uma configuração de teste que especifica os adaptadores de dados e diagnóstico que deseja usar. Depois que o teste de carga é concluído, use o Analisador de Testes de Carga para exibir os detalhes desses adaptadores de dados e diagnóstico enquanto analisa os resultados. Para exibir os detalhes do adaptador de diagnóstico e dados, escolha o botão **Exibir Dados e Anexos de Diagnóstico** na barra de ferramentas do Analisador de Teste de Carga. Por exemplo, se o teste de carga teve o adaptador de informações do sistema definido na configuração de teste, você poderá exibir as informações do sistema do computador que foi usado quando o teste de carga foi executado.

![Caixa de diálogo Escolher anexo do adaptador de dados de diagnóstico](../test/media/load_adapterdialog.png "Load_AdapterDialog")

Outro exemplo é um teste de carga que inclui o adaptador IntelliTrace na configuração de teste. O adaptador IntelliTrace permite que você abra a página Resumo do IntelliTrace.

![Resumo do IntelliTrace](../test/media/load_intellitrace.png "Load_IntelliTrace")

Para obter mais informações, consulte [Coletar informações de diagnóstico usando configurações de teste](../test/collect-diagnostic-information-using-test-settings.md) e [Coletar dados do IntelliTrace](../test/how-to-collect-intellitrace-data-to-help-debug-difficult-issues.md).

## <a name="to-view-data-and-diagnostic-attachments-in-a-load-test-from-the-load-test-analyzer"></a>Para exibir dados e anexos de diagnóstico em um teste de carga no Analisador de Testes de Carga

1.  Depois que um teste de carga for concluído ou depois de abrir o resultado do teste de carga, na barra de ferramentas do Analisador de Teste de Carga, escolha **Exibir Dados e Anexos de Diagnóstico**.

     A caixa de diálogo **Escolha o Adaptador de Dados de Diagnóstico** é exibida.

2.  Selecione o anexo do adaptador de dados de diagnóstico que você deseja analisar e escolha **OK**.

## <a name="see-also"></a>Consulte também

- [Analisar resultados de teste de carga](../test/analyze-load-test-results-using-the-load-test-analyzer.md)