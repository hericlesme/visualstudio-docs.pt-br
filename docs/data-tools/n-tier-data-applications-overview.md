---
title: "Visão geral de aplicativos de dados de N camadas | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- presentation tier
- middle tier
- data tier
- n-tier applications, about n-tier applications
ms.assetid: 1020581d-eaaa-41a2-aca4-bf4c212895f6
caps.latest.revision: "26"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: 3949d49f763c2513e86c2cd3f1b20c20fb858ecc
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/09/2017
---
# <a name="n-tier-data-applications-overview"></a>Visão geral de aplicativos de dados de N camadas
*N-camadas* aplicativos de dados são aplicativos de dados que são separados em várias *camadas*. Também chamado de "aplicativos distribuídos" e "aplicativos multicamadas", aplicativos de n camadas separam o processamento em camadas discretas que são distribuídas entre o cliente e o servidor. Ao desenvolver aplicativos que acessam dados, você deve ter uma separação clara entre as várias camadas que constituem o aplicativo.  
  
Um aplicativo de n camadas típico inclui uma camada de apresentação, uma camada intermediária e uma camada de dados. A maneira mais fácil para separar as várias camadas em um aplicativo de n camadas é criar projetos distintos para cada camada que você deseja incluir em seu aplicativo. Por exemplo, a camada de apresentação pode ser um aplicativo do Windows Forms, enquanto a lógica de acesso a dados pode ser uma biblioteca de classes localizada na camada intermediária. Além disso, a camada de apresentação pode se comunicar com a lógica de acesso a dados na camada intermediária por meio de um serviço como um serviço. Dividir componentes do aplicativo em camadas separadas aumenta a facilidade de manutenção e a escalabilidade do aplicativo. Ele faz isso permitindo adoção mais fácil de novas tecnologias que podem ser aplicadas a uma única camada sem a necessidade de recriar a solução inteira. Além disso, aplicativos de n camadas normalmente armazenam informações sigilosas na camada intermediária, que mantém o isolamento da camada de apresentação.  
  
O Visual Studio contém vários recursos para ajudar os desenvolvedores a criar aplicativos de n camadas:  
  
-   O conjunto de dados fornece um **projeto DataSet** propriedade que permite que você separe o dataset (camada de entidade de dados) e TableAdapters (camada de acesso a dados) em projetos distintos.  
  
-   O [LINQ to SQL Tools no Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) fornece configurações para gerar as classes DataContext e dados em namespaces separados. Isso permite uma separação lógica do acesso a dados e camadas de entidade de dados.  
  
-   [O LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index) fornece o <xref:System.Data.Linq.Table%601.Attach%2A> método que permite reunir o DataContext de diferentes camadas em um aplicativo. Para obter mais informações, consulte [de N camadas e aplicativos remotos com o LINQ to SQL](http://msdn.microsoft.com/Library/854a1cdd-53cb-45f5-83ca-63962a9b3598).  
  
## <a name="presentation-tier"></a>Camada de apresentação  
O *da camada de apresentação* é a camada na qual os usuários interagem com um aplicativo. Ele geralmente contém a lógica do aplicativo adicionais também. Componentes da camada de apresentação típicos incluem o seguinte:  
  
-   Componentes de dados, como o <xref:System.Windows.Forms.BindingSource> e <xref:System.Windows.Forms.BindingNavigator>.  
  
-   Objeto de representações de dados, como [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index) classes de entidade para uso na camada de apresentação.  
  
A camada de apresentação normalmente acessa a camada intermediária usando uma referência de serviço (por exemplo, um [serviços do Windows Communication Foundation e WCF Data Services no Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md) aplicativo). A camada de apresentação não acessa diretamente a camada de dados. A camada de apresentação se comunica com a camada de dados por meio do componente de acesso a dados na camada intermediária.  
  
## <a name="middle-tier"></a>Camada intermediária  
O *camada intermediária* é a camada que a camada de apresentação e os camada de dados usam para se comunicar entre si. Componentes de camada intermediária típicos incluem o seguinte:  
  
-   Lógica de negócios, como a validação de regras e dados de negócios.  
  
-   Componentes de acesso a dados e lógica, como o seguinte:  
  
    -   [TableAdapters](create-and-configure-tableadapters.md) e [DataAdapters e DataReaders](/dotnet/framework/data/adonet/dataadapters-and-datareaders).  
  
    -   Objeto de representações de dados, como [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index) classes de entidade.  
  
    -   Serviços comuns de aplicativos, como autenticação, autorização e personalização.  
  
A ilustração a seguir mostra os recursos e tecnologias que estão disponíveis no Visual Studio e onde eles podem caber na camada intermediária de um aplicativo de n camadas.  
  
![Componentes da camada de meio](../data-tools/media/ntiermid.png "NtierMid")  
camada intermediária  
  
A camada intermediária normalmente se conecta à camada de dados usando uma conexão de dados. Esta conexão de dados é normalmente armazenado no componente de acesso de dados.  
  
## <a name="data-tier"></a>Camada de Dados  
O *da camada de dados* é basicamente o servidor que armazena dados de um aplicativo (por exemplo, um servidor que executa [!INCLUDE[ssNoVersion](../data-tools/includes/ssnoversion_md.md)]).  
  
A ilustração a seguir mostra os recursos e tecnologias que estão disponíveis no Visual Studio e onde eles podem caber na camada de dados de um aplicativo de n camadas.  
  
![Componentes da camada de dados](../data-tools/media/ntierdatatier.png "ntierdatatier")  
Camada de dados  
  
A camada de dados não pode ser acessada diretamente do cliente na camada de apresentação. Em vez disso, o componente de acesso de dados na camada intermediária é usado para comunicação entre as camadas de dados e de apresentação.  
  
## <a name="help-for-n-tier-development"></a>Ajuda para o desenvolvimento de N camadas  
Os tópicos a seguir fornecem informações sobre como trabalhar com aplicativos de n camadas:  
  
[Separar conjuntos de dados e TableAdapters em diferentes projetos](../data-tools/separate-datasets-and-tableadapters-into-different-projects.md)  
  
[Passo a passo: criando um aplicativo de dados de N camadas](../data-tools/walkthrough-creating-an-n-tier-data-application.md)  

[N-camadas e aplicativos remotos com o LINQ to SQL](http://msdn.microsoft.com/Library/854a1cdd-53cb-45f5-83ca-63962a9b3598)  
  
## <a name="see-also"></a>Consulte também
[Passo a passo: Criando um aplicativo de dados de N camadas](../data-tools/walkthrough-creating-an-n-tier-data-application.md)   
[Atualização hierárquica](../data-tools/hierarchical-update.md)   
[Ferramentas de conjunto de dados no Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)   
[Acessando dados no Visual Studio](../data-tools/accessing-data-in-visual-studio.md)