---
title: "Você selecionou um objeto de banco de dados de um provedor de banco de dados sem suporte | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c0f1298e-31aa-471e-ae19-1bafffd2ae40
caps.latest.revision: "3"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: 05e638be5cc11f66052e5a1f6116e7205b824106
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/09/2017
---
# <a name="you-have-selected-a-database-object-from-an-unsupported-database-provider"></a>Você tiver selecionado um objeto de base de dados de um provedor de base de dados sem suporte
O Object Relational Designer oferece suporte a apenas o .NET Framework Data Provider para SQL Server (<xref:System.Data.SqlClient>). Embora você pode clicar em **Okey** e continuar a trabalhar com objetos de provedores de banco de dados sem suporte, você pode enfrentar um comportamento inesperado em tempo de execução.  
  
> [!NOTE]
>  Somente as conexões de dados que usam o provedor de dados. NET Framework para SQL Server são suportadas.  
  
### <a name="to-correct-this-error"></a>Para corrigir este erro  
  
- Clique em **OK**.

   Você pode continuar criando as classes de entidade que mapeia para a conexão que usa o provedor de banco de dados sem suporte. Você pode apresentar comportamento inesperado quando você usa provedores de base de dados sem suporte.  
  
     -ou-  
  
- Clique em **Cancelar**.

   A ação é interrompida. Crie ou use uma conexão de dados que usa o provedor do. NET Framework para SQL Server.  
  
## <a name="see-also"></a>Consulte também
[Mensagens de Object Relational Designer](../data-tools/o-r-designer-messages.md)  
[LINQ to SQL tools no Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)