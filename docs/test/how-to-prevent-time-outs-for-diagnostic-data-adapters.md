---
title: Tempos limite para adaptadores de dados de diagnóstico no Visual Studio | Microsoft Docs
ms.date: 10/19/2016
ms.topic: article
helpviewer_keywords:
- Diagnostic Data Adapter, increasing time-outs
ms.assetid: 39fff4fc-9233-4f67-96ac-e81bbaf7ca82
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-ide-test
ms.openlocfilehash: 50bdf23e83ca9ef70c40b010050a3e6aba90e0a5
ms.sourcegitcommit: 900ed1e299cd5bba56249cef8f5cf3981b10cb1c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/19/2018
---
# <a name="how-to-prevent-time-outs-for-diagnostic-data-adapters"></a>Como evitar tempos limites para adaptadores de dados de diagnóstico

Se estiver usando adaptadores de dados de diagnóstico nas configurações de teste, um tempo limite poderá ser atingido quando você iniciar sua execução de teste devido a um dos motivos a seguir:

-   O serviço do controlador de teste não está sendo executado no computador do controlador de teste. Talvez seja necessário reiniciar o serviço. Para obter mais informações sobre como determinar seu controlador de teste e gerenciar controladores de teste, consulte [Gerenciando controladores e agentes de teste com o Visual Studio](../test/manage-test-controllers-and-test-agents.md).

-   Se você coletar dados em um computador remoto, o firewall poderá bloquear o Microsoft Test Manager. O computador que executa o Microsoft Test Manager deve aceitar conexões de entrada do controlador de teste. Um tempo limite é atingido quando o Microsoft Test Manager não recebe uma mensagem do controlador porque está bloqueado pelo firewall. Você deve verificar as configurações do firewall no computador que executa o Microsoft Test Manager. Para obter mais informações sobre as configurações de firewall, consulte o seguinte [site da Microsoft](http://go.microsoft.com/fwlink/?LinkId=184980).

-   O controlador de teste não pode resolver o nome do computador que executa o Microsoft Test Manager. Isso poderá ocorrer se o DNS fornecer o endereço incorreto desse computador. Talvez seja preciso entrar em contato com o administrador da rede para resolver esse problema.

 Ao executar um teste longo que deve coletar muito dados, você pode descobrir que a coleção desses dados atingiu o tempo limite. Use o procedimento a seguir para resolver esse problema.

 Você pode aumentar o tempo limite atualizando o arquivo de configuração do Microsoft Test Manager ou o arquivo de configuração do agente de teste que está excedendo o tempo.

 Para o Microsoft Test Manager, o arquivo de configuração é chamado **mtm.exe.config**. Ele está localizado no seguinte diretório: *%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE*.

 Para atualizar um agente de teste, você deve atualizar os arquivos de configuração a seguir no computador do agente de teste. Todos esses arquivos estão localizados no computador do agente de teste no mesmo diretório: *%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE*.

-   QTAgent.exe.config

-   QTAgent32.exe.config

-   QTDCAgent.exe.config

-   QTDCAgent32.exe.config

 Se você executar testes manuais e coletar dados de um ambiente, quando um bug for criado ou um caso de teste for concluído, todos os dados coletados pelos adaptadores de dados de diagnóstico serão transferidos para o computador que está executando os testes manuais. Se você coletou muitos dados ou se tiver uma conexão de rede lenta, o processo poderá demorar mais do que o valor padrão de 60 segundos. Por exemplo, se você configurou o adaptador do IntelliTrace para coletar eventos do IntelliTrace e informações de chamada de vários processos, a transferência desses dados poderá exceder o tempo limite padrão. Para gerar esse valor, use o procedimento a seguir para atualizar o **mtm.exe.config**.

 Uma mensagem de erro será exibida se o tempo limite de atividade do Test Runner ou de um agente de teste for atingido. A mensagem de erro do agente de teste conterá as informações sobre qual computador do agente de teste atingiu o tempo limite. Use o procedimento a seguir para atualizar os arquivos de configuração, dependendo da mensagem de erro que você recebeu.

## <a name="to-increase-the-time-outs-for-your-diagnostic-data-adapters"></a>Para aumentar os tempos limite dos adaptadores de dados de diagnóstico

1.  Abra uma janela do Windows Explorer (ou Explorador de Arquivos).

     Para fazer isso, clique com o botão direito do mouse em **Iniciar** e aponte para **Explorar**.

    > [!NOTE]
    > Talvez sejam necessários privilégios administrativos para atualizar o arquivo.

2.  Localize o diretório *%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE* no seu computador que contenha o arquivo que você deve atualizar.

3.  Clique com o botão direito do mouse no arquivo e aponte para **Abrir com**. Selecione um editor.

     O arquivo é exibido no editor. Há muitas configurações armazenadas nesse arquivo. A maioria dessas configurações pode ser alterada usando o Microsoft Test Manager. No entanto, as configurações de tempo limite devem ser alteradas manualmente, conforme descrito nas etapas a seguir.

4.  Você deve alterar a seção de configurações de execução de teste para aumentar os valores de tempo limite. Essa seção tem o seguinte formato:

    ```
    <!-- Begin: Test execution settings -->

        <!-- How long test runner will wait for an event raised to all local data collectors to complete.  Default is 300. -->
        <add key="DataCollectorEventTimeoutInSeconds" value="300"/>

        <!-- How long test runner will wait for test run operations, such as starting or stopping a test run, to complete.  Default is 60. -->
        <add key="RunOperationTimeoutInSeconds" value="60"/>

        <!-- End: Test execution settings -->
    ```

5.  Para aumentar o tempo que os adaptadores de dados de diagnóstico devem aguardar até que os eventos sejam concluídos, aumente o valor da chave **DataCollectorEventTimeoutInSeconds**

6.  Se a mensagem de erro de tempo limite for para a atividade do Test Runner, você deverá aumentar o valor da chave **RunOperationTimeoutInSeconds**.

7.  Para aumentar o tempo limite de transferência de qualquer dado coletado de um bug ou quando um teste é finalizado para o computador que está executando os testes, você deverá adicionar o seguinte tempo limite a **mtm.exe.config** na seção appSettings do arquivo:

    ```
    <!-- How long test runner waits for data collected by diagnostic data adapters to be transferred to the computer. Default is 60 seconds. -->
    <add key="GetCollectorDataTimeout" value="300"/>
    ```

    > [!NOTE]
    > O valor de tempo limite é em segundos.

8.  Salve as alterações feitas no arquivo e execute novamente os testes que atingiram o tempo limite anteriormente.

## <a name="see-also"></a>Consulte também

- [Coletar informações de diagnóstico usando configurações de teste](../test/collect-diagnostic-information-using-test-settings.md)