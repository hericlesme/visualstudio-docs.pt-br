---
title: 'Como: depurar com a origem do Code Center Premium | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Code Center Premium
- debugging [Visual Studio], Code Center Premium
ms.assetid: 18b4769d-b007-4428-9dae-9e72c283ff0d
caps.latest.revision: "23"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: d7405deed95f14314215b869a02bcf8a1afddea2
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-debug-with-code-center-premium-source"></a>Como depurar com a origem do Code Center Premium
Com o depurador do [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)], você pode depurar a origem compartilhada segura do Microsoft MSDN Code Center Premium.  
  
 Este tópico explica como configurar e depurar o código-fonte superior do Code Center Premium no Visual Studio.  
  
### <a name="to-prepare-for-debugging-with-code-center-premium"></a>Para preparar para depurar com o Code Center Premium  
  
1.  Conecte seu leitor de cartão inteligente e insira o cartão obtido da Shared Source Initiative.  
  
2.  Inicie o Visual Studio.  
  
3.  No menu **Ferramentas**, clique em **Opções**.  
  
4.  No **opções** caixa de diálogo, abra o **depuração** nó e clique em **geral**.  
  
5.  Limpar o **habilitar apenas meu código (somente gerenciado)** caixa de seleção.  
  
6.  Selecione **habilitar Habilitar suporte de servidor de origem**.  
  
7.  Limpar **requer arquivos de origem correspondam exatamente à versão original**.  
  
8.  Sob o **depuração** nó, clique em **símbolos**.  
  
9. No **o arquivo de símbolo (. PDB) locais** caixa, desmarque o **Microsoft Server símbolos** caixa de seleção e adicione os seguintes locais:  
  
     `https://codepremium.msdn.microsoft.com/symbols`  
  
     `src=https://codepremium.msdn.microsoft.com/source/Visual%20Studio%202010/SP1/`  
  
    > [!NOTE]
    >  Certifique-se de incluir a barra à direita **/**  no final do caminho.  
  
     Mova esses locais até a parte superior da lista para garantir que os símbolos sejam carregados primeiro.  
  
    > [!NOTE]
    >  Esses locais do Code Center Premium devem ser listados primeiro para que sejam os primeiros locais a serem carregados. No Visual Studio 2010, você não pode mover os servidores acima de **Microsoft Symbol Servers** entrada, por isso, você deve desmarcar a caixa de seleção.  
    >   
    >  Para carregar símbolos dos símbolos Microsoft durante uma sessão de depuração, faça isso:  
    >   
    >  1.  Sobre o **depurar** menu, escolha **Windows** e, em seguida, escolha **módulos**.  
    > 2.  Selecione o módulo para o qual você deseja símbolos e abra o menu de atalho. Escolha **carregar símbolos de** e, em seguida, escolha **Microsoft Symbol Servers**.  
  
10. No **Cache símbolos de servidores de símbolos neste diretório** , digite um local como `C:\symbols` onde Code Center Premium pode armazenar em cache os símbolos. O armazenamento em cache dos símbolos pode melhorar significativamente o desempenho durante a depuração.  
  
     Se você tiver dificuldade para depurar código-fonte com o [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] depois de concluir este procedimento, verifique o local do cache para arquivos previamente armazenados em cache e arquivos de símbolo desatualizados. Remova os arquivos antigos desatualizados.  
  
11. Clique em **OK**.  
  
12. Reinicie o [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] para assegurar que as configurações persistiram.  
  
### <a name="to-debug-your-source-code-using-attach-to-process"></a>Para depurar seu código-fonte usando Anexar ao Processo  
  
1.  Conecte seu leitor de cartão inteligente e insira o cartão obtido da Shared Source Initiative.  
  
2.  Inicie o Visual Studio.  
  
3.  Abra seu projeto do Visual Studio.  
  
4.  Sobre o **ferramentas** menu, clique em **anexar ao processo**.  
  
5.  No **anexar ao processo** caixa de diálogo, clique em **selecione**.  
  
6.  No **Selecionar tipo de código** caixa de diálogo **detectar esses tipos de código**, selecione **nativo**, **gerenciado**, e **gerenciados ( v 4.0)**.  
  
7.  Clique em **Okey** para ignorar o **Selecionar tipo de código** caixa de diálogo.  
  
8.  No **processos disponíveis** , selecione o processo que você deseja depurar.  
  
9. Clique em **Anexar**.  
  
10. Quando você for solicitado a confirmar seu certificado, clique em **Okey**. Em seguida, insira seu PIN. Aceite os termos de uso do Code Center Premium, se for solicitado.  
  
     O download de símbolos pode demorar muito tempo, dependendo da velocidade da rede. A barra de status indica quando todos os símbolos foram baixados com êxito.  
  
11. Repita as etapas de anexação para todos os projetos gerenciados em sua solução.  
  
### <a name="to-debug-source-code-from-an-existing-solution"></a>Para depurar o código-fonte de uma solução existente  
  
1.  Em **Solution Explorer**, abra o menu de atalho para a solução e, em seguida, escolha **propriedades**.  
  
2.  Na caixa de diálogo páginas de propriedades da solução, escolha **depurar arquivos de origem** no **propriedades comuns** nó.  
  
3.  Adicione o seguinte local para o **diretórios que contêm arquivos de origem** lista:  
  
     `https://codepremium.msdn.microsoft.com/source/Visual%20Studio%202010/SP1/`  
  
    > [!NOTE]
    >  Certifique-se de incluir a barra à direita **/**  no final do caminho.  
  
4.  Para cada projeto gerenciado na sua solução, faça o seguinte  
  
    1.  No Solution Explorer, abra o menu de atalho para o projeto e, em seguida, escolha **propriedades**.  
  
    2.  Selecione **depurar** e, em seguida, escolha **habilitar a depuração de código não gerenciado**.  
  
### <a name="to-debug-your-solution-with-code-center-premium-source"></a>Para depurar sua solução com código do Code Center Premium  
  
1.  Na sua classe `Package`, defina um ponto de interrupção no construtor do pacote.  
  
2.  No `Debug` menu, clique em **iniciar depuração**.  
  
3.  Quando você atinge o ponto de interrupção no construtor de pacote, vá para o **pilha de chamadas** janela e com o botão direito do quadro de pilha do assembly que você deseja carregar símbolos de, em seguida, clique em **carregar símbolos**.  
  
     Clique duas vezes no quadro de chamada para carregar a origem.  
  
### <a name="to-browse-source-code-on-code-center-premium"></a>Para procurar o código-fonte no Code Center Premium  
  
1.  Conecte seu leitor de cartão inteligente e insira o cartão obtido da Shared Source Initiative.  
  
2.  Inicie o Internet Explorer e insira esta URL: `https://codepremium.msdn.microsoft.com`  
  
3.  Navegue para encontrar a fonte que você deseja.  
  
## <a name="see-also"></a>Consulte também  
 [Preparação e configurações do depurador](../debugger/debugger-settings-and-preparation.md)   
 [Segurança do depurador](../debugger/debugger-security.md)   
 [Code Center Premium](http://www.microsoft.com/resources/sharedsource/ccp.mspx)