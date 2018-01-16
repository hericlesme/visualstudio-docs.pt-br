---
title: Como usar o Boost.Test para C++ no Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 01/05/2018
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: bdf772be03f6021f499b9bf777922d6d2743e0dc
ms.sourcegitcommit: 7ae502c5767a34dc35e760ff02032f4902c7c02b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/09/2018
---
# <a name="how-to-use-boosttest-for-c-in-visual-studio"></a>Como usar o Boost.Test para C++ no Visual Studio

No **Visual Studio 2017 versão 15.5** e posterior, o adaptador de teste Boost.Test está integrado ao IDE do Visual Studio como um componente da carga de trabalho **Desenvolvimento para desktop com C++**.

![Adaptador de teste para Boost.Test](media/cpp-boost-component.png "Adaptador de teste para o componente Boost.Test")

Se a carga de trabalho **Desenvolvimento para desktop com C++** não estiver instalada, abra o **Instalador do Visual Studio** e selecione **Modificar**. Selecione a carga de trabalho **Desenvolvimento para desktop com C++** e escolha o botão **Modificar**.

## <a name="install-boost"></a>Instalar o Boost

O Boost.Test exige o [Boost](http://www.boost.org/)! Se o Boost não estiver instalado, recomendamos o uso do gerenciador de pacotes Vcpkg.

1. Siga as instruções em [Vcpkg: gerenciador de pacotes de C++ para Windows](/cpp/vcpkg) para instalar o vcpkg (caso ainda não o tenha).

1. Instale a biblioteca Boost.Test dinâmica ou estática:

    - Execute `vcpkg install boost-test` para instalar a biblioteca Boost.Test dinâmica.
    
       -OU-
       
    - Execute `vcpkg install boost-test:x86-windows-static` para instalar a biblioteca Boost.Test estática.

1. Execute `vcpkg integrate install` para configurar o Visual Studio com a biblioteca e incluir caminhos para os cabeçalhos e os binários do Boost.

## <a name="create-a-project-for-your-tests"></a>Criar um projeto para seus testes

> [!NOTE]
> No Visual Studio 2017 versão 15.5, não há nenhum modelo de projeto de teste ou de item pré-configurado disponível para o Boost.Test. Portanto, é necessário criar um projeto de aplicativo de console para manter seus testes. Os modelos de teste do Boost.Test são planejados para inclusão em uma futura versão do Visual Studio.

1. No **Gerenciador de Soluções**, clique com o botão direito do mouse no nó da solução e escolha **Adicionar** > **Novo Projeto...**.

1. No painel esquerdo, escolha **Visual C++** > **Windows Desktop** e, em seguida, selecione o modelo **Aplicativo de Console do Windows**.

1. Nomeie o projeto e escolha **OK**.

## <a name="link-and-configuration-boost-static-library-only"></a>Link e configuração (somente a biblioteca Boost estática)

Configure o projeto para executar testes do Boost.Test.

1. Para editar o arquivo de projeto, primeiro descarregue-o. No **Gerenciador de Soluções**, clique com o botão direito do mouse no nó do projeto e escolha **Descarregar Projeto**. Em seguida, clique com o botão direito do mouse no nó do projeto e escolha **Editar <name\>.vcxproj**.

1. Adicione duas linhas no grupo de propriedades **Globais**, como é mostrado aqui:

    ```xml
    <PropertyGroup Label="Globals">
    ....
        <VcpkgTriplet>x86-windows-static</VcpkgTriplet>
        <VcpkgEnabled>true</VcpkgEnabled>
    </PropertyGroup>
    ```
1. Salve e feche o arquivo \*.vcxproj e, em seguida, recarregue o projeto.

1. Para abrir a **Páginas de Propriedades**, clique com o botão direito do mouse no nó do projeto e escolha **Propriedades**.

1. Expanda **C/C++** > **Geração de Código** e, em seguida, selecione **Biblioteca em Tempo de Execução**. Selecione `/MTd` para a biblioteca em tempo de execução estática de depuração ou `/MT` para a biblioteca em tempo de execução estática de liberação.

1. Expanda **Vinculador > Sistema**. Verifique se **Subsistema** está definido como **Console**.

1. Escolha **OK** para fechar as páginas de propriedades.

## <a name="add-include-directives"></a>Adicionar diretivas de inclusão

1. Se houver uma função `main` no seu arquivo .cpp de teste, exclua-a.

1. No arquivo .cpp de teste, adicione quaisquer diretivas `#include` necessárias para que os tipos e as funções do programa sejam visíveis para o código de teste. Normalmente, o programa está um nível acima na hierarquia de pastas. Se você digitar `#include "../"`, uma janela do IntelliSense será exibida e permitirá que você selecione o caminho completo para o arquivo de cabeçalho.

   ![Adicionar diretivas de inclusão](media/cpp-gtest-includes.png "Adicionar diretivas de inclusão ao arquivo .cpp de teste")

   Você pode usar a biblioteca autônoma com:

   ```cpp
   #include <boost/test/unit_test.hpp>
   ```

   Ou, use a versão de cabeçalho único com:

   ```cpp
   #include <boost/test/included/unit_test.hpp>
   ```

   Em seguida, defina `BOOST_TEST_MODULE`.

O exemplo a seguir é suficiente para que o teste seja detectável no **Gerenciador de Testes**:

```cpp
#define BOOST_TEST_MODULE MyTest
#include <boost/test/included/unit_test.hpp\> //single-header
#include "../MyProgram/MyClass.h" // project being tested
#include <string>

BOOST_AUTO_TEST_CASE(my\_boost_test)
{
    std::string expected_value = "Bill";

    // assume MyClass is defined in MyClass.h
    // and get_value() has public accessibility
    MyClass mc;
    BOOST_CHECK(expected_value == mc.get_value());
}
```

## <a name="write-and-run-tests"></a>Gravar e executar testes
Agora, você está pronto para gravar e executar testes no Boost.Test. Consulte a [documentação da Boost Test Library](http://www.boost.org/doc/libs/1_38_0/libs/test/doc/html/index.html) (Biblioteca do Boost Test) para saber mais sobre as macros de teste. Consulte [Executar testes de unidade com o Gerenciador de Testes](run-unit-tests-with-test-explorer.md) para saber mais sobre como descobrir, executar e agrupar testes usando o **Gerenciador de Testes**.

## <a name="see-also"></a>Consulte também
[Escrever Testes de Unidade para C/C++](writing-unit-tests-for-c-cpp.md)
