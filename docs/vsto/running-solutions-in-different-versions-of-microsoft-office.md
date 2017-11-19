---
title: "Executando soluções em versões diferentes do Microsoft Office | Microsoft Docs"
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
- solutions [Office development in Visual Studio], multiple Office versions
- Office applications [Office development in Visual Studio], multiple Office versions
- Office development in Visual Studio, multiple Office versions
- Office solutions [Office development in Visual Studio]
- multiple Office versions
ms.assetid: 414e7741-c07d-4900-9d10-68b821413b3f
caps.latest.revision: "61"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 93e365d335f835196576ad9ed10216e904e81f93
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="running-solutions-in-different-versions-of-microsoft-office"></a>Executando soluções em versões diferentes do Microsoft Office
    
## <a name="running-office-solutions-created-by-using-visual-studio-2010-and-above"></a>Executando soluções do Office criadas usando o Visual Studio 2010 e posterior  
  
|Versão do Office direcionado pelo modelo de projeto|Destino do .NET Framework do projeto<sup>1</sup>|Versões do Office que pode executar a solução|Tempo de execução necessário no computador do usuário final|  
|--------------------------------------------------------|------------------------------------------------------|--------------------------------------------------|-------------------------------------------|  
|Office 2016 e[!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)]|[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]ou posterior|Office 2016<br /><br /> [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)]<br /><br /> [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]<br /><br /> Sistema Microsoft Office 2007<sup>2</sup>|Visual Studio 2010 Tools for Office Runtime|  
|[!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]|[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]ou posterior|Office 2016<br /><br /> [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)]<br /><br /> [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]<br /><br /> Sistema Microsoft Office 2007<sup>2</sup>|Visual Studio 2010 Tools for Office Runtime|  
|[!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]|.NET Framework 3,5|Office 2016<br /><br /> [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)]<br /><br /> [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]|Visual Studio 2010 Tools for Office Runtime|  
|Sistema Microsoft Office 2007|[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]ou posterior<br /><br /> ou<br /><br /> .NET Framework 3,5|Office 2016<br /><br /> [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)]<br /><br /> [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]<br /><br /> Sistema Microsoft Office 2007|Visual Studio 2010 Tools for Office Runtime|  
  
 1. A versão do .NET Framework que seu destinos do projeto é necessário nos computadores de usuário final para sua solução executar. Por exemplo, se seu projeto se destina ao .NET Framework 3.5, .NET Framework 3.5 é necessário nos computadores dos usuários finais. Neste exemplo, sua solução não será executado se apenas o [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] está instalado em computadores do usuário final.  
  
 2. Nesse cenário, a solução será executado sem erros no sistema Microsoft Office 2007 somente se ela não usa recursos que são novos no [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)].  
  
## <a name="running-office-solutions-created-by-using-versions-of-visual-studio-prior-to-visual-studio-2010"></a>Executando o Office soluções criadas pelo usando versões do Visual Studio antes do Visual Studio 2010  
 Aplicativos do Microsoft Office podem executar soluções criadas usando versões do Visual Studio antes do Visual Studio 2010. Em alguns casos, essas soluções necessitam de versões diferentes do [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]. Versões diferentes do [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] pode ser instalada lado a lado no mesmo computador.  
  
 A tabela a seguir mostra quais versões do Microsoft Office podem executar soluções criadas pelo uso de versões anteriores do Visual Studio e quais versões do [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] e o .NET Framework são necessárias para cada solução.  
  
