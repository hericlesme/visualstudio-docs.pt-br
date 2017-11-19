---
title: Definir o controle a ser criado quando arrastado da janela fontes de dados | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Data Sources Window, select controls
- Windows Forms, displaying data
- data [Visual Studio], displaying on Windows Forms
- data [Visual Studio], Data Sources window
ms.assetid: 20597ff8-0c98-43ec-8fb1-05376804ba48
caps.latest.revision: "31"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: 12b8c166873802e3c0e6a8d4e73ff1b686229222
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/09/2017
---
# <a name="set-the-control-to-be-created-when-dragging-from-the-data-sources-window"></a>Definir o controle a ser criado quando arrastado da janela fontes de dados
Você pode criar controles associados a dados, arrastando itens a partir de **fontes de dados** janela para o designer do WPF ou o designer de formulários do Windows. Cada item de **fontes de dados** janela possui um controle padrão que é criado quando você arrastá-la para o designer. No entanto, você pode escolher criar um controle diferente.  
  
## <a name="set-the-controls-to-be-created-for-data-tables-or-objects"></a>Definir os controles a ser criada para tabelas de dados ou objetos  
Antes de você arrasta os itens que representam as tabelas de dados ou objetos do **fontes de dados** janela, você pode escolher para exibir todos os dados em um controle, ou para exibir cada coluna ou propriedade em um controle separado.  
  
Nesse contexto, o termo *objeto* se refere a um objeto comercial personalizado, uma entidade (em um modelo de dados de entidade) ou um objeto retornado por um serviço.  
  
### <a name="to-set-the-controls-to-be-created-for-data-tables-or-objects"></a>Para definir os controles a serem criados para tabelas de dados ou objetos  
  
1.  Certifique-se de que o designer do WPF ou o designer de formulários do Windows está aberto.  
  
2.  No **fontes de dados** janela, selecione o item que representa a tabela de dados ou objeto que você deseja definir.  
  
3.  Clique no menu suspenso para o item e, em seguida, clique em um dos seguintes itens no menu:  
  
    -   Para exibir cada campo de dados em um controle separado, clique em **detalhes**. Quando você arrastar o item de dados para o designer, essa ação criará um controle associado a dados diferente para cada coluna ou propriedade do objeto, junto com os rótulos para cada controle ou tabela de dados pai.  
  
    -   Para exibir todos os dados em um único controle, selecione um controle diferente na lista, como **DataGrid** ou **lista** em um aplicativo WPF, ou **DataGridView** em um Windows Forms aplicativo.  
  
    A lista de controles disponíveis depende de qual Designer você abriu, qual versão do .NET Framework seus destinos do projeto e se você adicionou personalizado controla que suporte a vinculação de dados para o **caixa de ferramentas**. Se o controle que você deseja criar não está na lista de controles disponíveis, você pode adicionar o controle à lista. Para obter mais informações, consulte [adicionar controles personalizados à janela fontes de dados](../data-tools/add-custom-controls-to-the-data-sources-window.md).  
  
    Para saber como criar um controle personalizado do Windows Forms que pode ser adicionado à lista de controles para tabelas de dados ou objetos no **fontes de dados** janela, consulte [criar um controle de usuário do Windows Forms que dá suporte a dados complexos associação](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md).  
  
## <a name="set-the-controls-to-be-created-for-data-columns-or-properties"></a>Definir os controles a serem criados para colunas de dados ou propriedades  
Antes de você arrasta um item que representa uma coluna ou uma propriedade de um objeto a partir de **fontes de dados** janela para o designer, você pode definir o controle a ser criado.  
  
#### <a name="to-set-the-controls-to-be-created-for-columns-or-properties"></a>Para definir os controles a serem criados para colunas ou propriedades  
  
1.  Certifique-se de que o designer do WPF ou o designer de formulários do Windows está aberto.  
  
2.  No **fontes de dados** janela, expanda a tabela desejada, ou para exibir suas colunas ou propriedades do objeto.  
  
3.  Selecione cada coluna ou propriedade para o qual você deseja definir o controle a ser criado.  
  
4.  Clique no menu suspenso para a coluna ou propriedade e, em seguida, selecione o controle que você deseja criar quando o item é arrastado para o designer.  
  
     A lista de controles disponíveis depende de qual Designer você abriu, qual versão do .NET Framework seus destinos do projeto e controles de quais personalizados que oferecem suporte a dados que você adicionou ao **caixa de ferramentas**. Se o controle que você deseja criar está na lista de controles disponíveis, você pode adicionar o controle à lista. Para obter mais informações, consulte [adicionar controles personalizados à janela fontes de dados](../data-tools/add-custom-controls-to-the-data-sources-window.md).  
  
     Para aprender a criar um controle personalizado que pode ser adicionado à lista de controles para colunas de dados ou propriedades de **fontes de dados** janela, consulte [criar um controle de usuário do Windows Forms que dá suporte à associação de dados simples](../data-tools/create-a-windows-forms-user-control-that-supports-simple-data-binding.md).  
  
     Se você não quiser criar um controle para a coluna ou propriedade, selecione **nenhum** no menu suspenso. Isso é útil se você deseja arrastar a tabela pai ou o objeto para o designer, mas você não deseja incluir a propriedade ou coluna específica.  
  
## <a name="see-also"></a>Consulte também
[Associar controles a dados no Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)