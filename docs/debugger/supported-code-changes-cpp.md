---
title: "Alterações de código (C++) com suporte | Microsoft Docs"
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
- Edit and Continue, limitations
- supported code changes
- object files, limitations of Edit and Continue
- C# language, supported code changes
- coding, supported code changes
- resource files, limitations of Edit and Continue
- code changes, handling in Edit and Continue
- what's new [C#], supported code changes
- code changes
ms.assetid: f5754363-8a56-417b-b904-b05d9dd26d03
caps.latest.revision: "26"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e7309e17e04627654aaaf2e28a54c75fa2d6993c
ms.sourcegitcommit: 26419ab0cccdc30d279c32d6a841758cfa903806
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/11/2017
---
# <a name="supported-code-changes-c"></a>Alterações de código suportadas (C++)
Editar e continuar para o Visual C++ manipula a maioria dos tipos de alterações de código. Porém, algumas alterações não podem ser aplicadas durante a execução do programa. Para aplicar essas alterações sem suporte, você deverá parar a execução e criar uma versão atualizada do código.  
  
 Consulte [editar e continuar (Visual C++)](../debugger/edit-and-continue-visual-cpp.md) para obter informações sobre como trabalhar com editar e continuar para C++ no Visual Studio.  
  
##  <a name="BKMK_Unsupported_changes"></a>Não há suporte para alterações  
 As seguintes alterações de C/C++ não podem ser aplicadas durante uma sessão de depuração:  
  
-   A maioria das alterações aos dados globais ou estáticos.  
  
-   As alterações nos executáveis que são copiados de outro computador e não são criados localmente.  
  
-   As alterações para um tipo de dados que afeta o layout de um objeto, como, por exemplo, membros de dados de uma classe.  
  
-   Adicionando mais de 64k bytes do novo código ou dados.  
  
-   Adicionando variáveis que exigem um construtor em um ponto antes do ponteiro de instrução.  
  
-   As alterações que afetam o código que exigem a inicialização de tempo de execução.  
  
-   Adicionar manipuladores de exceção, em alguns casos.  
  
-   Alterações aos arquivos de recurso.  
  
-   Alterações ao código em arquivos somente leitura.  
  
-   Alterações ao código sem um arquivo PDB correspondente.  
  
-   Alterações ao código que não tem arquivo de objeto.  
  
 Se você fizer uma das alterações e, em seguida, tente aplicar alterações de código, uma mensagem de erro ou aviso é exibido no **saída** janela.  
  
-   Editar e Continuar não atualiza bibliotecas estáticas. Se você fizer uma alteração em uma biblioteca estática, a execução continuará com a versão antiga e nenhum aviso será emitido.  
  
##  <a name="BKMK_Unsupported_scenarios"></a>Cenários sem suporte  
 Editar e Continuar para C/C++ está indisponível nos seguintes cenários de depuração:  
  
-   Depurando aplicativos nativos compilados com [/Zo (aprimorar a otimização de depuração)](/cpp/build/reference/zo-enhance-optimized-debugging)  
  
-   Em versões do Visual Studio anteriores ao Visual Studio 2015 atualização 1, depurando aplicativos UWP ou componentes. A partir do Visual Studio 2015 atualização 1, você pode usar Editar e continuar em aplicativos C++ UWP e do DirectX, porque ele agora oferece suporte a `/ZI` opção de compilador com o `/bigobj` alternar. Você também pode usar Editar e continuar com binários compilados com o `/FASTLINK` alternar.  
  
-   Depuração no Windows 98.  
  
-   Depuração de modo misto (nativo/gerenciado).  
  
-   Depuração de JavaScript.  
  
-   Depuração de SQL.  
  
-   Depurando um arquivo de despejo.  
  
-   Edição do código após uma exceção não tratada, quando a **desenrolar a pilha de chamadas em exceções não tratadas** opção não estiver selecionada.  
  
-   Depurar um aplicativo usando **anexar a** em vez de executar o aplicativo escolhendo **iniciar** no **depurar** menu.  
  
-   Depurando código otimizado.  
  
-   Depurando uma versão antiga do código depois que uma nova versão não é compilada devido a erros de compilação.  
  
##  <a name="BKMK_Linking_limitations"></a>Limitações de vinculação  
  
