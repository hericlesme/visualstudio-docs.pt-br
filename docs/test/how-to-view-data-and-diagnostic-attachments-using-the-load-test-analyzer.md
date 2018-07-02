---
title: Exibir anexos de dados e de diagnóstico para testes de carga no Visual Studio
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, data and diagnostics attachments
ms.assetid: 73309bdd-437a-4eb0-88c8-702c3e24b9b0
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 525f4a1d11cd4026410baf696b4593daf2595e12
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34751359"
---
# <a name="how-to-view-data-and-diagnostic-attachments-using-the-load-test-analyzer"></a>Como exibir anexos de dados e diagnóstico usando o Analisador de Teste de Carga

Antes de executar um teste de carga, você pode selecionar uma configuração de teste que especifica os adaptadores de dados e diagnóstico que deseja usar. Depois que o teste de carga é concluído, use o Analisador de Testes de Carga para exibir os detalhes desses adaptadores de dados e diagnóstico enquanto analisa os resultados. Para exibir os detalhes do adaptador de diagnóstico e dados, escolha o botão **Exibir Dados e Anexos de Diagnóstico** na barra de ferramentas do Analisador de Teste de Carga. Por exemplo, se o teste de carga teve o adaptador de informações do sistema definido na configuração de teste, você poderá exibir as informações do sistema do computador que foi usado quando o teste de carga foi executado.

![Caixa de diálogo Escolhendo anexo do adaptador de dados de diagnóstico](../test/media/load_adapterdialog.png)

Outro exemplo é um teste de carga que inclui o adaptador IntelliTrace na configuração de teste. O adaptador IntelliTrace permite que você abra a página Resumo do IntelliTrace.

![Resumo do IntelliTrace](../test/media/load_intellitrace.png)

Para obter mais informações, consulte [Coletar informações de diagnóstico usando configurações de teste](../test/collect-diagnostic-information-using-test-settings.md) e [Coletar dados do IntelliTrace](../test/how-to-collect-intellitrace-data-to-help-debug-difficult-issues.md).

## <a name="to-view-data-and-diagnostic-attachments-in-a-load-test-from-the-load-test-analyzer"></a>Para exibir dados e anexos de diagnóstico em um teste de carga no Analisador de Testes de Carga

1.  Depois que um teste de carga for concluído ou depois de abrir o resultado do teste de carga, na barra de ferramentas do Analisador de Teste de Carga, escolha **Exibir Dados e Anexos de Diagnóstico**.

     A caixa de diálogo **Escolha o Adaptador de Dados de Diagnóstico** é exibida.

2.  Selecione o anexo do adaptador de dados de diagnóstico que você deseja analisar e escolha **OK**.

## <a name="see-also"></a>Consulte também

- [Analisar resultados de teste de carga](../test/analyze-load-test-results-using-the-load-test-analyzer.md)