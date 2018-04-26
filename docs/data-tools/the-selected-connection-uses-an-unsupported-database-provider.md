---
title: A conexão selecionada usa um provedor de base de dados sem suporte
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 4d25dfa1-8fa4-4529-9b90-973bc2ec2993
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 77519a5497c26553e2023862e46f3ba618e4f99f
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="the-selected-connection-uses-an-unsupported-database-provider"></a>A conexão selecionada usa um provedor de base de dados sem suporte

Esta mensagem aparece quando você arrasta os itens que não usam o .NET Framework Data Provider para SQL Server de **Server Explorer**/**Pesquisador de objetos de banco de dados** até o [LINQ to SQL Ferramentas do Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md).

[!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] suporta apenas as conexões de dados que usam o provedor. NET Framework para SQL Server. Somente as conexões a Microsoft SQL Server ou o Arquivo base de dados do Microsoft SQL Server são válidos.

Para corrigir esse erro, adicionar apenas itens de conexões de dados que usam o .NET Framework Data Provider para SQL Server para o [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].

## <a name="see-also"></a>Consulte também

- <xref:System.Data.SqlClient>
- [Mensagens do O/R Designer](../data-tools/o-r-designer-messages.md)
- [LINQ to SQL tools no Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
