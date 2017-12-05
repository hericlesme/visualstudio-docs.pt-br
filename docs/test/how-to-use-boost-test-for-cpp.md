---
title: Como usar o Boost.Test para C++ no Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 11/07/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2e0710a8-8e8a-4f6e-8415-5ab3eb830079
caps.latest.revision: "14"
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 6bfce4aa4153d8f01fa9ef6cd6dc0d4b08eedbc4
ms.sourcegitcommit: fb751e41929f031d1a9247bc7c8727312539ad35
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/15/2017
---
# <a name="how-to-use-boosttest-for-c-in-visual-studio"></a>Como usar o Boost.Test para C++ no Visual Studio
No **Visual Studio 2017 versão 15.5** ou posterior, o Boost.Test está integrado ao IDE do Visual Studio como um componente da carga de trabalho **Desenvolvimento de Área de Trabalho com C++**. Para instalá-lo no seu computador, abra o Instalador do Visual Studio e localize o **Adaptador do Boost.Test** na lista de componentes de carga de trabalho:

![Instalar o Boost Test](media/cpp-boost-component.png "Instalar Boost.Test para C++")

## <a name="install-boost"></a>Instalar o Boost

 O Boost.Test exige o [Boost](http://www.boost.org/)! Se o Boost não estiver instalado, recomendamos o uso do gerenciador de pacotes Vcpkg. 

1. Siga as instruções em [Vcpkg: gerenciador de pacotes de C++ para Windows](/cpp/vcpkg) para instalar o vcpkg (caso ainda não o tenha).
2. Execute `vcpkg install boost` para instalar as bibliotecas do Boost.
3. Execute o comando `vcpkg integrate install` para configurar o Visual Studio com a biblioteca e incluir caminhos para os cabeçalhos e binários do Boost. 

## <a name="create-a-project-for-your-tests"></a>Criar um projeto para seus testes
No Visual Studio 2017 versão 15.5, não há projeto de teste pré-configurado ou modelos de item disponíveis para o Boost.Test. Portanto, é necessário criar um projeto de aplicativo de console para manter seus testes. Os modelos de teste do Boost.Test são planejados para inclusão em uma futura versão do Visual Studio. 

1. No **Gerenciador de Soluções**, clique com o botão direito do mouse no nó da solução e escolha **Adicionar | Novo Projeto**. 
2. No painel à esquerda, escolha **Área de Trabalho do Windows** e, depois, **Aplicativo de Console do Windows** no painel central. 
3. Dê um nome ao projeto e clique em **OK**. 

## <a name="add-include-directives"></a>Adicionar diretivas de inclusão
No arquivo .cpp de teste, adicione quaisquer diretivas `#include` necessárias para que os tipos e as funções do programa sejam visíveis para o código de teste. Normalmente, o programa está um nível acima na hierarquia de pastas. Se você digitar `#include "../"`, uma janela do IntelliSense será exibida e permitirá que você selecione o caminho completo para o arquivo de cabeçalho.

![Adicionar diretivas de inclusão](media/cpp-gtest-includes.png "Adicionar diretivas de inclusão ao arquivo .cpp de teste")

No mínimo, é necessário incluir a [variante de cabeçalho único do Boost.Test](http://www.boost.org/doc/libs/1_48_0/libs/test/doc/html/utf/user-guide/usage-variants/single-header-variant.html) com `#include <path>/unit_test.hpp` e definir `BOOST_TEST_MODULE`. O exemplo a seguir é suficiente para que o teste seja detectável no **Gerenciador de Testes**:

```cpp
#include "stdafx.h"
#define BOOST_TEST_MODULE MyTest
#include <boost/test/included/unit_test.hpp>
#include "../MyProgram/MyClass.h" // project being tested
#include <string>

BOOST_AUTO_TEST_CASE(my_boost_test)
{
    std::string name = "Bill";
    MyClass mc(name);
    Assert::AreEqual();
    BOOST_CHECK(name == mc.GetName());
}
```

## <a name="write-and-run-tests"></a>Gravar e executar testes
Agora, você está pronto para gravar e executar testes no Boost.Test. Consulte a [documentação da Boost Test Library](http://www.boost.org/doc/libs/1_38_0/libs/test/doc/html/index.html) (Biblioteca do Boost Test) para saber mais sobre as macros de teste. Consulte [Executar testes de unidade com o Gerenciador de Testes](run-unit-tests-with-test-explorer.md) para saber mais sobre como descobrir, executar e agrupar testes usando o **Gerenciador de Testes**.

## <a name="see-also"></a>Consulte também
[Escrever Testes de Unidade para C/C++](writing-unit-tests-for-c-cpp.md)


  







