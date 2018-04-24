---
title: 'Como: depurar o código otimizado | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- breakpoints, in optimized code
- debugging [C++], optimized code
- optimization, debug builds
- debug builds, optimizing
- optimized code, debugging
ms.assetid: fc8eeeb8-6629-4c9b-99f7-2016aee81dff
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9610f71a197c47521e2139d40aff1afde6a8a894
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2018
---
# <a name="how-to-debug-optimized-code"></a>Como depurar o código otimizado
> [!NOTE]
>  As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas. Para alterar as configurações, escolha Importar e Exportar Configurações no menu Ferramentas. Para obter mais informações, confira [Personalizar o IDE do Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
> [!NOTE]
>  O [/Zo (aprimorar a otimização de depuração)](/cpp/build/reference/zo-enhance-optimized-debugging)opção de compilador (introduzida na atualização 3 do Visual Studio) gera as informações de depuração de código otimizado (projetos que não são criados com o **/Od** opção de compilador. Consulte [/O opções (otimizar código)](/cpp/build/reference/o-options-optimize-code)). Isso inclui suporte aprimorado para depuração locais variáveis e funções embutidas.  
>   
>  [Editar e continuar](../debugger/edit-and-continue-visual-csharp.md) é desabilitada quando o **/Zo** ocompiler opção é usada.  
  
 Quando o compilador otimiza o código, ele reposiciona e reclassifica instruções. Isso resulta em um código compilado mais eficiente. Devido a esse rearranjo, o depurador nem sempre pode identificar o código-fonte que corresponde a um conjunto de instruções.  
  
 A otimização pode afetar:  
  
-   As variáveis locais, que podem ser removidas pelo otimizador ou movidas para locais que o depurador não entende.  
  
-   Posições dentro de uma função, que são alteradas quando o otimizador mescla blocos de código.  
  
-   Nomes de função para quadros na pilha de chamadas, que pode estar errado se o otimizador mesclar duas funções.  
  
 Os quadros que você vê na pilha de chamadas estão quase sempre corretos, porém, supondo que você tenha símbolos para todos os quadros. Os quadros na pilha de chamadas estarão incorretos se você tiver um dano na pilha, se você tiver as funções escritas na linguagem assembly, ou se houver quadros do sistema operacional sem símbolos correspondentes na pilha de chamadas.  
  
 As variáveis globais e estáticas são sempre mostradas corretamente. Da mesma forma que o layout da estrutura. Se você tiver um ponteiro para uma estrutura e o valor do ponteiro estiver correto, cada variável de membro da estrutura mostrará o valor correto.  
  
 Devido a essas restrições, você deverá depurar usando uma versão não otimizada do programa se isso for possível. Por padrão, a otimização está desativada na configuração de Depuração de um programa do Visual C++ e ativada na configuração de Versão.  
  
 No entanto, um bug pode aparecer somente em uma versão otimizada de um programa. Nesse caso, você deverá depurar o código otimizado.  
  
### <a name="to-turn-on-optimization-in-a-debug-build-configuration"></a>Para ativar a otimização em uma configuração da compilação de Depuração  
  
1.  Quando você cria um novo projeto, selecione o destino de `Win32 Debug`. Use o `Win32``Debug` de destino até que o programa é totalmente depurado e você está pronto para criar um `Win32 Release` destino. O compilador não otimiza o destino de `Win32 Debug`.  
  
2.  Selecione o projeto no Gerenciador de Soluções.  
  
3.  Sobre o **exibição** menu, clique em **páginas de propriedade**.  
  
4.  No **páginas de propriedade** caixa de diálogo caixa, certifique-se de `Debug` está selecionado no **configuração** lista suspensa.  
  
5.  Na exibição de pasta, à esquerda, selecione o **C/C++** pasta.  
  
6.  Sob o **C++** pasta, selecione `Optimization`.  
  
7.  Na lista de propriedades à direita, localize `Optimization`. A configuração ao lado dele provavelmente diz `Disabled (` [/Od](/cpp/build/reference/od-disable-debug)`)`. Escolha uma das outras opções (`Minimum Size``(`[/O1](/cpp/build/reference/o1-o2-minimize-size-maximize-speed)`)`, `Maximum Speed``(` [/O2](/cpp/build/reference/o1-o2-minimize-size-maximize-speed)`)`, `Full Optimization``(` [/Ox](/cpp/build/reference/ox-full-optimization) `)`, ou `Custom`).  
  
8.  Se você escolher a opção `Custom` para `Optimization`, agora poderá definir opções para qualquer uma das outras propriedades mostradas na lista de propriedades.  
  
9. Selecione as propriedades de configuração, C/C++, nó de linha de comando de página de propriedades do projeto e adicionar `(` [/Zo](/cpp/build/reference/zo-enhance-optimized-debugging) `)` para o **opções adicionais** caixa de texto.  
  
    > [!WARNING]
    >  `/Zo` requer o Visual Studio 2013 Update 3 ou posterior.  
    >   
    >  Adicionando `/Zo` desabilitará [editar e continuar](../debugger/edit-and-continue-visual-csharp.md).  
  
 Quando você depura o código otimizado, use o **desmontagem** janela para ver quais instruções são realmente criadas e executadas. Quando você define pontos de interrupção, precisa saber que o ponto de interrupção pode mover junto com uma instrução. Por exemplo, considere o seguinte código:  
  
```  
for (x=0; x<10; x++)  
```  
  
 Suponha que você defina um ponto de interrupção nesta linha. Você pode esperar que o ponto de interrupção seja atingido 10 vezes, mas se o código for otimizado, o ponto de interrupção será atingido somente uma vez. Isso ocorre porque a primeira instrução define o valor de `x` como 0. O compilador reconhece que isso somente precisa ser feito uma vez e o move para fora do loop. O ponto de interrupção também será movido. As instruções que comparam e incrementam `x` permanecem dentro do loop. Quando você exibe o **desmontagem** janela, o [unidade da etapa](http://msdn.microsoft.com/en-us/8791dac9-64d1-4bb9-b59e-8d59af1833f9) é definida automaticamente como instruções para proporcionar maior controle, que é útil quando você percorrer o código otimizado.  
  
## <a name="see-also"></a>Consulte também  
 [Segurança do depurador](../debugger/debugger-security.md)   
 [Depurando código nativo](../debugger/debugging-native-code.md)