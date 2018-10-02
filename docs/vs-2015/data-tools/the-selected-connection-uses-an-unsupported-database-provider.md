---
title: A conexão selecionada usa um provedor de banco de dados sem suporte | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4d25dfa1-8fa4-4529-9b90-973bc2ec2993
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 4e38bda495521bf81c6eb4b9a00a0f32620a71fb
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47461772"
---
# <a name="the-selected-connection-uses-an-unsupported-database-provider"></a>A conexão selecionada usa um provedor de base de dados sem suporte
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [a conexão selecionada usa um provedor de banco de dados sem suporte](https://docs.microsoft.com/visualstudio/data-tools/the-selected-connection-uses-an-unsupported-database-provider).  
  
  
Esta mensagem aparece quando você arrasta itens que não usam o .NET Framework Data Provider para SQL Server a partir **Gerenciador de servidores**/**Database Explorer** até a [LINQ to SQL Ferramentas do Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md).  
  
 [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] suporta apenas as conexões de dados que usam o provedor. NET Framework para SQL Server. Somente as conexões a Microsoft SQL Server ou o Arquivo base de dados do Microsoft SQL Server são válidos.  
  
### <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Adicionar itens somente as conexões de dados que usam o provedor de dados. NET Framework para SQL Server a [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Data.SqlClient>   
 [Conectando-se a dados no Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Provedores de dados do .NET framework](http://msdn.microsoft.com/library/03a9fc62-2d24-491a-9fe6-d6bdb6dcb131)   
 [Passo a passo: Criando Classes LINQ to SQL (Object Relational Designer)](http://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233)   
 [Criando aplicativos de dados](../data-tools/creating-data-applications.md)

