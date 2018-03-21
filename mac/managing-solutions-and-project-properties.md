---
title: "Gerenciando propriedades de solução e projeto | Microsoft Docs"
author: asb3993
ms.author: amburns
ms.date: 04/14/2017
ms.topic: article
ms.assetid: 75247EB8-323A-4AFD-A451-6703A03D5D1F
ms.openlocfilehash: eac94a70cdfac556fce6e04188ab24c5102eab25
ms.sourcegitcommit: 39c525ec200c6c4ea94815567b3fad7ab14fb7b3
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/08/2018
---
# <a name="managing-project-and-solution-properties"></a>Gerenciando propriedades de solução e projeto

## <a name="project-options"></a>Opções do projeto

As opções de projeto são específicas para cada projeto e afetam como ele é escrito, criado e executado. Isso contrasta com as Preferências do Visual Studio para Mac (que definem opções específicas do usuário) e as Opções da solução (que definem as opções para toda a solução). As opções do projeto são armazenadas no arquivo de projeto (.csproj), para que outros desenvolvedores possam compilar e executar o projeto corretamente. Ter opções de projeto específicas permite que vários desenvolvedores trabalhem no mesmo documento sem comprometer a formatação do arquivo.

Para abrir as opções do projeto no Visual Studio para Mac, clique duas vezes no nome do projeto ou clique com o botão direito do mouse para abrir o menu de contexto e selecione **Opções**:

 ![Opção no menu de contexto](media/projects-and-solutions-image2.png)

As opções editáveis incluem opções para compilar, executar e definir o código-fonte e o controle de versão.

As opções do projeto são organizadas em cinco categorias diferentes:

* **Geral** – as informações do projeto como Nome, Descrição e Namespace Padrão são definidas aqui, bem como o Local do projeto.
* **Build** – Permite aos desenvolvedores definir ou alterar perfis PCL para Bibliotecas de Classes Portáteis. Ele também permite definir comandos, configurações e opções do compilador personalizados. O caminho de saída e o nome de assembly também pode ser definidos aqui.
* **Executar** – Permite criar configurações de execução personalizadas por projeto.
* **Código-fonte** – Permite controlar a formatação de vários tipos de arquivos e convenções de nomenclatura diferentes. Você também pode definir as políticas de nomenclatura e os estilos de cabeçalho padrão aqui.
* **Controle de Versão** – Permite editar o estilo da mensagem de confirmação ao usar o Controle de Versão com o seu projeto.

Cada projeto pode conter as opções específicas do projeto, dependendo da plataforma. Por exemplo, um projeto Xamarin.Android, como o ilustrado na imagem a seguir, tem opções relacionadas ao build do Android, como opções de vinculador, e ao aplicativo, como essas permissões:

 ![Opções do Projeto Android](media/projects-and-solutions-image5.png)

O Xamarin.iOS tem opções relacionadas à assinatura do pacote, tais como o perfil de provisionamento necessário a ser usado:

 ![Opções do Projeto iOS](media/projects-and-solutions-image6.png)

## <a name="solution-options"></a>Opções da Solução 

As opções da solução são como as Opções do projeto, mas abrangem todas as Soluções em seu escopo. Elas fornecem uma maneira de definir informações de criador, configurações de build, estilos de formatação de código e controle de versão, e proporcionam uma maneira de atribuir o projeto de inicialização na Solução.  A caixa de diálogo Opções da Solução pode ser acessada no item de menu **Projeto > Opções de Solução**, no item de menu de contexto **Opções** na Solução no Painel de soluções ou clicando duas vezes na Solução no Painel de Soluções:

 ![Opções da Solução](media/projects-and-solutions-image7.png)
