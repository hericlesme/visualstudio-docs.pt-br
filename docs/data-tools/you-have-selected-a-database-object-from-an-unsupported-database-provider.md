---
title: Você tiver selecionado um objeto de base de dados de um provedor de base de dados sem suporte
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: c0f1298e-31aa-471e-ae19-1bafffd2ae40
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: f3ab7375db8c3adfe769cf1c344937b60695eb25
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="you-have-selected-a-database-object-from-an-unsupported-database-provider"></a>Você tiver selecionado um objeto de base de dados de um provedor de base de dados sem suporte

O Object Relational Designer oferece suporte a apenas o .NET Framework Data Provider para SQL Server (<xref:System.Data.SqlClient>). Embora você pode clicar em **Okey** e continuar a trabalhar com objetos de provedores de banco de dados sem suporte, você pode enfrentar um comportamento inesperado em tempo de execução.

> [!NOTE]
> Somente as conexões de dados que usam o provedor de dados. NET Framework para SQL Server são suportadas.

## <a name="to-correct-this-error"></a>Para corrigir este erro

- Clique em **OK**.

   Você pode continuar criando as classes de entidade que mapeia para a conexão que usa o provedor de banco de dados sem suporte. Você pode apresentar comportamento inesperado quando você usa provedores de base de dados sem suporte.

    -ou-

- Clique em **Cancelar**.

   A ação é interrompida. Crie ou use uma conexão de dados que usa o provedor do. NET Framework para SQL Server.

## <a name="see-also"></a>Consulte também

- [Mensagens do O/R Designer](../data-tools/o-r-designer-messages.md)
- [LINQ to SQL tools no Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)