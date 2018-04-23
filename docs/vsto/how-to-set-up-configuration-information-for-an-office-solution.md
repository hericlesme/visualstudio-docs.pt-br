---
title: 'Como: configurar as informações de configuração para uma solução do Office | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- solutions [Office development in Visual Studio], configuration files
- configuration files [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 9659872fa6cb4e294d1757412862c10e42cde2e9
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
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
  
  