---
title: Como usar o CTest para C++ no Visual Studio
ms.date: 11/07/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
ms.author: mblome
manager: douge
ms.workload:
- cplusplus
author: mikeblome
ms.openlocfilehash: 98e258c2547bbd3cd1b87d289bf643956acfdb1d
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34751027"
---
# <a name="how-to-use-ctest-for-c-in-visual-studio"></a>Como usar o CTest para C++ no Visual Studio

O CMake (que inclui o CTest) está integrado por padrão ao IDE do Visual Studio como um componente da carga de trabalho **Desenvolvimento de Área de Trabalho com C++**. Se você precisar instalá-lo em seu computador, abra o programa Instalador do Visual Studio, clique no botão **Modificar** e marque [Ferramentas CMake para Visual C++](/cpp/ide/cmake-tools-for-visual-cpp) na lista de componentes de carga de trabalho.

## <a name="to-write-tests"></a>Para escrever testes

O suporte de CMake no Visual Studio não envolve o sistema de projetos do Visual Studio. Portanto, você grava e configura testes CTest exatamente como faria em qualquer ambiente CMake. Para saber mais sobre o uso de CMake no Visual Studi, confira [Ferramentas CMake para Visual C++](/cpp/ide/cmake-tools-for-visual-cpp).

## <a name="to-run-tests-visual-studio-2017-version-156"></a>Para executar testes (Visual Studio 2017 versão 15.6)

No Visual Studio 2017 versão 15.6, o CTest é totalmente integrado ao **Gerenciador de Testes** e também oferece suporte a estruturas de teste de unidade do Google e Boost. Essas estruturas são incluídas por padrão como componentes na carga de trabalho **Desenvolvimento de área de trabalho com C++**. No entanto, se você estiver atualizando um projeto de uma versão anterior do Visual Studio, talvez seja necessário instalar essas estruturas usando o programa Instalador do Visual Studio.

A ilustração a seguir mostra os resultados de uma execução de CTest usando a estrutura do Google Test:

![CTest com a Estrutura do Google Test no VS2017 15.6](media/ctest-test-explorer.png)

Se você estiver usando CTest, mas não os adaptadores do Google ou Boost, verá resultados no nível de CTest em vez do nível de método de teste individual. Você pode depurar e percorrer executáveis apenas de CTest, mas os rastreamentos de pilha em testes individuais não têm suporte.

## <a name="to-run-tests-visual-studio-2017-version-155"></a>Para executar testes (Visual Studio 2017 versão 15.5)

No **Visual Studio 2017 versão 15.5**, o CTest não está integrado ao **Gerenciador de Testes**. É possível executar testes do menu principal do CMake ou do menu de contexto em um arquivo **CMakeLists.txt** no **Gerenciador de Soluções**. Os resultados de teste são direcionados para a **Janela de Saída** do Visual Studio.

![Executar testes de CTest no VS2017 15.5](media/cpp-cmake-run-tests.png)

## <a name="see-also"></a>Consulte também

[Escrever Testes de Unidade para C/C++](writing-unit-tests-for-c-cpp.md)