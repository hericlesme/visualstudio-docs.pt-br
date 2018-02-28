---
title: "Ferramentas do Visual Studio para cenários de instalação de tempo de execução do Office | Microsoft Docs"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visual Studio Tools for Office runtime, installation scenarios
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload:
- office
ms.openlocfilehash: 9c63f5e4cef88ed927326b69f1fa389e34b06c8b
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/10/2018
---
# <a name="visual-studio-tools-for-office-runtime-installation-scenarios"></a>Cenários de instalação de tempo de execução do Visual Studio Tools para Office
  Você pode instalar o Visual Studio 2010 Tools for Office Runtime de três maneiras:  
  
-   Quando você instala o Visual Studio.  
  
-   Quando você instala o Microsoft Office.  
  
-   Quando você instala o Visual Studio 2010 Tools para Office Runtime redistribuível.  
  
 Os componentes de tempo de execução que são instalados dependem da configuração do computador e o cenário de instalação.  
  
## <a name="runtime-components-that-are-installed-in-each-installation-scenario"></a>Componentes de tempo de execução que estão instalados em cada cenário de instalação  
 O Visual Studio 2010 Tools para Office Runtime tem três componentes: o carregador de soluções do Office, as extensões do Office para o .NET Framework 3.5 e as extensões do Office para o [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou posterior. Quando você instalar o tempo de execução, o carregador de soluções do Office sempre é instalado. A instalação das extensões do Office para o .NET Framework depende da configuração do computador e o cenário de instalação. Se uma das extensões do Office não pode ser instalada quando o tempo de execução é instalado pela primeira vez, o tempo de execução automaticamente instalará as extensões ausentes do Office posteriormente, quando determinados requisitos forem atendidos. Esse recurso de tempo de execução é chamado *instalar sob demanda*.  
  
 A tabela a seguir mostra os componentes de tempo de execução são instalados por padrão em cada cenário de instalação do tempo de execução. Para obter mais informações sobre cada cenário é exibido mais tarde.  
  
|Cenário de instalação do tempo de execução|Carregador de soluções do Office|Extensões do Office para o .NET Framework 3.5|Extensões do Office para o[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]|Extensões do Office para o[!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]|  
|-----------------------------------|----------------------------|--------------------------------------------------|---------------------------------------------------------------------------------------|---------------------------------------------------------------------------|  
|Com [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] e posterior|Sim|Sim, se o .NET Framework 3.5 já está instalado.|Sim|Sim|  
|Com[!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]|Sim|Sim, se o .NET Framework 3.5 já está instalado.|Não|Não|  
|Com o Office 2010 Service Pack 1 (SP1) ou posterior|Sim|Sim, se o .NET Framework 3.5 já está instalado.|Sim, se o [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] já está instalado.|Não|  
|Com o redistribuível de tempo de execução|Sim|Sim, se o .NET Framework 3.5 já está instalado|Sim, se o [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] já está instalado.|Sim, se o [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] já está instalado.|  
  
### <a name="installing-the-runtime-with-visual-studio-or-the-microsoft-office-developer-tools-for-visual-studio"></a>Instalar o tempo de execução com o Visual Studio ou o Microsoft Office Developer Tools para Visual Studio  
 Quando você instala as ferramentas de desenvolvedor do Office no Visual Studio, as extensões do Office para o [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] e [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] são sempre instaladas no computador de desenvolvimento. As extensões do Office para o .NET Framework 3.5 são instaladas somente se o .NET Framework 3.5 já está presente no computador de desenvolvimento. Se você instalar o .NET Framework 3.5, depois de instalar o [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)], o tempo de execução automaticamente instala as extensões do Office para o .NET Framework 3.5 na primeira vez que você criar um projeto do Office que tem como alvo o .NET Framework 3.5.  
  
> [!WARNING]  
>  Não é possível criar um projeto do Office que se destina ao .NET Framework 3.5 usando [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] ou posterior.  
  
 Para obter mais informações sobre como instalar o Office developer tools, consulte [como: configurar um computador para desenvolver soluções do Office](../vsto/how-to-configure-a-computer-to-develop-office-solutions.md).  
  
### <a name="installing-the-runtime-with-office"></a>Instalar o tempo de execução com o Office  
 Quando você instala o Office, as extensões do Office para o .NET Framework 3.5 são instaladas se o .NET Framework 3.5 já está presente no computador. Se você instalar o .NET Framework 3.5 depois do Office, o tempo de execução automaticamente instala as extensões do Office para o .NET Framework 3.5, o primeiro tempo que um aplicativo do Office tenta carregar uma solução que tem como destino o .NET Framework 3.5.  
  
 As extensões do Office para o [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou versões posteriores não são instalados com o Office, mesmo se o [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou posterior já está presente quando você instala o Office.  
  
 As extensões do Office para o [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] são instalados com o Office. Os usuários finais podem obter as extensões do Office para o [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] instalando uma atualização do Windows.  
  
 Para garantir que os usuários têm as extensões necessárias para usar o aplicativo, inclua a versão mais recente do Visual Studio 2010 Tools para Office Runtime redistribuível como um pré-requisito para sua solução. Para obter mais informações sobre pré-requisitos, consulte [pré-requisitos de solução do Office para implantação](http://msdn.microsoft.com/en-us/9f672809-43a3-40a1-9057-397ce3b5126e).  
  
### <a name="installing-the-runtime-by-using-the-runtime-redistributable"></a>Instalando o tempo de execução usando o redistribuível de tempo de execução  
 Você pode instalar o tempo de execução, executando o Visual Studio 2010 Tools for Office Runtime redistribuível manualmente ou incluindo os pacotes redistribuíveis como um pré-requisito quando você implanta uma solução do Office.  
  
 Quando você instala o tempo de execução usando o Visual Studio 2010 Tools para Office Runtime redistribuível, as extensões do Office para o .NET Framework 3.5 e as extensões do Office para o [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou posterior está instalado se as versões correspondentes do .NET Framework já estão presentes no computador. Se o computador não tem uma dessas versões do .NET Framework quando o tempo de execução é instalado, as extensões do Office para a versão ausente do .NET Framework não estão instaladas no momento. Se você instalar a versão ausente do .NET Framework mais tarde, o tempo de execução automaticamente instala as extensões do Office correspondentes na próxima vez em que uma solução que requer as extensões está instalada (se o tempo de execução foi instalado com uma solução que foi implantada usando o ClickOnce) ou carregado (se o tempo de execução foi instalado com uma solução que foi implantada usando o Windows Installer).  
  
 Para obter mais informações sobre como incluir pré-requisitos em uma solução de ClickOnce, consulte [como: instalar pré-requisitos em computadores de usuário final para executar soluções do Office](http://msdn.microsoft.com/en-us/74dd2c52-838f-4abf-b2b4-4d7b0c2a0a98). Para obter mais informações sobre como instalar o tempo de execução do pacote redistribuível manualmente, consulte [como: instalar o Visual Studio Tools para Office Runtime redistribuível](../vsto/how-to-install-the-visual-studio-tools-for-office-runtime-redistributable.md).  
  
## <a name="see-also"></a>Consulte também  
 [Ferramentas do Visual Studio para visão geral de tempo de execução do Office](../vsto/visual-studio-tools-for-office-runtime-overview.md)   
 [Assemblies no tempo de execução das Ferramentas do Visual Studio para o Office](../vsto/assemblies-in-the-visual-studio-tools-for-office-runtime.md)  
  
  