---
title: "Gerenciando propriedades de solução e projeto | Microsoft Docs"
author: asb3993
ms.author: amburns
ms.date: 04/14/2017
ms.topic: article
ms.assetid: 75247EB8-323A-4AFD-A451-6703A03D5D1F
ms.openlocfilehash: 8871ab002a94a9c0bbc0063a25b4dea9cb271142
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="managing-project-and-solution-properties"></a>Gerenciando propriedades de solução e projeto

## <a name="project-options"></a>Opções do projeto

As opções de projeto são específicas para cada projeto e afetam como ele é escrito, criado e executado. Isso contrasta com as Preferências do Visual Studio para Mac, que definem opções específicas do usuário, e com as Opções da solução, que definem as opções para toda a solução. As opções do projeto são armazenadas no arquivo de projeto (.csproj), para que outros desenvolvedores possam compilar e executar o projeto corretamente. Isso permite que vários desenvolvedores trabalhem no mesmo documento sem comprometer a formatação do arquivo.

As opções do projeto no Visual Studio para Mac podem ser iniciadas clicando duas vezes no nome do projeto ou clicando com o botão direito do mouse para abrir o menu de contexto e selecionando **Opções**:

 ![Opção no menu de contexto](media/projects-and-solutions-image2.png)

As opções editáveis incluem aquelas para compilar, executar e definir o código-fonte e o controle de versão.

As opções do projeto são organizadas em cinco categorias diferentes que têm os seguintes recursos:

* **Geral** – Informações do projeto como Nome, Descrição e Namespace Padrão podem ser definidas aqui, bem como o Local do projeto.
* **Build** – Permite aos desenvolvedores definir ou alterar perfis PCL para Bibliotecas de Classes Portáteis. Ele também permite definir comandos, configurações e opções do compilador personalizados. O caminho de saída e o nome de assembly também pode ser definidos aqui.
* **Executar** – Permite criar configurações de execução personalizadas por projeto.
* **Código-fonte** – Permite controlar a formatação de vários tipos de arquivos e convenções de nomenclatura diferentes. Você também pode definir as políticas de nomenclatura e os estilos de cabeçalho padrão aqui.
* **Controle de Versão** – Permite editar o estilo da mensagem de confirmação ao usar o Controle de Versão com o seu projeto.

Cada projeto pode conter também as opções específicas do projeto, dependendo da plataforma. Por exemplo, um projeto Xamarin.Android, como o ilustrado abaixo, terá opções relacionadas ao build do Android, como opções de vinculador, e ao aplicativo, como essas permissões:

 ![Opções do Projeto Android](media/projects-and-solutions-image5.png)

O Xamarin.iOS conterá opções relacionadas à assinatura do pacote, tais como o perfil de provisionamento necessário a ser usado e às opções de empacotamento IPA:

 ![Opções do Projeto iOS](media/projects-and-solutions-image6.png)

## <a name="solution-options"></a>Opções da Solução 

As opções da solução são como as Opções do projeto, mas abrangem todas as Soluções em seu escopo. Elas fornecem uma maneira de definir informações de criador, configurações de build, estilos de formatação de código e controle de versão, e proporcionam uma maneira de atribuir o projeto de inicialização na Solução.  A caixa de diálogo Opções da Solução pode ser acessada no item de menu **Projeto > Opções de Solução**, no item de menu de contexto **Opções** na Solução no Painel de soluções ou clicando duas vezes na Solução no Painel de Soluções:

 ![Opções da Solução](media/projects-and-solutions-image7.png)
