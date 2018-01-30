---
title: Exibir eventos com o IntelliTrace | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e1c9c91a-0009-4c4e-9b4f-c9ab3a6022a7
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: ebc3067ea154c8b9a5f6e180f397c5421f2be470
ms.sourcegitcommit: 9a2f937e42305db6e3eaa7aadc235b0ba9aafc83
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2018
---
# <a name="view-events-with-intellitrace-in-visual-studio"></a>Exibir eventos com o IntelliTrace no Visual Studio
Você pode usar o IntelliTrace para coletar informações sobre eventos específicos ou as categorias de eventos ou chamadas de função individuais além de eventos. Os procedimentos a seguir mostram como fazer isso.  
  
 Você pode usar o IntelliTrace na edição Enterprise do Visual Studio, mas não nas edições Professional ou da comunidade.  
  
##  <a name="GettingStarted"></a>Configurar o Intellitrace  
 Você pode tentar a depuração com apenas eventos do IntelliTrace. Os eventos do IntelliTrace são eventos do depurador, exceções, eventos do .NET Framework e outros eventos do sistema. Você deve ativar ou desativar eventos específicos para controlar os eventos que registros do IntelliTrace antes de iniciar a depuração. Para obter mais informações, consulte [funcionalidades do IntelliTrace](../debugger/intellitrace-features.md).  
  
 - Ative o evento do IntelliTrace para acesso a arquivos. Vá para o **Ferramentas > Opções > IntelliTrace > eventos do IntelliTrace** página e, em seguida, expanda o **arquivo** categoria. Verifique o **arquivo** categoria de evento. Isso faz com que todos os arquivos eventos (acessar, fechar, excluir) a ser verificada.

## <a name="create-your-app"></a>Crie seu aplicativo
  
1.  Crie um aplicativo de console C#. No arquivo Program.cs, adicione o seguinte `using` instrução:  
  
    ```csharp  
    using System.IO;  
    ```  
  
2.  Criar um <xref:System.IO.FileStream> no método Main, lê-lo, feche-o e exclua o arquivo. Adicione outra linha apenas para ter um local para definir um ponto de interrupção:  
  
    ```csharp  
    static void Main(string[] args)  
    {  
        FileStream fs = File.Create("WordSearchInputs.txt");  
        fs.ReadByte();  
        fs.Close();  
        File.Delete("WordSearchInputs.txt");  
  
        Console.WriteLine("done");  
    }  
    ```  
  
3.  Definir um ponto de interrupção em `Console.WriteLine("done");`  

## <a name="start-debugging-and-view-intellitrace-events"></a>Iniciar a depuração e exibir eventos do IntelliTrace
  
1.  Inicie a depuração como de costume. (Pressione **F5** ou clique em **Depurar > Iniciar depuração**.  
  
    > [!TIP]
    >  Manter o **locais** e **Autos** abrir o windows durante a depuração para ver e anote os valores nessas janelas.  
  
2.  Interrompe a execução no ponto de interrupção. Se você não vir o **ferramentas de diagnóstico** janela, clique em **Depurar > Windows > eventos do IntelliTrace**.  
  
     No **ferramentas de diagnóstico** janela, localizar o **eventos** guia (você deve ver 3 guias, **eventos**, **uso de memória**, e **CPU Uso**). O **eventos** guia mostra uma lista cronológica de eventos, terminando com o último evento antes do depurador interrompe a execução. Você verá um evento chamado **WordSearchInputs.txt acesso**.  
  
     Captura de tela a seguir é do Visual Studio 2015 atualização 1.  
  
     ![IntelliTrace&#45;Update1](../debugger/media/intellitrace-update1.png "IntelliTrace-Update1")  
  
3.  Selecione o evento para expandir seus detalhes.  
  
     Captura de tela a seguir é do Visual Studio 2015 atualização 1.  
  
     ![IntelliTraceUpdate1&#45;SingleEvent](../debugger/media/intellitraceupdate1-singleevent.png "IntelliTraceUpdate1-SingleEvent")  
  
     Você pode escolher o link de pathname para abrir o arquivo. Se o nome de caminho completo não estiver disponível, o **abrir arquivo** caixa de diálogo é exibida.  
  
     Clique em **Ativar depuração histórica**, que define contexto do depurador para a hora em que o evento selecionado foi coletado, mostrando os dados históricos no **pilha de chamadas**, **locais** e os outros participantes janelas do depurador. Se o código-fonte estiver disponível, o Visual Studio moverá o ponteiro para o código correspondente na janela de origem para que você possa examiná-lo.  
  
     Captura de tela a seguir é do Visual Studio 2015 atualização 1.  
  
     ![HistoricalDebugging&#45;Update1](../debugger/media/historicaldebugging-update1.png "HistoricalDebugging-Update1")  
  
4.  Se você não encontrou o bug, tente examinar outros eventos que levam ao bug. Você também pode ter informações de registro de chamadas do IntelliTrace para que você possa percorrer chamadas de função. 
  
## <a name="next-steps"></a>Próximas etapas

Você pode usar alguns dos recursos avançados do IntelliTrace com depuração histórica:

 - Para exibir instantâneos, consulte [exibir instantâneos usando IntelliTrace etapa-back](../debugger/how-to-use-intellitrace-step-back.md)
 - Para saber como inspecionar variáveis e navegar pelo código, consulte [inspecionar o seu aplicativo com depuração histórica](../debugger/historical-debugging-inspect-app.md)