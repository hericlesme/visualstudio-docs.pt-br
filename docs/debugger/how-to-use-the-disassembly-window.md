---
title: Exibir o código de desmontagem no depurador do Visual Studio | Microsoft Docs
ms.custom: H1Hack27Feb2017
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.disassembly
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- assembly language, debugging inline assembly code
- breakpoints, Disassembly window
- Disassembly window
- machine code
ms.assetid: eaf84dd0-c82d-481b-af51-690b74e7794c
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 46c0ae689a9d514983aeb747bebc6cb9905c6e11
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2018
---
# <a name="view-disassembly-code-in-the-visual-studio-debugger"></a>Exibir o código de desmontagem no depurador do Visual Studio
Este recurso está disponível somente se a depuração de nível de endereço está habilitada a **opções** caixa de diálogo, **depuração** nó. Não está disponível para depuração de Script ou SQL.  
  
 O **desmontagem** janela mostra código assembly correspondente às instruções criadas pelo compilador. Se você estiver depurando código gerenciado, essas instruções de assembly correspondem ao código nativo criado pelo compilador JIT (Just-in-Time), não a linguagem intermediária da Microsoft (MSIL) gerada pelo compilador do Visual Studio.  
  
 Além de instruções assembly, o **desmontagem** janela pode exibir as seguintes informações opcionais:  
  
-   Endereço de memória onde cada instrução está localizada. Para aplicativos nativos, este é o endereço de memória real. Para o Visual Basic, C# ou código gerenciado, é um deslocamento do início da função.  
  
-   O código-fonte do qual o código do assembly deriva.  
  
-   As representações byte a byte de código do computador real ou instruções de MSIL.  
  
-   Nomes do símbolo para os endereços de memória.  
  
-   Números de linha que correspondem ao código-fonte.  
  
 As instruções da linguagem de assembly consistem em mnemônica, que são abreviações para nomes de instrução e símbolos que representam variáveis, registros e constantes. Cada instrução de linguagem de máquina é representada por um mnemônico de assembly da linguagem, geralmente seguido por uma ou mais variáveis, registros ou constantes.  
  
 Se você não puder ler a linguagem assembly e quiser aproveitar a janela Desmontagem, consulte um bom livro sobre programação da linguagem de assembly. A programação da linguagem de assembly está além do escopo do que podemos abordar nesta breve introdução à janela Desmontagem.  
  
 Como o código do assembly depende intensamente dos registros do processador ou, no caso do código gerenciado, os registros do Common Language Runtime, você normalmente achará útil usar a janela Desmontagem junto com a janela Registros, o que permite examinar o conteúdo do registro.  
  
 Você provavelmente jamais desejará ou precisará exibir instruções de código de máquina em seu formato bruto e numérico, em vez da linguagem de assembly. No entanto, se quiser fazer isso, poderá usar a janela Memória para essa finalidade ou escolher Bytes de Código no menu de atalho na janela Desmontagem.  
  
> [!NOTE]
>  As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas. Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**. Para obter mais informações, confira [Personalizar o IDE do Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
### <a name="to-display-the-disassembly-window"></a>Para exibir a janela Desmontagem  
  
-   Enquanto você está depurando, selecione **Depurar > Windows** e, em seguida, clique em **desmontagem**.
  
### <a name="to-turn-optional-information-on-or-off"></a>Para ativar ou desativar as informações opcionais  
  
-   Clique com botão direito do **desmontagem** janela, marque ou desmarque as opções desejadas no menu de atalho.  
  
     Uma seta amarela na margem esquerda marca o local do ponto de execução atual. Para o código nativo, isso corresponde ao contador do programa da CPU. Este local mostra a próxima instrução que será executada em seu programa.  
  
     Para obter mais informações, consulte [paginação para cima ou para baixo na memória](../debugger/how-to-page-up-or-down-in-memory.md).  
  
## <a name="see-also"></a>Consulte também  
 [Exibindo dados no depurador](../debugger/viewing-data-in-the-debugger.md)   
 [Como usar a janela Registros](../debugger/how-to-use-the-registers-window.md)