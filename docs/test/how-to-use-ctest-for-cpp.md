---
title: Como usar o CTest para C++ no Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 11/07/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
author: mikeblome
ms.openlocfilehash: 989f2b06df55fd0927863fe7e5603d3d0ec90b06
ms.sourcegitcommit: 7ae502c5767a34dc35e760ff02032f4902c7c02b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/09/2018
---
# <a name="how-to-use-ctest-for-c-in-visual-studio"></a>Como usar o CTest para C++ no Visual Studio
O CMake (que inclui o CTest) está integrado ao IDE do Visual Studio como um componente da carga de trabalho **Desenvolvimento de Área de Trabalho com C++**. Para instalá-lo no seu computador, abra o Instalador do Visual Studio e localize as [Ferramentas CMake para Visual C++](/cpp/ide/cmake-tools-for-visual-cpp) na lista de componentes de carga de trabalho.

O suporte de CMake no Visual Studio não envolve o sistema de projeto do Visual Studio. Portanto, você grava e configura testes CTest exatamente como faria em qualquer ambiente CMake. Consulte [Ferramentas CMake para Visual C++](/cpp/ide/cmake-tools-for-visual-cpp) para saber mais sobre como usar o CMake no Visual Studio.

O CTest do **Visual Studio 2017 versão 15.5** não está integrado ao **Gerenciador de Testes** atualmente. É possível executar testes do menu principal do CMake ou do menu de contexto em um arquivo **CMakeLists.txt** no **Gerenciador de Soluções**. Os resultados de teste são direcionados para a **Janela de Saída** do Visual Studio.

![Executar testes de CTest](media/cpp-cmake-run-tests.png "Executar testes de CTest")


## <a name="see-also"></a>Consulte também
[Escrever Testes de Unidade para C/C++](writing-unit-tests-for-c-cpp.md)


  







