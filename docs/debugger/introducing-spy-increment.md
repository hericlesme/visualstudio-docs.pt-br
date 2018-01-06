---
title: Apresentando o Spy + + | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Spy++
ms.assetid: 733b514b-63a9-402d-89aa-4f0416766655
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: cb12ef13e73e33b213d2b8ca79c2439b517fbda9
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="introducing-spy"></a>Introdução a Spy++
Spy + + permite que você execute as seguintes tarefas:  
  
-   Exiba um gráfico de árvore de relações entre objetos do sistema. Isso inclui [processos](../debugger/processes-view.md), [threads](../debugger/threads-view.md), e [windows](../debugger/windows-view.md).  
  
-   Pesquisar especificado [windows](../debugger/how-to-search-for-a-window-in-windows-view.md), [threads](../debugger/how-to-search-for-a-thread-in-threads-view.md), [processos](../debugger/how-to-search-for-a-process-in-processes-view.md), ou [mensagens](../debugger/how-to-search-for-a-message-in-messages-view.md).  
  
-   Exibir as propriedades de selecionado [windows](../debugger/how-to-display-window-properties.md), [threads](../debugger/how-to-display-thread-properties.md), [processos](../debugger/how-to-display-process-properties.md), ou [mensagens](../debugger/how-to-display-message-properties.md).  
  
-   Selecione uma janela, thread, processo ou mensagem diretamente no modo de exibição.  
  
-   Use o [ferramenta localizador](../debugger/how-to-use-the-finder-tool.md) para selecionar uma janela, o posicionamento do ponteiro do mouse.  
  
-   Definir [mensagem opção](../debugger/how-to-open-messages-view-from-find-window.md) usando parâmetros de seleção de log de mensagem complexas.  
  
 Spy + + tem uma barra de ferramentas e hiperlinks para ajudá-lo a trabalhar mais rápido. Ele também fornece um **atualizar** comando para atualizar a exibição ativa, um **ferramenta descobridora de janelas** para fazer a espionagem mais fácil e um **fonte** caixa de diálogo para personalizar o windows de modo de exibição. Além disso, Spy + + permite salvar e restaurar as preferências do usuário.  
  
 Em vários Spy + + windows, clique para exibir um menu de atalho de comandos usados com frequência. Os comandos que são exibidos depende de onde o ponteiro é. Por exemplo, se você clica uma entrada na exibição da janela e a janela selecionada estiver visível, clique em **realçar** no atalho do menu faz com que a borda da janela selecionada para flash, para que possa ser localizado mais facilmente.  
  
> [!NOTE]
>  Há dois outros utilitários semelhantes Spy + +: PView, que mostra detalhes sobre os processos e threads e DDESPY. EXE, que lhe permite monitorar mensagens de troca dinâmica de dados (DDE).  
  
## <a name="64-bit-operating-systems"></a>Sistemas operacionais de 64 bits  
 Há duas versões do Spy + +. A primeira versão, denominada Spy + + (spyxx.exe) é projetada para exibir as mensagens enviadas para uma janela que está em execução em um processo de 32 bits. Por exemplo, o Visual Studio é executado em um processo de 32 bits. Portanto, você pode usar Spy + + para exibir as mensagens enviadas a **Gerenciador de soluções**. Como a configuração padrão para a maioria das compilações no Visual Studio é executado em um processo de 32 bits, a primeira versão do Spy + + é aquele que é [disponível no **ferramentas** menu](../debugger/how-to-start-spy-increment.md) no Visual Studio.  
  
 A segunda versão denominada Spy + + (64 bits) (spyxx_amd64.exe) é projetada para exibir as mensagens enviadas para uma janela que está em execução em um processo de 64 bits. Por exemplo, em um sistema operacional de 64 bits, o bloco de notas é executada em um processo de 64 bits. Portanto, você pode usar Spy + + (64 bits) para exibir as mensagens enviadas para o bloco de notas. Spy + + (64 bits) normalmente está localizado em  
  
 .. \\ *Pasta de instalação do visual Studio*\Common7\Tools\spyxx_amd64.exe.  
  
 Você pode executar qualquer versão do Spy + + diretamente da linha de comando.  
  
> [!NOTE]
>  Embora o nome de arquivo (64 bits) do Spy + + contiver "amd", ele é executado em qualquer x64 sistema operacional Windows.  
  
## <a name="see-also"></a>Consulte também 
 [Como: Iniciar Spy + +](../debugger/how-to-start-spy-increment.md)   
 [Usando Spy + +](../debugger/using-spy-increment.md)   
 [Exibições do Spy + +](../debugger/spy-increment-views.md)   
 [Referência a Spy++](../debugger/spy-increment-reference.md)