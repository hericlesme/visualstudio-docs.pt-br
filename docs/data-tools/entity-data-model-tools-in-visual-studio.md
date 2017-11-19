---
title: Ferramentas do Entity Framework no Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1b06b573-84aa-4458-b3f5-e238df47bf45
caps.latest.revision: "21"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: eb4ca4445af3970828f4212c69c11d9d173d5650
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="entity-framework-tools-in-visual-studio"></a>Ferramentas do Entity Framework no Visual Studio
Entity Framework é uma tecnologia de mapeamento relacional de objeto que permite que os desenvolvedores de .NET trabalhar com dados relacionais usando objetos específicos do domínio. Elimina a necessidade para a maioria do código de acesso a dados que os desenvolvedores geralmente precisam gravar. Entity Framework é o mapeamento relacional de objeto recomendado (ORM) modelagem tecnologia para novos aplicativos .NET.  
  
Ferramentas do Entity Framework são projetadas para ajudá-lo a criar aplicativos Entity Framework (EF). A documentação completa do Entity Framework está aqui: [EF núcleos e 6 EF](https://docs.microsoft.com/ef/).  
  
Com ferramentas do Entity Framework, você pode criar um *modelo conceitual* de uma já existente do banco de dados e, em seguida, graficamente visualizar e editar o modelo conceitual. Ou então, criar um modelo conceitual graficamente primeiro e, em seguida, gerar um banco de dados que oferece suporte a seu modelo. Em ambos os casos, você pode atualizar automaticamente seu modelo quando subjacente alterações do banco de dados e gerar automaticamente o código da camada de objeto para o seu aplicativo. Geração de banco de dados e geração de código da camada de objeto são personalizáveis.  
  
As ferramentas do Entity Framework estão instaladas como parte do **armazenamento de dados e processamento** carga de trabalho em que o instalador do Visual Studio. Você também pode instalá-los como um componente indvidual no **SDKs, bibliotecas e estruturas** categoria.  
 
Estas são as ferramentas específicas que constituem ferramentas do Entity Framework no Visual Studio:  
  
-   Você pode usar o [!INCLUDE[vstecado](../data-tools/includes/vstecado_md.md)]  **[!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)] Designer** (**Entity Designer**) para criar visualmente e modificar entidades, associações, mapeamentos e relacionamentos de herança. O **Entity Designer** também gera [!INCLUDE[TLA#tla_cshrp](../data-tools/includes/tlasharptla_cshrp_md.md)] ou [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] código da camada de objeto.  
  
-   Você pode usar o  **[!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)] assistente** para gerar um modelo conceitual de um banco de dados existente e adicionar informações de conexão de banco de dados para seu aplicativo.  
  
-   Você pode usar o **criar Assistente de banco de dados** para criar um modelo conceitual primeiro e, em seguida, criar um banco de dados que oferece suporte ao modelo.  
  
-   Você pode usar o **Assistente de atualização de modelo** para atualizar o modelo conceitual, o modelo de armazenamento e mapeamentos de quando foram feitas alterações no banco de dados subjacente.  
  
    > [!NOTE]
    >  A partir do Visual Studio 2010, ferramentas do Entity Framework não oferecem suporte a [!INCLUDE[ss2k](../data-tools/includes/ss2k_md.md)].  
  
As ferramentas geram ou modificar um arquivo. edmx. Esse arquivo. edmx contém informações que descrevem o modelo conceitual, o modelo de armazenamento e os mapeamentos entre eles. Para obter mais informações, consulte [EDMX](https://msdn.microsoft.com/data/jj650889.aspx).  
  
[Entity Framework Power Tools](https://marketplace.visualstudio.com/items?itemName=EntityFrameworkTeam.EntityFrameworkPowerToolsBeta4) ajudá-lo a criar aplicativos que usam o modelo de dados de entidade. Power tools pode gerar um modelo conceitual, validar um modelo existente, produzir arquivos de código-fonte que contêm classes de objeto com base no modelo conceitual e produzem arquivos de código-fonte que contêm modos de exibição que gera o modelo. Para obter informações detalhadas, consulte [modos de exibição de mapeamento Pre-Generated](https://msdn.microsoft.com/data/dn469601.aspx).  
  
## <a name="related-topics"></a>Tópicos relacionados  
  
|Título|Descrição|  
|-----------|-----------------|  
|[ADO.NET Entity Framework](/dotnet/framework/data/adonet/ef/index)|Descreve como usar [!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)] ferramentas, que [!INCLUDE[adonet_ef](../data-tools/includes/adonet_ef_md.md)] fornece para criar aplicativos.|  
|[Modelo de dados de entidade](/dotnet/framework/data/adonet/entity-data-model)|Fornece links e informações sobre como trabalhar com dados que são usados por aplicativos baseados em [!INCLUDE[adonet_ef](../data-tools/includes/adonet_ef_md.md)].|  
|[Documentação do Entity Framework (EF))](https://msdn.microsoft.com/library/ee712907(v=vs.113).aspx)|Fornece um índice de vídeos, tutoriais e documentação avançada para ajudá-lo a tirar o máximo proveito do Entity Framework.|  
|[ASP.NET 5 aplicativo para o novo banco de dados](https://docs.efproject.net/en/latest/platforms/aspnetcore/new-db.html)|Descreve como criar um novo aplicativo ASP.NET 5 usando o Entity Framework 7.|  
  
## <a name="see-also"></a>Consulte também  
 [Ferramentas de dados do Visual Studio para .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)