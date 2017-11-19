---
title: "Como: configurar as informações de configuração para uma solução do Office | Microsoft Docs"
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
- solutions [Office development in Visual Studio], configuration files
- configuration files [Office development in Visual Studio]
ms.assetid: f123838f-957a-4cf5-acc0-0cc0f4c2aea2
caps.latest.revision: "33"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: a8c2e0a904ad3cdbef3e70072d263cc26274de52
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-set-up-configuration-information-for-an-office-solution"></a>Como configurar informações de definição para uma solução do Office
  Você pode usar arquivos de configuração para definir as configurações que são específicas às suas soluções do Office. Você pode especificar configurações como a política de associação de assembly, objetos de comunicação remota, depuração e configurações de rastreamento.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
### <a name="to-add-a-configuration-file-to-your-office-project"></a>Para adicionar um arquivo de configuração para o seu projeto do Office  
  
1.  No menu **Projeto**, clique em **Adicionar Novo Item**.  
  
2.  No **categorias** painel, clique em **geral**.  
  
3.  No **modelos** painel, selecione **arquivo de configuração de aplicativo**.  
  
4.  No **nome** , digite o mesmo nome como o conjunto mais a extensão. config. Por exemplo, um arquivo de configuração para um assembly de projeto do Excel chamado ExcelWorkbook1.dll seria nomeado ExcelWorkbook1.dll.config.  
  
5.  Clique em **Adicionar**.  
  
6.  Crie arquivo de configuração de acordo com o esquema de arquivo de configuração do aplicativo. Para obter mais informações, consulte [esquema de arquivo de configuração para o .NET Framework](/dotnet/framework/configure-apps/file-schema/index).  
  
 Não há nenhuma consideração especial para o uso de arquivos de configuração com projetos do Office.  
  
## <a name="see-also"></a>Consulte também  
 [Esquema de arquivo de configuração para o .NET Framework](/dotnet/framework/configure-apps/file-schema/index)   
 [Projetando e criando soluções do Office](../vsto/designing-and-creating-office-solutions.md)   
 [Implantando uma solução do Office](../vsto/deploying-an-office-solution.md)  
  
  