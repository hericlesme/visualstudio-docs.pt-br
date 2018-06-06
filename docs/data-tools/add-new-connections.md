---
title: Adicionar novas conexões
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: a7b580f8bd04c4fbce9518d903a568bbd0f9175a
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34747086"
---
# <a name="add-new-connections"></a>Adicionar novas conexões

Você pode testar sua conexão a um banco de dados ou serviço e explorar o conteúdo do banco de dados e esquemas usando **Server Explorer**, **Cloud Explorer**, ou **Pesquisador de objetos do SQL Server**. A funcionalidade dessas janelas sobrepõe até certo ponto. As diferenças básicas são:

- conexões de servidor

   Instalado por padrão no Visual Studio. Pode ser usado para testar as conexões e exibir bancos de dados do SQL Server, outros bancos de dados que têm um provedor ADO.NET instalados e alguns serviços do Azure. Também mostra objetos de baixo nível, como contadores de desempenho do sistema, logs de eventos e filas de mensagens. Se uma fonte de dados não tiver nenhum provedor ADO.NET, ele não aparecer aqui, mas você ainda poderá ser usada no Visual Studio ao se conectar por meio de programação.

- Cloud Explorer

   Instale essa janela manualmente como uma extensão do Visual Studio selecionando **ferramentas**, **extensões e atualizações**, **Online**, **MarkeplacedeVisualStudio**. Fornece funcionalidades especializadas para explorar e conectar-se aos serviços do Azure.

- Pesquisador de Objetos do SQL Server

   Instalado com o SQL Server Data Tools e visível sob o **exibição** menu. Se você não vê-lo lá, vá para **programas e recursos** no painel de controle, encontre o Visual Studio e, em seguida, selecione **alteração** para executar o instalador novamente depois de selecionar a caixa de seleção para SQL Server Data Tools. Use **Pesquisador de objetos do SQL Server** para exibir bancos de dados SQL (se eles têm um provedor ADO.NET), criar novos bancos de dados, modificar esquemas, criar procedimentos armazenados, recuperar cadeias de caracteres de conexão, exibir os dados e muito mais. Bancos de dados SQL não tem nenhum provedor ADO.NET instalado não serão mostradas aqui, mas você ainda pode se conectar a eles por meio de programação.

## <a name="add-a-connection-in-server-explorer"></a>Adicionar uma conexão no Gerenciador de servidores

Para criar uma conexão ao banco de dados, clique o **Adicionar Conexão** ícone no **Gerenciador de servidores**, ou com o botão direito em **Server Explorer** no **dados Conexões** nó e selecione **Adicionar Conexão**. A partir daqui, você também pode se conectar a um banco de dados em outro servidor, um serviço do SharePoint ou um serviço do Azure.

![Ícone de Conexão de novo Gerenciador do servidor](../data-tools/media/raddata-server-explorer-new-connection-icon.png)

Isso abre o **Adicionar Conexão** caixa de diálogo. Aqui, podemos digitou o nome da instância LocalDB do SQL Server.

![Adicionar nova Conexão](../data-tools/media/raddata-add-new-connection-dialog.png)

## <a name="change-the-provider"></a>Alterar o provedor

Se a fonte de dados não é o desejado, clique no **alteração** botão para escolher uma nova fonte de dados e/ou em um novo provedor de dados do ADO.NET. O novo provedor pode solicitar suas credenciais, dependendo de como você configurou.

![Provedor de dados AD0.NET de alteração](../data-tools/media/raddata-change-ad0.net-data-provider.png)

## <a name="test-the-connection"></a>Testar a conexão

Depois de escolher a fonte de dados, clique em **Conexão de teste**. Se não for bem-sucedida, você precisará solucionar problemas com base na documentação do fornecedor.

![Conexão de teste](../data-tools/media/raddata-test-connection.png)

Se o teste for bem-sucedido, você estará pronto para criar um *fonte de dados*, que é um termo do Visual Studio que realmente significa um *modelo de dados* que se baseia no banco de dados subjacente ou do serviço.

## <a name="see-also"></a>Consulte também

- [Ferramentas de dados do Visual Studio para .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)