###  <a name="BKMK_Linker_options_that_disable_Edit_and_Continue"></a>Opções do vinculador que desativam Editar e continuar  
 As opções de vinculador a seguir desabilitam Editar e Continuar:  
  
-   Configuração **/OPT: REF**, **/OPT: ICF**, ou **/incremental: no** desativa editar e continuar com o seguinte aviso:  
  
     LINK : warning LNK4075: ignoring /EDITANDCONTINUE due to /OPT  
  
     especificação  
  
-   Configuração **/ORDER**, **/versão**, ou **/Force** desativa editar e continuar com este aviso:  
  
     LINK : warning LNK4075: ignoring /INCREMENTAL due to /option  
  
     especificação  
  
-   Definir qualquer opção que evite a criação de um arquivo de banco de dados do programa (.pdb) desabilita Editar e Continuar sem aviso específico.  
  
###  <a name="BKMK_Auto_relinking_limitations"></a>Vinculando novamente limitações de auto  
 Por padrão, Editar e Continuar vincula novamente o programa ao final de uma sessão de depuração para criar um executável atualizado.  
  
 Editar e Continuar não pode vincular o programa novamente se você o depurá-lo a partir de um local diferente do local de compilação original. Uma mensagem informa que você precisa recompilar manualmente.  
  
 Editar e Continuar não recompila bibliotecas estáticas. Se você fizer alterações em uma biblioteca estática usando editar e continuar, você precisa recriar manualmente os aplicativos de biblioteca e vincular usá-lo.  
  
 Editar e Continuar não invoca as etapas personalizadas de compilação. Se o seu programa usa etapas personalizadas de compilação, recompile manualmente de modo que as etapas personalizadas de compilação possam ser invocadas. Nesse caso, você pode desabilitar nova vinculação após Editar e Continuar para assegurar que seja solicitado a fazer a recompilação manualmente.  
  
 **Para desabilitar vinculando novamente depois de editar e continuar**  
  
1.  Sobre o **depurar** menu, escolha **opções e configurações**.  
  
2.  No **opções** caixa de diálogo de **depuração** nó e selecione o **editar e continuar** nó.  
  
3.  Limpar o **vincular novamente as alterações de código após a depuração** caixa de seleção.  
  
##  <a name="BKMK_Precompiled_Header_Limitations"></a>Limitações de cabeçalho pré-compilado  
 Por padrão, Editar e Continuar carrega e processa cabeçalhos pré-compilados no plano de fundo para acelerar o processamento de alterações de código. O carregamento de cabeçalhos pré-compilados requer a alocação de memória física, o que pode ser um problema se você estiver compilando em um computador com RAM limitada. Você pode determinar se isso pode ser um problema usando o Gerenciador de tarefas do Windows para determinar a quantidade de memória física disponível enquanto você está depurando. Se esse valor for maior que o tamanho dos cabeçalhos pré-compilados, Editar e Continuar não terá problemas. Se o valor for menor que o tamanho dos cabeçalhos pré-compilados, você pode impedir que Editar e Continuar carregue cabeçalhos pré-compilados no plano de fundo.  
  
 **Para desabilitar o carregamento de plano de fundo de cabeçalhos pré-compilados para editar e continuar**  
  
1.  Sobre o **depurar** menu, escolha **opções e configurações**.  
  
2.  No **opções** caixa de diálogo de **depuração** nó e selecione o **editar e continuar** nó.  
  
3.  Limpar o **permitir pré-compilação** caixa de seleção.  
  
##  <a name="BKMK_IDL_Attribute_Limitations"></a>Limitações de atributos IDL  
 Editar e Continuar não regeneram arquivos IDL (definição da interface). Consequentemente, as alterações aos atributos de IDL não serão refletidas ao depurar. Para ver o resultado das alterações em atributos IDL, você deve parar a depuração e recriar seu aplicativo. Editar e Continuar não gera um erro ou um aviso se os atributos de IDL tiverem sido alterados. Para obter mais informações, consulte [atributos IDL](/cpp/windows/idl-attributes).  
  
## <a name="see-also"></a>Consulte também  
 [Editar e continuar (Visual C++)](../debugger/edit-and-continue-visual-cpp.md)