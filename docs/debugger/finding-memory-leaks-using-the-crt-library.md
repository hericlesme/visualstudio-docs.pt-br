---
title: "Localizando perdas de memória usando a biblioteca CRT | Microsoft Docs"
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
- breakpoints, on memory allocation
- _CrtMemState
- _CrtMemCheckpoint
- memory leaks
- _CrtMemDifference
- memory leaks, detecting and isolating
- _CrtDumpMemoryLeaks
- _CrtSetBreakAlloc
- _crtBreakAlloc
- _CrtSetReportMode
- memory, debugging
- _CrtMemDumpStatistics
- debugging memory leaks
- _CRTDBG_MAP_ALLOC
- _CrtSetDbgFlag
ms.assetid: cf6dc7a6-cd12-4283-b1b6-ea53915f7ed1
caps.latest.revision: "28"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e3c95f24db0dc158b668f0e324fd5bac066dd4ff
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="finding-memory-leaks-using-the-crt-library"></a>Localizando perdas de memória usando a biblioteca CRT
Vazamentos de memória, definidos como a falha em desalocar corretamente a memória anteriormente alocada, estão entre os bugs mais sutis e difíceis de detectar em aplicativos C/C++. Um vazamento de memória pequeno não pode ser observado no início, mas ao longo do tempo, um vazamento de memória progressivo pode causar os sintomas que variam de desempenho reduzido a falhar quando o aplicativo é executado sem memória. Pior, um aplicativo de escape que usa toda a memória disponível pode causar a falha de outro aplicativo, criando a confusão a respeito de que o aplicativo é responsável. Até mesmo vazamentos de memória aparentemente inofensivos podem ser sintomáticos de outros problemas que devem ser corrigidos.  
  
 O depurador do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] e as bibliotecas em tempo de execução (CRT) do C fornecem os meios para detectar e identificar vazamentos de memória.  
  
## <a name="enabling-memory-leak-detection"></a>Habilitando a detecção de vazamento de memória  
 As principais ferramentas para detectar memória vazamentos são bibliotecas de tempo de execução do C (CRT) e o depurador depura funções heap.  
  
 Para ativar as funções da heap de depuração, inclua as seguintes instruções em seu programa:  
  
```  
#define _CRTDBG_MAP_ALLOC  
#include <stdlib.h>  
#include <crtdbg.h>  
```  
  
 Para que as funções CRT funcionem corretamente, as instruções `#include` devem seguir a ordem mostrada aqui.  
  
 Incluindo mapas crtdbg o `malloc` e [livre](/cpp/c-runtime-library/reference/free) funções para as versões de depuração, [malloc_dbg](/cpp/c-runtime-library/reference/malloc-dbg) e `free`, que controlam alocação de memória e a desalocação. Esse mapeamento ocorre apenas em compilações de depuração, que tem `_DEBUG`. Compilações lançadas usam as funções `malloc` e `free`.  
  
 A declaração de `#define` mapeia uma versão de base de funções heap de CRT para a versão de depuração correspondente. Se você omitir a instrução `#define`, o despejo de vazamento de memória será menos detalhado.  
  
 Após ser habilitado, o heap de depuração funciona usando essas declarações. Você poderá fazer uma chamada a `_CrtDumpMemoryLeaks` antes de um ponto de saída do aplicativo para exibir um relatório de vazamento de memória quando seu aplicativo for encerrado:  
  
```  
_CrtDumpMemoryLeaks();  
```  
  
 Se seu aplicativo tiver várias saídas, você não precisa colocar manualmente uma chamada para [crtdumpmemoryleaks](/cpp/c-runtime-library/reference/crtdumpmemoryleaks) em cada ponto de saída. Uma chamada para `_CrtSetDbgFlag` no início do seu aplicativo causará uma chamada automática para `_CrtDumpMemoryLeaks` em cada ponto de saída. Você deve definir os dois campos de bits mostrados aqui:  
  
```  
_CrtSetDbgFlag ( _CRTDBG_ALLOC_MEM_DF | _CRTDBG_LEAK_CHECK_DF );  
```  
  
 Por padrão, `_CrtDumpMemoryLeaks` gera o relatório de vazamento de memória para o **depurar** painel do **saída** janela. Você pode usar `_CrtSetReportMode` para redirecionar o relatório para outro local.  
  
 Se você usar uma biblioteca, a biblioteca poderá redefinir a saída para outro local. Nesse caso, você pode definir o local de saída para o **saída** janela, conforme mostrado aqui:  
  
