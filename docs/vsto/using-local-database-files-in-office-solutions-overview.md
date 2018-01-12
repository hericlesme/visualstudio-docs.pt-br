---
title: "Usando arquivos de banco de dados Local na visão geral das soluções do Office | Microsoft Docs"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office applications [Office development in Visual Studio], data
- data [Office development in Visual Studio], local
- local data [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 1576af3c3fc8a1c7f514a4941eb849df03774c5f
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/10/2018
---
# <a name="using-local-database-files-in-office-solutions-overview"></a>Visão geral do uso de arquivos de banco de dados locais em soluções do Office
  Você pode incluir um arquivo de banco de dados, como um arquivo SQL Server Express (. mdf) ou um arquivo do Microsoft Office Access (. mdb), em sua solução do Office. Isso permite que os usuários finais manter um banco de dados local em situações em que manter um banco de dados centralizado não é necessário, por exemplo, em uma solução local de inventário que é usada apenas em um único computador.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## <a name="importing-the-database-file-into-a-project"></a>Importar o arquivo de banco de dados para um projeto  
 Para importar o arquivo de banco de dados para seu projeto, use o **Assistente de configuração de fonte de dados** para criar uma fonte de dados com base no arquivo de banco de dados. O assistente adiciona o arquivo de banco de dados e um conjunto de dados tipado ao seu projeto.  
  
## <a name="deploying-the-database-file"></a>Implantando o arquivo de banco de dados  
 O **Assistente de configuração de fonte de dados** usa um caminho relativo para criar conexões com o arquivo de banco de dados local. Isso permite que você copie a solução de um computador para outro se você mantiver as posições relativas dos arquivos.  
  
 Se você implanta a solução em um servidor e, em seguida, distribua o documento para cada usuário final, você deve distribuir o arquivo de banco de dados manualmente e instalá-lo na mesma posição em relação ao documento. Isso significa que o usuário final não é possível mover o documento para um novo local no seu computador, a menos que ele ou ela também move o arquivo de banco de dados.  
  
## <a name="local-database-files-and-caching-the-dataset"></a>Arquivos de banco de dados local e o armazenamento em cache o conjunto de dados  
 Em soluções de nível de documento para o Microsoft Office Excel e o Microsoft Office Word, você pode armazenar em cache conjuntos de dados no documento marcando-se a instância do conjunto de dados com o atributo <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute>. Quando você adicionar o arquivo de banco de dados ao seu projeto usando o **Assistente de configuração de fonte de dados**, um conjunto de dados tipado é adicionado automaticamente ao seu projeto. Raramente é necessário aplicar <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> para este conjunto de dados, porque os dados já são locais no computador do usuário. Para obter mais informações, consulte [Caching Data](../vsto/caching-data.md).  
  
## <a name="see-also"></a>Consulte também  
 [Associando dados a controles em soluções do Office](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Como: preencher documentos com dados de um banco de dados](../vsto/how-to-populate-documents-with-data-from-a-database.md)   
 [Como: atualizar uma fonte de dados com dados de um controle de Host](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)   
 [Implantando uma solução do Office](../vsto/deploying-an-office-solution.md)   
 [Armazenando dados em cache](../vsto/caching-data.md)  
  
  