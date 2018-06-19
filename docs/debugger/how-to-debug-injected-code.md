---
title: 'Como: depurar código injetado | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.injected
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- assembly language, viewing
- debugging [C++], viewing assembly code
- debugging [C++], injected code
- debugging [C++], enabling source annotation
- injected code
- Show Source Code command [debugger]
- debugging [C++], using attributes
- disassembly code, debugging
ms.assetid: a1b4104d-d49e-451f-a91e-e39ceaf35875
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bf602d8ee670e5fce8602cb50d2aaa1066b501de
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2018
ms.locfileid: "31475149"
---
# <a name="how-to-debug-injected-code"></a>Como depurar código injetado
> [!NOTE]
>  As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas. Para alterar as configurações, escolha Importar e Exportar Configurações no menu Ferramentas. Para obter mais informações, confira [Personalizar o IDE do Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
 Usar atributos pode simplificar muito a programação C++. Para obter mais informações, consulte [conceitos](/cpp/windows/attributed-programming-concepts). Alguns atributos são interpretados diretamente pelo compilador. Outros atributos injetam o código na origem do programa, que o compilador em seguida compila. Este código injetado facilita a programação reduzindo a quantidade de códigos que você precisa escrever. Entretanto, às vezes, um bug pode causar falha no aplicativo ao executar o código injetado. Quando isso acontece, você provavelmente desejará examinar o código injetado. O Visual Studio fornece duas maneiras de ver o código injetado:  
  
-   Você pode exibir o código injetado no **desmontagem** janela.  
  
-   Usando [/Fx](/cpp/build/reference/fx-merge-injected-code), você pode criar um arquivo de origem mesclada que contém código injetado e original.  
  
 O **desmontagem** janela mostra instruções de linguagem assembly que correspondem ao código-fonte e o código injetado por atributos. Além disso, o **desmontagem** janela pode mostrar a anotação do código-fonte.  
  
### <a name="to-turn-on-source-annotation"></a>Para ativar a anotação de origem  
  
-   Clique com botão direito do **desmontagem** janela e escolha **Mostrar código-fonte** no menu de atalho.  
  
     Se você souber o local de um atributo em uma janela de origem, você pode usar o menu de atalho para localizar o código injetado no **desmontagem** janela.  
  
### <a name="to-view-injected-code"></a>Para exibir o código injetado  
  
1.  O depurador deve estar no modo de interrupção.  
  
2.  Em uma janela do código-fonte, coloque o cursor na frente do atributo cujo código injetado você deseja exibir.  
  
3.  Clique com botão direito e selecione **Go To Disassembly** no menu de atalho.  
  
     Se o local de atributo estiver próximo ao ponto de execução atual, você pode selecionar o **desmontagem** janela a partir de **depurar** menu.  
  
### <a name="to-view-the-disassembly-code-at-the-current-execution-point"></a>Para exibir o código de desmontagem no ponto de execução atual  
  
1.  O depurador deve estar no modo de interrupção.  
  
2.  Do **depurar** menu, escolha **Windows**e clique em **desmontagem**.  
  
## <a name="see-also"></a>Consulte também  
 [Segurança do depurador](../debugger/debugger-security.md)   
 [Depurando código nativo](../debugger/debugging-native-code.md)