```  
_CrtSetReportMode( _CRT_ERROR, _CRTDBG_MODE_DEBUG );  
```  
  
## <a name="interpreting-the-memory-leak-report"></a>Interpretando o relatório de vazamento de memória  
 Se seu aplicativo não definir `_CRTDBG_MAP_ALLOC`, [crtdumpmemoryleaks](/cpp/c-runtime-library/reference/crtdumpmemoryleaks) exibe um relatório de vazamento de memória que tem esta aparência:  
  
```  
Detected memory leaks!  
Dumping objects ->  
{18} normal block at 0x00780E80, 64 bytes long.  
 Data: <                > CD CD CD CD CD CD CD CD CD CD CD CD CD CD CD CD  
Object dump complete.  
```  
  
 Se o seu aplicativo definir `_CRTDBG_MAP_ALLOC`, o relatório de vazamento de memória se parecerá com este:  
  
```  
Detected memory leaks!  
Dumping objects ->  
c:\users\username\documents\projects\leaktest\leaktest.cpp(20) : {18}   
normal block at 0x00780E80, 64 bytes long.  
 Data: <                > CD CD CD CD CD CD CD CD CD CD CD CD CD CD CD CD  
Object dump complete.  
```  
  
 A diferença é que o segundo relatório mostra o nome do arquivo e número da linha no qual a memória vazada é atribuída primeiro.  
  
 Se você definir `_CRTDBG_MAP_ALLOC` ou não, o relatório de vazamento de memória exibirá as seguintes informações:  
  
-   O número de alocação de memória, que é `18` nesse exemplo  
  
