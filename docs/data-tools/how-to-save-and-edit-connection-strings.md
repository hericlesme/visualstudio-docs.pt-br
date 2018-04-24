---
title: Como salvar e editar cadeias de conexão
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: f8ef3a2c-029c-423b-9d9e-a4f1add4f640
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 820808a79c8ed18c08c6c54ba416c0993aac06d5
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/19/2018
---
# <a name="how-to-save-and-edit-connection-strings"></a>Como salvar e editar cadeias de conexão
Cadeias de caracteres de Conexão em aplicativos do Visual Studio podem ser salvo no arquivo de configuração do aplicativo (também chamado de configurações do aplicativo), ou embutidos diretamente em seu aplicativo. Salvar cadeias de conexão no arquivo de configuração do aplicativo simplifica a tarefa de realizar a manutenção de seu aplicativo. Se a cadeia de conexão precisar ser alterada, você poderá atualizá-la no arquivo de configurações do aplicativo (em vez de alterá-la no código-fonte e recompilar o aplicativo).

O armazenamento das informações confidenciais (tal como a senha) dentro da cadeia de conexão pode afetar a segurança do aplicativo. Cadeias de conexão salvas no arquivo de configuração do aplicativo não são criptografadas nem ofuscadas, de modo que talvez seja possível que alguém acesse o arquivo e exiba seu conteúdo. O uso da segurança integrada do Windows é uma maneira mais segura de controlar o acesso a um banco de dados.

Se você optar por não usar a segurança integrada do Windows e seu banco de dados exigir um nome de usuário e uma senha, você poderá omiti-los da cadeia de conexão, mas seu aplicativo precisará fornecer essas informações para se conectar com êxito ao banco de dados. Por exemplo, você pode criar uma caixa de diálogo que solicita ao usuário essas informações e compila dinamicamente a cadeia de conexão no tempo de execução. A segurança ainda pode ser um problema se as informações forem interceptadas no caminho para o banco de dados.
Para obter mais informações, consulte [Protegendo informações de conexão](/dotnet/framework/data/adonet/protecting-connection-information).

## <a name="to-save-a-connection-string-from-within-the-data-source-configuration-wizard"></a>Para salvar uma cadeia de caracteres de conexão de dentro do Assistente de configuração de fonte de dados
No **Assistente de configuração de fonte de dados**, selecione a opção para salvar a conexão na cadeia de salvar a Conexão caracteres para a página do arquivo de configuração do aplicativo.

## <a name="to-save-a-connection-string-directly-into-application-settings"></a>Para salvar uma cadeia de conexão diretamente nas configurações do aplicativo
- No Solution Explorer, clique duas vezes no ícone do meu projeto (Visual Basic) ou no ícone de propriedades (c#) para abrir o Designer de projeto.
- Selecione a guia Configurações.
- Insira um nome para a cadeia de caracteres de conexão. Consulte esse nome ao acessar a cadeia de conexão no código.
- Defina o tipo para (cadeia de caracteres de Conexão).
- Deixe o escopo definido para o aplicativo.
- Digite a cadeia de conexão para o campo de valor ou clique no botão de reticências (...) no campo de valor para abrir a caixa de diálogo Propriedades de Conexão para criar a cadeia de conexão.

## <a name="editing-connection-strings-stored-in-application-settings"></a>Editando cadeias de conexão armazenadas nas configurações do aplicativo
Você pode modificar as informações de conexão que são salvas nas configurações do aplicativo usando o Designer de projeto.

### <a name="to-edit-a-connection-string-stored-in-application-settings"></a>Para editar uma cadeia de conexão nas configurações do aplicativo
- No Solution Explorer, clique duas vezes no ícone do meu projeto (Visual Basic) ou no ícone de propriedades (c#) para abrir o Designer de projeto.
- Selecione a guia Configurações.
- Localize a conexão que você deseja editar e selecione o texto no campo de valor.
- Edite a cadeia de conexão no campo de valor ou clique no botão de reticências (...) no campo de valor para editar a conexão com a caixa de diálogo Propriedades de Conexão.

## <a name="editing-connection-strings-for-datasets"></a>Edição de cadeias de caracteres de conexão para conjuntos de dados
Você pode modificar as informações de conexão para cada TableAdapter em um conjunto de dados.

### <a name="to-edit-a-connection-string-for-a-tableadapter-in-a-dataset"></a>Para editar uma cadeia de caracteres de conexão para um TableAdapter em um conjunto de dados
- No Solution Explorer, clique duas vezes o conjunto de dados (arquivo. xsd) com a conexão que você deseja editar.
- Selecione o TableAdapter ou a consulta com a conexão que você deseja editar.
- Na janela Propriedades, expanda o nó de Conexão.
- Para modificar rapidamente a cadeia de caracteres de conexão, edite a propriedade ConnectionString, ou clique na seta para baixo na propriedade de Conexão e escolha Nova Conexão.

## <a name="security"></a>Segurança
O armazenamento das informações confidenciais (tal como uma senha) dentro da cadeia de conexão pode afetar a segurança do aplicativo. O uso da segurança integrada do Windows é uma maneira mais segura de controlar o acesso a um banco de dados.
Para obter mais informações, consulte [Protegendo informações de conexão](/dotnet/framework/data/adonet/protecting-connection-information).

## <a name="see-also"></a>Consulte também

- [Adicionando conexões](../data-tools/add-new-connections.md)