|Edição do Visual Studio usado para criar a solução|Versão do Office direcionado pelo modelo de projeto|Versões do Office que pode executar a solução|Tempo de execução necessário no computador do usuário final|Versão necessária do .NET Framework no computador do usuário final|  
|----------------------------------------------------------|--------------------------------------------------------|--------------------------------------------------|-------------------------------------------|----------------------------------------------------------|  
|Visual Studio 2008 Professional<br /><br /> ou<br /><br /> Visual Studio Team System 2008|Sistema Microsoft Office 2007|[!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)]e [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] <sup>1</sup><br /><br /> Sistema Microsoft Office 2007|Visual Studio 2010 Tools for Office Runtime<sup>1</sup><br /><br /> ou<br /><br /> Visual Studio Tools para o Microsoft Office system (versão 3.0 Runtime)|.NET Framework 3,5|  
|Uma das seguintes edições do Visual Studio 2005 com VSTO 2005 SE<sup>2</sup> instalado:<br /><br /> -O visual Studio 2005 Tools para Office<br />-O visual Studio Team System 2005<br />-O visual Studio 2005 Professional|Sistema Microsoft Office 2007|[!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)]e [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] (somente 32 bits<sup>3</sup>)<br /><br /> Sistema Microsoft Office 2007|O Visual Studio 2005 Tools para Office segundo o tempo de execução de edição|.NET framework 2.0, .NET Framework 3.0 ou do .NET Framework 3.5|  
|Qualquer uma das seguintes edições do Visual Studio:<br /><br /> -O visual Studio 2008 Professional<br />-O visual Studio Team System 2008<br />-O visual Studio 2005 Tools para Office (com ou sem o VSTO 2005 SE<sup>2</sup> instalado)<br />-O visual Studio Team System 2005 (com ou sem o VSTO 2005 SE<sup>2</sup> instalado)<br />-O visual Studio 2005 Professional com VSTO 2005 SE<sup>2</sup> instalado|O Microsoft Office 2003|[!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)]e [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] (somente 32 bits<sup>3</sup>)<br /><br /> Sistema Microsoft Office 2007<br /><br /> O Microsoft Office 2003|O Visual Studio 2005 Tools para Office segundo o tempo de execução de edição|.NET framework 2.0, .NET Framework 3.0 ou do .NET Framework 3.5|  
  
 1. [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)]e [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] aplicativos incluem o Visual Studio 2010 Tools for Office Runtime. Portanto, esses aplicativos sempre usam o Visual Studio 2010 Tools para Office Runtime em vez do Visual Studio Tools para o Microsoft Office system (versão 3.0 Runtime) nesse cenário. Aplicativos no sistema Microsoft Office 2007 podem usar o Visual Studio 2010 Tools para Office Runtime ou o Visual Studio Tools para o Microsoft Office system (versão 3.0 Runtime).  
  
 2. VSTO 2005 SE é um suplemento gratuito do Visual Studio que fornece modelos de projeto de suplemento do VSTO para o Microsoft Office 2003 e o Microsoft Office 2007. Ele pode ser instalado com o Visual Studio 2005 Professional, Visual Studio 2005 Tools para Office ou uma edição do Visual Studio Team System 2005. Para obter mais informações, consulte [Visual Studio 2005 Tools para Office Second Edition](http://go.microsoft.com/fwlink/?LinkId=148446).  
  
 3. Soluções do Office que exigem o Visual Studio 2005 Tools para Office Runtime segundo de edição não são compatíveis com as versões de 64 bits do [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] e [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]. Para executar essas soluções na edição de 64 bits do [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] ou [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)], você deve atualizar o projeto para [!INCLUDE[vs_dev10_long](../sharepoint/includes/vs-dev10-long-md.md)] ou a um projeto do Visual Studio 2008 que tem como alvo o Microsoft Office 2007.  
  
## <a name="see-also"></a>Consulte também  
 [Projetando e criando soluções do Office](../vsto/designing-and-creating-office-solutions.md)   
 [Ferramentas do Visual Studio para visão geral de tempo de execução do Office](../vsto/visual-studio-tools-for-office-runtime-overview.md)   
 [Como: criar projetos do Office no Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Ferramentas do Visual Studio para cenários de instalação de tempo de execução do Office](../vsto/visual-studio-tools-for-office-runtime-installation-scenarios.md)   
 [Configurando um computador para desenvolver soluções do Office](../vsto/running-solutions-in-different-versions-of-microsoft-office.md)  
  
  