---
title: Como usar o Google Test para C++ no Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 11/04/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a4868fae-fd6d-4b98-a85f-f23b0dd2fca5
caps.latest.revision: "14"
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 7655c8690c48657c9efab967851ceff43c253135
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-google-test-for-c-in-visual-studio"></a>Como usar o Google Test para C++ no Visual Studio
No **Visual Studio 2017 versão 15.5** ou posterior, o Google Test está integrado ao IDE do Visual Studio como componente padrão da carga de trabalho **Desenvolvimento de Área de Trabalho com C++**. Para verificar se ele está instalado no seu computador, abra o Instalador do Visual Studio e localize o Google Test na lista de componentes de carga de trabalho:

![Instalar o Google Test](media/cpp-google-component.png "Instalar o Google Test para C++")

## <a name="add-a-google-test-project-to-the-solution"></a>Adicionar um projeto do Google Test à solução
1. No **Gerenciador de Soluções**, clique com o botão direito do mouse no nó da solução e escolha **Adicionar | Novo Projeto**. 
2. No painel à esquerda, clique em **Teste, no nó Visual C++** e escolha **Projeto do Google Test** no painel central. 
3. Dê um nome ao projeto de teste e clique em **OK**. 

![Novo projeto do Google Test](media/cpp-gtest-new-project.png "Adicionar um novo projeto do Google Test")

## <a name="configure-the-test-project"></a>Configurar o projeto de teste
Na caixa de diálogo **Configuração do Projeto de Teste** exibida, escolha o projeto que deseja testar. Ao escolher um projeto, o Visual Studio adiciona uma referência ao projeto selecionado. Se nenhum projeto for escolhido, então, será necessário adicionar as referências manualmente ao(s) projeto(s) que você deseja testar. Ao escolher entre a vinculação estática e dinâmica para os binários do Google Test, as considerações são as mesmas de qualquer programa do C++. Para saber mais, consulte [DLLs no Visual C++](/cpp/build/dlls-in-visual-cpp). 

 ![Configurar o projeto do Google Test](media/cpp-gtest-config.png "Configurar o projeto do Google Test")

## <a name="set-additional-options"></a>Definir opções adicionais
No menu principal, escolha **Ferramentas | Opções | Adaptador de Teste para Google Test** para definir opções adicionais. Consulte a documentação do Google Test para saber mais sobre essas configurações.

 ![Configurações de projeto do Google Test](media/cpp-gtest-settings.png "Configurações de projeto do Google Test")

## <a name="add-include-directives"></a>Adicionar diretivas de inclusão
No arquivo .cpp de teste, adicione quaisquer diretivas `#include` necessárias para que os tipos e as funções do programa sejam visíveis para o código de teste. Normalmente, o programa está um nível acima na hierarquia de pastas. Se você digitar `#include "../"`, uma janela do IntelliSense será exibida e permitirá que você selecione o caminho completo para o arquivo de cabeçalho.

![Adicionar diretivas de inclusão](media/cpp-gtest-includes.png "Adicionar diretivas de inclusão ao arquivo .cpp de teste")

## <a name="write-and-run-tests"></a>Gravar e executar testes
Agora, você está pronto para gravar e executar testes no Google Test. Consulte o [Google Test Primer](https://github.com/google/googletest/blob/master/googletest/docs/Primer.md) (Primer do Google Test) para saber mais sobre as macros de teste. Consulte [Executar testes de unidade com o Gerenciador de Testes](run-unit-tests-with-test-explorer.md) para saber mais sobre como descobrir, executar e agrupar testes usando o **Gerenciador de Testes**.

## <a name="see-also"></a>Consulte também
[Escrever Testes de Unidade para C/C++](writing-unit-tests-for-c-cpp.md)


  







