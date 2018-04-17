---
title: Projetos DAC no Visual Studio, projetos e projetos do servidor de banco de dados | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- managing change, databases
- database features of Visual Studio, managing change
- databases, managing change
- managing change, database servers
ms.assetid: 40b51f5a-d52c-44ac-8f84-037a0917af33
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: baca17712d6cf39753dab51c60fee901c0ea08ca
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="database-projects-and-data-tier-applications-in-visual-studio"></a>Projetos de banco de dados e aplicativos da camada de dados no Visual Studio  
Você pode usar os projetos de banco de dados para criar novos bancos de dados, novos aplicativos da camada de dados (DACs) e atualizar bancos de dados existentes e aplicativos da camada de dados. Projetos de banco de dados e projetos de DAC permitem aplicar técnicas de gerenciamento de projeto e controle de versão para seus esforços de desenvolvimento de banco de dados da mesma forma que você aplicar essas técnicas para código gerenciado ou nativo. Você pode ajudar sua equipe de desenvolvimento a gerenciar as alterações de bancos de dados e servidores de banco de dados, criando um *projeto DAC*, *projeto de banco de dados*, ou um *projeto do servidor* e colocá-lo sob o controle de versão. Membros da equipe podem, em seguida, check-out de arquivos para fazer, compilar e testar as alterações em um *ambiente de desenvolvimento isolado*, ou de área restrita, antes de compartilhá-los com a equipe. Para ajudar a garantir a qualidade do código, sua equipe pode concluir e testar todas as alterações para uma versão específica do banco de dados em um ambiente de preparo antes de implantar as alterações em produção.  
  
Para obter uma lista dos recursos de banco de dados que são suportados por aplicativos de camada de dados, consulte [recursos com suporte em aplicativos da camada de dados](http://go.microsoft.com/fwlink/?LinkId=164239) no site da Microsoft. Se você usar recursos que não são suportados por aplicativos de camada de dados no banco de dados, você deve usar um projeto de banco de dados para gerenciar as alterações ao banco de dados.  
  
## <a name="common-high-level-tasks"></a>Tarefas comuns de alto nível  
  
|Tarefas de alto nível|Conteúdo de suporte|  
|----------------------|------------------------|  
|**Iniciar o desenvolvimento de um aplicativo da camada de dados:** um DAC é um novo conceito apresentado com [!INCLUDE[sskatmai_r2](../data-tools/includes/sskatmai_r2_md.md)] que contém a definição de um [!INCLUDE[ssNoVersion](../data-tools/includes/ssnoversion_md.md)] objetos que são usados por um cliente-servidor ou de 3 camadas de instância de banco de dados e o suporte aplicativo. Um DAC inclui objetos de banco de dados, como tabelas e exibições, junto com as entidades de instância, como logons. Você pode usar [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] para criar um projeto de DAC, crie um arquivo de pacote DAC e enviar esse arquivo de pacote DAC para um administrador de banco de dados para a implantação em uma instância do [!INCLUDE[ssNoVersion](../data-tools/includes/ssnoversion_md.md)] mecanismo de banco de dados.|-   [Criando e gerenciando aplicativos da camada de dados](http://go.microsoft.com/fwlink/?LinkId=160741) (Microsoft web site)<br />-   [SQL Server Management Studio](http://go.microsoft.com/fwlink/?LinkId=227328)|  
|**Executar o desenvolvimento de banco de dados iterativos:** se você for um testador ou desenvolvedor, check-out de partes do projeto e, em seguida, atualizá-los em um ambiente de desenvolvimento isolado. Usando esse tipo de ambiente, você pode testar suas alterações sem afetar outros membros da equipe. Depois que as alterações forem concluídas, você verificar os arquivos no controle de versão, onde outros membros da equipe podem obter as alterações e criar e implantá-los em um servidor de teste.|-   [Consulta e editores de texto (SQL Server Management Studio)](http://go.microsoft.com/fwlink/?LinkId=227327) (web site da Microsoft)<br />-   [Depurador Transact-SQL](http://go.microsoft.com/fwlink/?LinkId=227324) (Microsoft web site)|  
|**Criação de protótipos, verificando testar os resultados e modificar os scripts de banco de dados e objetos:** você pode usar o [!INCLUDE[tsql](../data-tools/includes/tsql_md.md)] editor para realizar qualquer uma dessas tarefas comuns.|-   [Consulta e editores de texto (SQL Server Management Studio)](http://go.microsoft.com/fwlink/?LinkId=227327) (web site da Microsoft)|  
  
## <a name="see-also"></a>Consulte também
[Ferramentas de dados do Visual Studio para .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)