-   O [bloquear tipo](http://msdn.microsoft.com/en-us/e2f42faf-0687-49e7-aa1f-916038354f97), que é `normal` neste exemplo.  
  
-   O número de alocação de memória hexadecimal, que é `0x00780E80` nesse exemplo.  
  
-   O tamanho do bloco, `64 bytes` neste exemplo.  
  
-   Os primeiros 16 bytes de dados no bloco, no formulário hexadecimal.  
  
 O relatório de vazamento de memória identifica um bloco de memória como normal, cliente, ou CRT. Um *bloco normal* comum memória alocada pelo seu programa. Um *blocos de cliente* é um tipo especial de bloco de memória usado por programas MFC para objetos que exigem um destruidor. O operador MFC `new` cria um bloco normal ou um bloco de cliente, como apropriado para o objeto que estiver sendo criado. Um *bloco CRT* alocada pela biblioteca CRT para seu próprio uso. A biblioteca de CRT trata a desalocação desses blocos. Portanto, é improvável que você os veja no relatório de vazamento de memória a menos que algo esteja significativamente errado, por exemplo, a biblioteca de CRT está danificada.  
  
 Há dois tipos de outros blocos de memória que nunca aparecem nos relatórios de escape de memória. Um *bloco livre* é a memória que foi liberada. Isso significa que não está vazado, por definição. Um *ignorar bloco* é a memória que você tenha marcado explicitamente para excluí-la a partir do relatório de vazamento de memória.  
  
 Essas técnicas funcionam para a memória alocada usando a função de CRT `malloc` padrão. Se seu programa aloca memória usando o C++ `new` operador, no entanto, você pode ver apenas o número de arquivos e linhas em que a implementação do global `operator new` chamadas `_malloc_dbg` no relatório de vazamento de memória. Como esse comportamento não é muito útil, você pode alterá-lo para relatar a linha que fez a alocação usando uma macro parecida com esta: 
 
```C++  
#ifdef _DEBUG
    #define DBG_NEW new ( _NORMAL_BLOCK , __FILE__ , __LINE__ )
    // Replace _NORMAL_BLOCK with _CLIENT_BLOCK if you want the
    // allocations to be of _CLIENT_BLOCK type
#else
    #define DBG_NEW new
#endif
```  
  
Agora você pode substituir o `new` operador usando o `DBG_NEW` macro em seu código. Em compilações de depuração, isso usa uma sobrecarga global `operator new` que usa parâmetros adicionais para o tipo de bloco, o arquivo e o número de linha. Esta sobrecarga do `new` chamadas `_malloc_dbg` para registrar as informações extras. Quando você usa `DBG_NEW`, o vazamento de memória relatórios mostram o nome de arquivo e número de linha em que os objetos vazados foram alocados. Em compilações para venda, ele usa o padrão `new`. (Não é recomendável criar uma macro de pré-processador denominada `new`, ou qualquer outra palavra-chave idioma.) Aqui está um exemplo da técnica:  
  
```C++  
// debug_new.cpp
// compile by using: cl /EHsc /W4 /D_DEBUG /MDd debug_new.cpp
#define _CRTDBG_MAP_ALLOC
#include <cstdlib>
#include <crtdbg.h>

#ifdef _DEBUG
    #define DBG_NEW new ( _NORMAL_BLOCK , __FILE__ , __LINE__ )
    // Replace _NORMAL_BLOCK with _CLIENT_BLOCK if you want the
    // allocations to be of _CLIENT_BLOCK type
#else
    #define DBG_NEW new
#endif

struct Pod {
    int x;
};

void main() {
    Pod* pPod = DBG_NEW Pod;
    pPod = DBG_NEW Pod; // Oops, leaked the original pPod!
    delete pPod;

    _CrtDumpMemoryLeaks();
}
```  
  
Quando você executar esse código no depurador do Visual Studio, a chamada para `_CrtDumpMemoryLeaks` gera um relatório no **saída** janela que é semelhante a este:  
  
```Output  
Detected memory leaks!
Dumping objects ->
c:\users\username\documents\projects\debug_new\debug_new.cpp(20) : {75}
 normal block at 0x0098B8C8, 4 bytes long.
 Data: <    > CD CD CD CD 
Object dump complete.
```  
  
Isso indica que a alocação vazada foi na linha 20 debug_new.cpp.  
  
## <a name="setting-breakpoints-on-a-memory-allocation-number"></a>Pontos de interrupção em um Número de Alocação de Memória  
 O número de alocação de memória informa quando um bloco de memória vazado tiver sido atribuído. Um bloco com uma alocação de memória de 18, por exemplo, é o 18º bloco de memória alocado durante a execução do aplicativo. O relatório de CRT conta todas as alocações bloco de memória durante a execução. Isso inclui as alocações pela biblioteca de CRT e por outras bibliotecas, como o MFC. Portanto, um bloco com um número de alocação de memória de 18 não pode ser o 18º bloco de memória atribuído pelo seu código. Normalmente, não será.  
  
 Você pode usar o número de alocação para definir um ponto de interrupção na alocação da memória.  
  
#### <a name="to-set-a-memory-allocation-breakpoint-using-the-watch-window"></a>Para definir um ponto de interrupção de alocação de memória usando a janela Inspeção  
  
1.  Defina um ponto de interrupção no início do seu aplicativo, e depois inicie seu aplicativo.  
  
2.  Quando o aplicativo for interrompido no ponto de interrupção, o **inspecionar** janela.  
  
3.  No **inspecionar** , digite `_crtBreakAlloc` no **nome** coluna.  
  
     Se estiver usando a versão com multithread da DLL da biblioteca CRT (a opção /MD), inclua o operador de contexto: `{,,ucrtbased.dll}_crtBreakAlloc`  
  
4.  Pressione **retornar**.  
  
     O depurador avalia a chamada e coloca o resultado no **valor** coluna. Esse valor será -1 se você não tiver configurado qualquer ponto de interrupção em alocações de memória.  
  
5.  No **valor** coluna, substitua o valor mostrado com o número de alocação da alocação de memória em que você deseja interromper.  
  
 Após definir um ponto de interrupção em um número de alocação de memória, você poderá continuar a depuração. Tenha cuidado ao executar o programa nas mesmas condições que a execução anterior de modo que a ordem de alocação de memória não seja alterada. Quando o programa for interrompido na alocação de memória especificado, você pode usar o **pilha de chamadas** janela e outras janelas do depurador para determinar as condições sob as quais a memória foi alocada. Em seguida, você pode continuar a execução para observar o que acontece ao objeto e determinar o motivo dele não ser deslocado corretamente.  
  
 Definindo um ponto de interrupção de dados no objeto também pode ser útil. Para obter mais informações, consulte [usando pontos de interrupção](../debugger/using-breakpoints.md).  
  
 Você também pode definir pontos de interrupção de alocação de memória no código. Há duas formas de fazer isso:  
  
```  
_crtBreakAlloc = 18;  
```  
  
 ou:  
  
```  
_CrtSetBreakAlloc(18);  
```  
  
## <a name="comparing-memory-states"></a>Comparando estados de memória  
 Outra técnica para localizar vazamentos de memória envolve pegar instantâneos do estado da memória do aplicativo em pontos-chave. Para obter um instantâneo do estado da memória em um determinado ponto no seu aplicativo, criar um **crtmemstate** estrutura e passá-lo para o `_CrtMemCheckpoint` função. Esta função preenche a estrutura com uma forma instantânea do estado de memória atual:  
  
```  
_CrtMemState s1;  
_CrtMemCheckpoint( &s1 );  
  
```  
  
 `_CrtMemCheckpoint` preencha a estrutura com uma forma instantânea do estado de memória atual.  
  
 Para gerar o conteúdo de um **crtmemstate** estrutura, transmitir a estrutura para o `_ CrtMemDumpStatistics` função:  
  
```  
_CrtMemDumpStatistics( &s1 );  
  
```  
  
 saída de`_ CrtMemDumpStatistics` resulta num despejo do estado de memória que parece com este:  
  
```  
0 bytes in 0 Free Blocks.  
0 bytes in 0 Normal Blocks.  
3071 bytes in 16 CRT Blocks.  
0 bytes in 0 Ignore Blocks.  
0 bytes in 0 Client Blocks.  
Largest number used: 3071 bytes.  
Total allocations: 3764 bytes.  
  
```  
  
 Para determinar se um vazamento de memória ocorreu em uma seção de código, você pode capturar instantâneos do estado da memória antes e após a seção e, em seguida, usar `_ CrtMemDifference` para comparar os dois estados:  
  
```  
_CrtMemCheckpoint( &s1 );  
// memory allocations take place here  
_CrtMemCheckpoint( &s2 );  
  
if ( _CrtMemDifference( &s3, &s1, &s2) )  
   _CrtMemDumpStatistics( &s3 );  
```  
  
 `_CrtMemDifference` compara os estados de memória `s1` e `s2` e retorna um resultado em (`s3`) que é a diferença de `s1` e de `s2`.  
  
 Uma técnica para localizar vazamentos de memória começa colocando chamadas de `_CrtMemCheckpoint` no início e fim do seu aplicativo, depois usando `_CrtMemDifference` para comparar os resultados. Se `_CrtMemDifference` mostra um vazamento de memória, você pode adicionar mais chamadas de `_CrtMemCheckpoint` para dividir seu programa usando uma busca binária até ter isolado a fonte do vazamento.  
  
## <a name="false-positives"></a>Falsos positivos  
 Em alguns casos, `_CrtDumpMemoryLeaks` poderá dar falsas indicações de vazamentos de memória. Isso pode ocorrer se você usar uma biblioteca que marca alocações internas como _NORMAL_BLOCKs em vez de `_CRT_BLOCK`s ou de `_CLIENT_BLOCK`s. Nesse caso, `_CrtDumpMemoryLeaks` não é capaz de reconhecer a diferença entre alocações de usuário e alocações internas de biblioteca. Se os destruidores globais das alocações de biblioteca forem executados após o ponto onde você chama `_CrtDumpMemoryLeaks`, cada alocação interna da biblioteca será relatada como um vazamento de memória. As versões anteriores de biblioteca padrão do modelo, anteriores do Visual Studio .NET, causaram `_CrtDumpMemoryLeaks` para relatar falsos positivos, mas este foram corrigidos em versões recentes.  
  
## <a name="see-also"></a>Consulte também  
 [Detalhes de Heap de depuração CRT](../debugger/crt-debug-heap-details.md)   
 [Segurança do depurador](../debugger/debugger-security.md)   
 [Depurando código nativo](../debugger/debugging-native-code.md)
